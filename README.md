
[
  {
    "owner": "Saulnoz",
    "grapeType": "MERLOT",
    "domain": "Chateau Réaut",
    "year": 2011,
    "quantity": 100,
    "openingDate": "2016-10-11T15:39:20",
    "finishingDate": null
  }
]

@RequestMapping(value = "/bottle", method = RequestMethod.POST)
@RequestBody

 @RequestMapping(value = "/bottle/{id}", method = RequestMethod.GET)
    public Bottle getBottle(@PathVariable Long id) {
    

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



		<dependency>
			<groupId>com.h2database</groupId>
			<artifactId>h2</artifactId>
			<version>1.4.192</version>
		</dependency>

    @Bean
    public DataSource dataSource() {
        EmbeddedDatabaseBuilder edb = new EmbeddedDatabaseBuilder()
                .setType(EmbeddedDatabaseType.H2)
                .addScript("classpath:sql/schema.sql");
        if (dbInit) {
            edb.addScript("classpath:sql/start-data.sql");
        }
        return edb.build();
    }


class BottleMapper implements RowMapper<Bottle> {
        @Override
        public Bottle mapRow(ResultSet resultSet, int i) throws SQLException {
            Timestamp finishingDate = resultSet.getTimestamp("finishing_date");
            return new Bottle(resultSet.getLong("id"), resultSet.getString("owner"),
                    GrapeTypes.valueOf(resultSet.getString("grape_type")), resultSet.getString("domain_name"),
                    resultSet.getString("year"), resultSet.getInt("quantity"),
                    resultSet.getTimestamp("opening_date").toLocalDateTime(),
                    finishingDate != null ? finishingDate.toLocalDateTime() : null);
        }
    }




BottleEndpoint
    @Autwired servoce   
        => BottleService
            @Autowired Dao
            @Autowired RequestState
            @Autowired UserSession
            @Autowired ApplicationState
                => bottles.stream().forEach(bottle -> dao.addBottle)

@Scope(value = "request", proxyMode = ScopedProxyMode.TARGET_CLASS)
@Scope(value = "session", proxyMode = ScopedProxyMode.TARGET_CLASS)