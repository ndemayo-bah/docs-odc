---
summary: Learn the best practices for fetching and displaying data in OutSystems.
tags: 
outsystems_tools: 
guid: 65834d5d-b36c-47b0-afc5-43ae35b5bd7d
locale: en-us
app_type: mobile apps, reactive web apps 
platform-version: odc
figma: 
---

# Best practices for fetching and displaying data

In OutSystems, you can fetch data to populate screens using aggregates or data actions. Follow these best practices to manage and display data from different sources efficiently.

## Use aggregates to fetch data from database entities

[Aggregates](../../data/fetch-data/aggregate.md) allow you to fetch data using an optimized query tailored to your needs. 

### Recommendations

Use aggregates to fetch data from database entities. Favor using aggregates over advanced queries.

### Benefits

When fetching data from database entities, aggregates offer the following advantages:

* Aggregates are visually defined and scoped to the screen, making it easy to retrieve the data needed for display.

* Aggregates automatically absorb changes in the data model and can load the local database's data from the server. 

* Aggregates support combining several entities and advanced filtering.

* Aggregates retrieve only the attributes that are used on the screen.

* Aggregates run asynchronously. Asynchronous fetching allows users to interact with the app while data loads.

For more information, refer to [Fetch and display data from the database in OutSystems](../interaction/fetch-display.md) and [Displaying Data on Screens](https://learn.outsystems.com/training/journeys/building-screens-with-data-637/displaying-data-on-screens/odc/109).

## Use data actions to fetch complex data from the database or to fetch external data

Data actions allow you to define custom server-side logic. The outputs of a data action can be used in screen widgets.

### Recommendations

Use data actions when:

* Fetching complex data from the database, which you cannot achieve using a single aggregate. 

* Fetching data from external sources (for example, REST APIs).

### Benefits

Data actions can call external REST web services or execute advanced SQL queries, allowing you to retrieve complex data from the database, which you wouldn’t be able to do using aggregates.

For more information, refer to [Displaying Data on Screens](https://learn.outsystems.com/training/journeys/building-screens-with-data-637/displaying-data-on-screens/odc/109).

## Keep Max. Records consistent with your needs

The Max. Records property of an aggregate defines the maximum number of records read from the database. If the Max. Records property is not set, all the records that match the criteria will be retrieved, increasing database load and response time.

### Recommendation

Set the aggregate's Max. Records property to match the amount of data you want to display.

### Benefits

Usually, there's no need to display thousands of records on a single screen, so retrieving them all from the database is unnecessary. Setting the Max. Records according to your needs optimizes the aggregate execution time and improves screen loading. This is especially useful in table records or when an aggregate is used to fetch a single record.

<div class="info" markdown="1">

Setting the Max. Records property in SQL elements doesn't change its SQL statement. This limit is only applied at the app level to the results returned by the database. Unlike aggregates, to filter the results at the database level, you must add an SQL clause to the SQL element statement (for example, TOP). 

</div>

## Don’t show a blank screen while data is being fetched

Plan what your app will display to the user while data is being fetched. 

### Recommendations

To avoid showing a blank screen while data is being fetched:

* Fetch smaller data when initializing the app. This renders essential elements while larger data loads in the background. 

* Inform users that data is loading. For example, use loading spinners, progress bars, or skeleton screens. 

### Benefits

By following these recommendations, you avoid the perception of an unresponsive or broken app, improving user experience.
