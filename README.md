## Exercise Context

This exercise will introduce you to the different data models our frontend typically handles. Checkout the design mockup below:

![Design](design.jpg)

The design displays an activity feed made up of different types of activities. This view requires data from different data models, aggregated by day and ordered by timestamp, from newest to oldest. The different data models are:

- **Users:** Represents a user of the platform (see [schema](schemas/user.schema.json))
- **Datasets:** Represents a dataset on the platform (see [schema](schemas/dataset.schema.json))
- **Requests:** Represents a request (this is like asking a question on a forum) that a user has made on the platform (see [schema](schemas/request.schema.json))
- **Discussion:** Represents a comment contributed to a discussion. Comments can be made on datasets & forum requests (see [schema](schemas/discussion.schema.json))
- **Collection:** Represents a number of datasets grouped together by category (e.g. Breast Cancer data; see [schema](schemas/collection.schema.json))
- **Datasource:** Represents the organisation publishing genomic data. This is typically an institution, laboratory or governmental organisation (see [schema](schemas/datasource.schema.json))

In production, you can imagine a hypothetical API with the following endpoints, one for each of the data models:

**GET** `<domain>/<object_name>/<id>`:
 - On success: Returns a single entity for the given id
  - Code: `200`
  - Content type: `application/json`
  - Body: Matching object schema
 - On error:
  - Code: `401 | 404 | 500 | 502`
  - Content type: `application/json`
  - Body: [error schema](schemas/error.schema.json)

There would also be an endpoint to get the feed of events to display:

**GET** `<domain>/feed`:
 - On success:
  - Code: `200`
  - Content type: `application/json`
  - Body: [feed_array](schemas/feed.schema.json)
 - On error:
  - Code: `401 | 500 | 502`
  - Content type: `application/json`
  - Body: [error schema](schemas/error.schema.json)

### Aim of Exercise

The goal of the exercise is for you to implement a solution using the information provided:
  - Write an UI that shows an activity feed clustered by day mirroring the provided design mockup. Some of the icons are not provided, you can use a solution like [font awesome](http://fontawesome.io/) instead.
  - Mock the hypothetical API requests and take into account that the requests may fail. Each of the requests hits a different service with an independent time response and uptime rate. You don't need to implement any backend code! Just mock the calls to it.
  - For this exercise we are not concern with browser compatibility, you can go wild in terms of new apis or experimental features.

### Review
After the exercise, we will arrange a call to discuss your solution with you (as soon as possible, depending on availability). In preparation for the call, think about:
- what makes your solution scalable, maintainable & robust?
- what are the drawbacks of your solution?
- with more time, what could you do to improve your solution?

### Guidance

Because of the time restrictions you may not be able to do everything. This is intended ;), so focus on what you consider more relevant.

We have designed the exercise on purpose to be loose, allowing some creativity and the usage of previous experience. You are free to use the resources we provided or dismiss them, you can also use any technology or paradigm. The time allowed is tight, so you are also encouraged to reuse any code you have previously used somewhere else.

You should think about:
 - The project file structure
 - Handling of modularity and complexity, split of the different components
 - Readability and coherence of the code style
 - Interaction with mutable state and side effects
 - CSS composition
 - What to and not to test and how to test it
 - Approach to documentation
 - In general, how to reduce technical debt
 - A working solution. You can and should hand over some non working code, but try to deliver something working as well

### Useful Resources
To help you out, we have provided some resources. You don't need them to complete the exercise, but you may find them useful:
  - Some examples of the API [responses](examples) and their [schemas](schemas)
  - Some [basic CSS](base.css) that you can extend
