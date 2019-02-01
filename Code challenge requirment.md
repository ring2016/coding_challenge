# Code challenge requirment

Per talked this morning, attached please find the code challenge, and kindly submit the result with mail to me/public Github **by 9Jan**, thanks. 

**Code Challenge**

An organisation generates lots of data and the following challenge captures some of the issues our data engineers are expected to face on a daily basis. There is no single correct approach to this problem and this task is expected to create a conversation around domain modelling and tradeoffs.

**Background**

Our platform will generate immense amounts of user browsing/session data that we need to make sense of to inform product and other business decision. Assume that we have some log files generated real-time from our users active sessions.

```json
{

"userId": 1,

"sessionId": "{some-uuid}",

"timestamp": "2018-01-01T00:00:00.000000",

"url": "/foo/bar",

"experiments": "baz"

}

```

Each log item is structured as shown in the snippet above and is identified with a unique userId and sessionId . Users can make multiple separate page views within the same singe session. There is also a timestamp of page views recorded along with the URL of the page being viewed and identifiers for any A/B experiments the users may be a part of.

 

**Specifications**

Our business requires real-time processing of data given our users are global and active on our site 24/7. We would like the ability to understand and respond to changing user demand and preferences in real-time. 

 

The business would like to know a couple of key statistics about the user base which can be computed from the data provided.

\1. What are the top 5 most accessed URLs according to the session logs

\2. What is the average session time in mulliseconds across all users? The median? Max? Min?

 

**Tehcnology**

Assume that our organisation's data pipelines provide real-time capabilities. Your task is to parse the logs into the data pipeline, persist the log events and provide the necessary business insight via an API.

 

Take your visual que on the tech stack from the diagram below. The choice of technologies/databases is for you to decide but at a high level your task is to parse the logs into our streaming data pipeline, persist the log events and provide the necessary business insight via an API.

![image-20190109094042971](https://ws1.sinaimg.cn/large/006tNc79gy1fz0hu6jbu3j30vl03iaad.jpg)

The API should output in JSON its calculations according to the following specification

```json
{

"most_viewed_urls": ["url1", "url2", "url3", "url4", "url5"],

"session_stats": {

"median": 13942,

"mean": 10124,

"max": 34031,

"min": 921

}

}
```

The data for the code challenge will be provided in a compressed (zip) file located here: [see attached file]

You can deploy the solution to a cloud provider or run the entire stack locally using docker. Neither of these are prequisites and your choice will not impact how you're measured.

**How we will measure each submission**

**Functionality** — Does your program work according to the specifications of the problem?

**Modeling** — Do your data structures fit the business objects in the problem and is the program's control flow clear?

**Documentation** — Is your code appropriately documented in the form appropriate to your implementation language?

**Language Use** — Do you make good use of the features available in the language you chose?

**Testing** — Did you include tests that explain and reinforce the design of your code?





 
