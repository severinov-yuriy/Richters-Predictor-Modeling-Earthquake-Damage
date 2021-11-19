# **Richter’s Predictor: Modeling Earthquake Damage**

This is a late solution for competition on [**drivendata.org**](http://drivendata.org) within the course **"*Predictive Analytics for Supply Chain Management"*** on ***"Strategic Management of Logistics and Supply Chains in the Digital Economy"*** master's program.

Requirements for solution was to build a machine learning model, which predicts level of damage for building on their technical, historical, economical characteristics.

Wins model, which shows the best result on micro-averaged F1 indicator. That solution takes 678 place of 4 318 participants. It’s the top 16% of all participants. Solution was prepared by the study group of three person – me and my team members, who have not got github repository.

Short result of our project you can see in "Richter's Predictor_ Modeling Earthquake Damage.pdf" file. Detailed solution step-by-step you can see in "report.Rmd" file.

Summary:

Dataset includes 39 variables, and mainly consists of information on the buildings’ structure and their legal ownership. The `building_id` column is a unique and random identifier. The remaining 38 features are described in the report file.

EDA result:

- `area_percentage` and `height_percentage` are correlating;
- has_secondary_use correlates with its subtypes;
- height_percentage is correlating with count_floors_pre_eq stronger than any other pairs of variables;
- area_percentage and height_percentage are correlating with has_super_structure features and secondary use of buildings;
- older buildings suffered from more damage, than the newer ones, but newer buildings were still fairly damaged;
- percent of seriously damaged higher buildings is much more than of the lower ones;
- depending on age, count of floors, number of families, variables actually behave in different way.

We made the following transformations with the data to make them eligible
for the applied models in order to ultimately optimize the final result:

- converted categorical variables into factors
- converted categorical binary variables into dummies
- relevelled dataset on the basic damage value of 2

We tried to implement the following extensions, but with them dataset expanded up to 79 variables and we were unable to calculate any model on the subset larger than 1% of all data:

- count_of_floors_per_age <- count_floors_pre_eq/(age+1)
- count_of_floors_per_area <- count_floors_pre_eq/area_percentage
- count_of_floors_per_height <- count_floors_pre_eq/height_percentage
- ****area_per_age <- area_percentage/(age+1)
- height_per_age <- height_percentage/(age+1)
- families_on_floor <- count_families/count_floors_pre_eq
- families_on_area <- count_families/area_percentage
- families_on_height <- count_families/height_percentage

With that implementations final result might have been much higher

The best result shows C5.0 decision tree, it performs about 0.71 F-1 micro-averaged score.

Please, check "report.rmd" and "Richter's Predictor_ Modeling Earthquake Damage.pdf" for more detailed solution.
