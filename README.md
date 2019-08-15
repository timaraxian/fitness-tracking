# fitness-tracking

For an example checkout the [demo notebook](https://github.com/timaraxian/fitness-tracking/blob/master/demo/demo_weight_calories.ipynb)

### What is needed in order to use this notebook?

- Fill in the variables in the second cell
- A csv file which records the calories you've consumed each day
- A csv file which contains one or both of your weight in the morning, weight in the evening, and optionally bodyfat percentage

#### Variables
- `date_of_birth` your date of birth
- `height` your height in centimetres
- `sex` your sex (if you supply your body fat percentage this is not required)
- `exercise_level` 
		- 0 = sedentary
		- 1 = light (1-2 days a week)
		- 2 = moderate (3-5 days a week)
		- 3 = heavy (6-7 days a week)
		- 4 = athlete (2 times a day )
- `fill_missing_days` boolean flag if you want the chart to linear interpolate many skipped days
- `calories_path` path to the calories csv file
- `weight_path` path to the weight csv file
- `planned_deficit` how many calories you want to be in deficit everyday
- `use_bodyfat` even if bodyfat is supplied in the csv you can choose to use the mifflin calculation of basal metabolic rate by setting this to false.

#### Calories csv

|ts|item|calories|
|:--:|:----:|:--------:|
|YYYY-MM-DD|string|float

```
ts,item,calories
2019-01-01,breakfast,234
2019-01-01,coffee,10
2019-01-01,biscuits,35
2019-01-01,banh-mi,650
2019-01-01,spaghetti,700
2019-01-01,protein-shake,113
...
2019-05-12,breakfast,320
2019-05-12,lunch,466
2019-05-12,matcha-latte,150
2019-05-12,dinner,1130
2019-05-13,croissant,370
2019-05-13,frappucino,730
2019-05-13,dumplings,1200
2019-05-13,popcorn,300
2019-05-13,coke,105
2019-05-14,daily,1840
...
```

#### Weight csv
|ts|weight_am|weight_pm|bodyfat
|:--:|:-------------:|:-------------:|:-------:|
|YYYY-MM-DD|float|float|float

```
ts,weight_am,weight_pm,bodyfat
2019-01-01,85.2,85.9,20
2019-01-02,85.0,85.6,
2019-01-02,,85.5,19.7
2019-01-03,84.3,84.0,
2019-01-06,82,81.7,
```

### FAQ

1. Do I need to record my weight in both the morning and evening?
	Nope.
2. Do I need to record my bodyfat everyday? or at all?
	Nope, the bodyfat percentage is just used to generate a more accurate basal metabolic rate. Height, weight, age and sex are perfectly fine
4. What if I skip one date?
	That's ok the code will linear interpolate the missing day in the charts
5. What if I skip many dates?
	There is a variable `fill_missing_days` which can be set to `True` which will then linear interpolate all of the missing dates, however this might have unexpected results

### Sources
[Basal Metabolic Rate](https://en.wikipedia.org/wiki/Basal_metabolic_rate)
[Total Daily Energy Expenditure & Basal Metabolic Rate Calculator](https://goodcalculators.com/tdee-bmr-calculator/)
	
