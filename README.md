# DMML2019_Team_Microsoft

## Team Microsoft members   

- Besson, Dario – MLaw in Legal Issues, Crime and Security of IT (UNIL)
- Fleck, Alyssa – MLaw in Legal Issues, Crime and Security of IT (UNIL)
- Liao, Yi Chuan – Exchange Program (Taiwan)
- Nkoumondo, Laryssa – MLaw in Legal Issues, Crime and Security of IT (UNIL)

## The project

The goal for this project is to identify restaurants/food establishments that are likely to fail the next food inspection based on the results of previous reviews. The main challenge lies in the proper use of temporal and textual data contained in the set.
Food safety is not to be taken lightly as it is a matter of public health. Food inspections aim to reduce the sanitary risks associated with poor practices in the food service industry. Building a model that would help large cities predict which establishments to target first would further mitigate these risks.

_Update (2019, November 25) :_ The goals was adapted. The new objective is to predict the result of inspections based on a seat of features including inspections' and restaurants' characteristics.

## The data

The data set was found on the City of Chicago's data portal. The City provides records for past food inspections conducted from January 1, 2010 to the present. The dimensionality is 17, while the cardinality is 195’736 (as of ‎2019, November 9 [04:06 PM]).
The set contains information about violations that were observed during the inspections, the risk assessment of the establishment, the facility type of the establishments and location amongst other things.

**Note :** There is a file called "SOURCES" in which the different datasets used in this project are regrouped.

Data augmentation possibilities are :

- Use the weather history for Chicago to compute the average maximum temperature of the last 3 days before inspection and also retrieve the maximum temperature on the day of inspection.
- Use the license ID to retrieve the approximate date of creation of the business from another data set available on the same portal (Business Licenses, see sources).
- Extract information from other features in the original dataset. For instance, the week day (Monday, Tuesday, ...) of the inspection based on the date.
- ~~Retrieve information about the location using an API~~ (such as Microsoft Bing Maps’ API, the validity of this method was assessed and the method was abandoned because information that could be retrieved was limited.).
- ~~Use the coordinates to determine the neighbourhood in which an establishment is settled~~ (used geographic coordinates instead).

Source: City of Chicago (2019, November 9). Food Inspections. Chicago Data Portal. Retrieved from https://data.cityofchicago.org/Health-Human-Services/Food-Inspections/4ijn-s7e5.

_Update (2019, December 9) :_ Revision of data augmentation possibilities.

## The approach

The methods used for this project will primarily be classification and text analytics. The latter would be used to process textual information (i.e. “description of the findings that caused the violation”) in order to compute a score that would indicate if the staff comments are positive or negative.
Logistic regression seems to be a valid approach for the second step which would be a binary classification (“fail” or “pass”) or multiclass classification (if the third class “pass with conditions” was added).

_Update (2019, November 25) :_ The initial idea was to work on time series. Due to time constraint, the scope of the project was adapted. The classification will be applied to inspections individually with a variety of classifiers which has to be determined.

## The notebooks
Several notebooks were created for this project :
- _0_data_cleaning.ipynb :_ The data needed to be cleaned in some aspects. Choices were made regarding which classes to keep for categorical features such as "Facility Type" for which more than 400 classes existed. Missing data was dealt with. Also, some features in the original data set were dropped.
- _1_EDA.ipynb :_ This file contains the exploratory data analysis which provides an insight on the data that will be used for this project. This includes map visualisation, histograms, etc.
- _2_augmentation.ipynb :_ This file is the concretisation of the data augmentation possibilities which were presented above.
- _3_prediction.ipynb :_ All the models tested are regrouped in this file. After normalising and encoding the data, several models were tested and assessed. This includes : logistic regression, (TO BE UPDATED WITH OTHER TECHNIQUES).

## Post-feedback remarks (2019, November 18) :

- Classifying the inspection staff's comments could be tricky due to unlabelled data. One possibility could be to use the risk indicator 1 (low) and 3 (high) and the inspection result to train the classifier. The underlying assumption is that comments for high risk establishments should be more negative and comments for low risk establishments more positive. The feasibility still has to be discussed.
- One feature that could be taken into account would be the temperature average in the last 5 days before inspection.
- Another feature could be the cuisine type (https://developer-tripadvisor.com/content-api/business-content/cuisines/) accessed through TripAdvisor API.
- TripAdvisor API allows requests about the "cleanliness rating" and could be use as a feature. There is one issue though, only the current rating can be retrieved, which does not reflect the rating variation over time.

## Post-feedback remarks (2019, November 25) :

- The scope of the project was adapted.
- Text analysis for violations was ruled out.
- In July 2018, there was a change in the regulation. As a result, new violations were created and the classification (minor, serious, critical) changed. Dropping the inspections that occurred after July 1 could solve the issue. Alternatively, the "Violations" feature could be dropped and compensated with other features (ex : total duration of activity).
