# springboot
simple springboot examples
@Converter
public class AuditFieldTimeStampConverter implements AttributeConverter<LocalDateTime, String> {

	@Override
	public String convertToDatabaseColumn(LocalDateTime localDateTime) {
		DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss.SSSSSSS XXX");
		OffsetDateTime offsetDateTime = OffsetDateTime.of(localDateTime, OffsetDateTime.now().getOffset());
		return offsetDateTime.format(formatter);
	}

	@Override
	public LocalDateTime convertToEntityAttribute(String dateTimeString) {
		DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss.SSSSSSS XXX");
		return LocalDateTime.parse(dateTimeString, formatter);
	}

}
