


Schema :
CREATE TABLE bottle (
  id           IDENTITY PRIMARY KEY,
  owner        VARCHAR(255) NOT NULL,
  domain       VARCHAR(255) NOT NULL,
  opening_date TIMESTAMP    NOT NULL,
);

    // it should come from the configuration file "application.properties"
    @Value("${db.init}")
    public Boolean dbInit;

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
            return new Bottle(resultSet.getLong("id"), resultSet.getString("owner"),
                    resultSet.getString("domain"),
                    resultSet.getTimestamp("opening_date").toLocalDateTime());
        }
    }

    @Autowired
    private JdbcTemplate jdbcTemplate;

    @Override
    public Bottle get(Long id) {
        return jdbcTemplate.queryForObject("SELECT * FROM bottle WHERE id = ?", new Object[]{id}, bottleMapper);
    }
