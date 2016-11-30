
[
  {
    "owner": "Saulnoz",
    "grapeType": "MERLOT",
    "domain": "Chateau Réaut",
    "year": 2011,
    "quantity": 100,
    "finishingDate": null
  }
]

@RequestMapping(value = "/bottle", method = RequestMethod.POST)
@RequestBody

  @Bean
    public Jackson2ObjectMapperBuilder jacksonBuilder() {
        Jackson2ObjectMapperBuilder b = new Jackson2ObjectMapperBuilder();
        b.serializers(new LocalDateTimeSerializer(DateTimeFormatter.ISO_DATE_TIME));
        b.deserializers(new LocalDateTimeDeserializer(DateTimeFormatter.ISO_DATE_TIME));
        return b;
    }



		<dependency>
			<groupId>com.fasterxml.jackson.datatype</groupId>
			<artifactId>jackson-datatype-jsr310</artifactId>
			<version>2.6.1</version>
		</dependency>