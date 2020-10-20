Project 6: Anomaly Detection from tweet streams mentioning 'GOOG' tickr symbol
------------------------------------------------------------------------------------

--------------------------
Dataset Used
--------------------------
realTweets/realTweets/Twitter_volume_GOOG.csv

Real life dataset containing the number of times the tickr symbol 'GOOG' was mentioned in tweets on a given day every five minutes.

--------------------------
Feature Engineering
--------------------------
I have generated three new features from the value column. The first feature is the difference between consecutive values. The second feature is the cummulative sum which is monotonically increasing. The third feature is the entropy within a window. All of the features including the original value column show a noticeable anomaly around March 13 from visual inspection.

--------------------------
Anomaly Detection
--------------------------
I have used two different approaches for detecting anomalous time series data. Firstly, I have used an IsolationForest approach where the datapoints are divided based on random split value. In the case of an isolation forest, outliers are usually found along the shortest paths in the trees. Then, I have used a OneClassSVM classifier to identify anomalies based on the non-classified values. I have performed an additional step of normalizing the features before using the OneClassSVM classifier since convergence of this classifier depends on the normalized values.

--------------------------
Analysis
--------------------------
From both the IsolationForest and OneClassSVM approaches, a high anomaly index is visible from the second week of March to the first week of April. After a quick fact-checking, I believe the spike in 'GOOG' tickr may have been because of an inconsistency with the stock dividends for Canadian investors. A news article (https://sdtimes.com/2lemetry/googles-multi-device-reference-app-amazons-acquisition-2elemtry-sd-times-news-digest-march-13-2015/) from around that time may have caused Twitter users to share the news through tweets mentioning 'GOOG' tickr symbol.