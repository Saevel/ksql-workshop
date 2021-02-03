# KSQL Workshop

## Creating tables and streams

Go to the 'stocks' folder and modify the top portion of the "script.sql" file, so that:

* you create a stream, based on the "stock_prices" Kafka topic, called "STOCK_PRICES_STREAM"
with JSON value format

* you create a table, based on the "stock_prices" Kafka topic, called "STOCK_PRICES_TABLE",
keyed by "STOCK_ID" field and with the JSON value format

Once this is done, run "./gradlew :testModule -PmoduleName=stocks" or "gradlew.bat :testModule -PmoduleName=stocks" to
verify the correctness of your implementation

## Transformations

Go to the "new_hires" folder and modify the "script.sql" file, so that:

* you use the "insert as select" syntax to filter out new hires with salary larger than 3000 and stream them into the
"HIGH_SALARY_HIRES" stream, which is already defined

* you use the "create as select" syntax to create the "MAX_SALARIES" table, which would store, for each country, its
maximal salary as "MAX_SALARY" and store it on the "max_salaries" topic, in the "JSON" value format and with "country" 
as key

Once this is done, run "./gradlew :testModule -PmoduleName=new_hires" or "gradlew.bat :testModule -PmoduleName=new_hires"
to verify the correctness of your implementation

## Joins and Windowing

Go to the "recommendations" folder and modify the "script.sql" file so that:

* you create the "USERS_INTERESTED_IN_INV" table, which will store, in the "DELIMITED" format, on the "users_interested"
Kafka topic, all userId's for users who had at least 2 events of type "CLICK" with "data" object containing the 
"investment" as "target" inside the "data" object, during each 3 seconds (Tumbling Window)

* you re-key the data in the "SERVICE_RECOMMENDATIONS" stream so that it can be joined with "USERS_INTERESTED_IN_INV",
fulfilling all the co-partitioning requirements

* you join the "USERS_INTERESTED_IN_INV" and re-keyed recommendations to provide an array of recommended service as
"recommended_servcies" and "userId", in a table called "USER_RECOMMENDATIONS", stored on the "user_recommendations" topic,
in the 'AVRO' storage format

Once this is done, run "./gradlew :testModule -PmoduleName=recommendations" or 
"gradlew.bat :testModule -PmoduleName=recommendations" to verify the correctness of your implementation
