
During this exercise you are presented with a real design that was proposed but never implemented in practice due to product pivotation. The exercise is a simplified version of the real deal, but it will give you a good introduction to the type of data our frontend handles.

## Design Mockup
![Design](design.jpg)

This design shows different data models aggregated by day in descencent order by timestamp. The different types of data are:

- **[Users](schemas/user.schema.json):** Represents a user in the platform.
- **[Datasets](schemas/dataset.schema.json):** Represents metadata about a bunch of raw genomic data.
- **[Requests](schemas/request.schema.json):** When a user needs data they may create a `request for data`. This entity contains the information of what the user is looking for.
- **[Discussion](schemas/discussion.schema.json):** Both datasets and request can have user discussions attached to them.
- **[Collection](schemas/collection.schema.json):** Collections are a way to aggrupate multiple datasets under the same category. An example of a collection would be `Breast Cancer`.
- **[Datasource](schemas/datasource.schema.json):** All datasets have an origin. A datasource contains information about the origin of a certain amount of datasets. Usually a datasource is asociated with an institute, laboratory or organization.

To access this data you would have, once in production, an hypotetical API with the following endpoints for each one of the models:

**GET** `<domain>/<object_name>/<id>`:
 - On success: Returns a single entity for the given id
  - Code: `200`
  - Content type: `application/json`
  - Body: Matching object schema
 - On error:
  - Code: `401 | 404 | 500 | 502`
  - Content type: `application/json`
  - Body: [error schema](schemas/error.schema.json)

And one endpoint to to get the feed of events to display:

**GET** `<domain>/feed`:
 - On success: 
  - Code: `200`
  - Content type: `application/json`
  - Body: [feed_array](schemas/feed.schema.json)
 - On error:
  - Code: `401 | 500 | 502`
  - Content type: `application/json`
  - Body: [error schema](schemas/error.schema.json)


The goal of the exercise is for you to implement a solution using the information provided:
  - Write an UI that shows an activity feed clustered by day mirroring the provided design mockup. Some of the icons are not provided, you can use a solution like [font awesome](http://fontawesome.io/) instead.
  - Mock the hypothetical API requests and take into account that the requests may fail. Each of the requests hits a different service with an independent time response and uptime rate. You don't need to implement any backend code! Just mock the calls to it.

Because of the time restrictions you may not be able to do everything. This is intended ;), so focus on what you consider more relevant.

To help you out, we provide some resources. You don't not need them to complete the exercise, but you may find them usesful:
  - Some examples of the API output and their schemas.
  - Some basic CSS that you can extend.

We have designed the exercise on purpose to be loose, allowing some creativity and the usage of previous experience. You are free to use the resources we provided or dismiss them, you can also use any technology or paradigm. The time allowed is tight, so you are also encouraged to reuse any code you have previously used somewhere else.

We will take into consideration:
 - The project file structure.
 - Handling of modularity and complexity, split of the different components.
 - Readability and coherence of the code style.
 - Interaction with mutable state and side effects.
 - CSS composition.
 - What to and not to test and how to test it.
 - Approach to documentation.
 - In general, how to reduce technical debt.
 - A working solution. You can and should hand over some non working code, but try to deliver something working as well.

After the exercise we will arrange a call do discuss your solution, it may be on a different date depending on avalability. Aside the code, you may want to summarize the provided solution, detailing:
- What makes your approach scalable, maintainable, robust...
- What are the drawbacks of this solution.
- With more time what could be done to enhance the solution?
