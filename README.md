# DMML2019_Team_Microsoft

## Team Microsoft members   

- Besson, Dario – MLaw in Legal Issues, Crime and Security of IT (UNIL)
- Fleck, Alyssa – MLaw in Legal Issues, Crime and Security of IT (UNIL)
- Liao, Yi Chuan – Exchange Program (Taiwan)
- Nkoumondo, Laryssa – MLaw in Legal Issues, Crime and Security of IT (UNIL)

## The project

The goal for this project is to identify restaurants/food establishments that are likely to fail the next food inspection based on the results of previous reviews. The main challenge lies in the proper use of temporal and textual data contained in the set.
Food safety is not to be taken lightly as it is a matter of public health. Food inspections aim to reduce the sanitary risks associated with poor practices in the food service industry. Building a model that would help large cities predict which establishments to target first would further mitigate these risks.

## The data

The data set was found on the City of Chicago's data portal. The City provides records for past food inspections conducted from January 1, 2010 to the present. The dimensionality is 17, while the cardinality is 195’736 (as of ‎November 9th, ‎2019, ‏‎16:06).
The set contains information about violations that were observed during the inspections, the risk assessment of the establishment, the facility type of the establishments and location amongst other things.

Data augmentation possibilities are : using the coordinates to determine the neighbourhood in which an establishment is settled, using the license ID to retrieve the business activity from another data set available on the same portal, retrieving information about the location using an API (such as Microsoft Bing Maps’ API, the validity of this method still has to be assessed).

Source: City of Chicago (2019, November 9). Food Inspections. Chicago Data Portal. Retrieved from https://data.cityofchicago.org/Health-Human-Services/Food-Inspections/4ijn-s7e5.

## The approach

The methods used for this project will primarily be classification and text analytics. The latter would be used to process textual information (i.e. “description of the findings that caused the violation”) in order to compute a score that would indicate if the staff comments are positive or negative.
Logistic regression seems to be a valid approach for the second step which would be a binary classification (“fail” or “pass”) or multiclass classification (if the third class “pass with conditions” was added).


## Post-feedback remarks :

- Classifying the inspection staff's comments could be tricky due to unlabelled data. One possibility could be to use the risk indicator 1 (low) and 3 (high) and the inspection result to train the classifier. The underlying assumption is that comments for high risk establishments should be more negative and comments for low risk establishments more positive. The feasibility still has to be discussed.
- One feature that could be taken into account would be the temperature average in the last 5 days before inspection.
- Another feature could be the cuisine type (https://developer-tripadvisor.com/content-api/business-content/cuisines/) accessed through TripAdvisor API.
- TripAdvisor API allows requests about the "cleanliness rating" and could be use as a feature. There is one issue though, only the current rating can be retrieved, which does not reflect the rating variation over time.
