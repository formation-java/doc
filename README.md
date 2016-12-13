
use a main @RequestMapping on the class, to handle the /bottle common path.

for a get variable, use
    @RequestMapping("/{id}")
    public Bottle get(@PathVariable Long id)

for a post request, use
    @RequestMapping(value = "/bottle", method = RequestMethod.POST)
    public void create(@RequestBody ...)



        <dependency>
            <groupId>com.fasterxml.jackson.datatype</groupId>
            <artifactId>jackson-datatype-jsr310</artifactId>
            <version>2.6.1</version>
        </dependency>


@Bean
    public Jackson2ObjectMapperBuilder jacksonBuilder() {
        Jackson2ObjectMapperBuilder b = new Jackson2ObjectMapperBuilder();
        b.serializers(new LocalDateTimeSerializer(DateTimeFormatter.ISO_DATE_TIME));
        b.deserializers(new LocalDateTimeDeserializer(DateTimeFormatter.ISO_DATE_TIME));
        return b;
    }