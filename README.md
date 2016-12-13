
use a main @RequestMapping on the class, to handle the /bottle common path.

for a get variable, use
    @RequestMapping("/{id}")
    public Bottle get(@PathVariable Long id)

for a post request, use
    @RequestMapping(value = "/bottle", method = RequestMethod.POST)
    public void create(@RequestBody ...)
