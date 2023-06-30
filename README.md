# U.S. Medical Insurance Costs

1. Look over your dataset

- Open insurance.csv and take a look at the file

2. Scoping to Project

- Find out the average age of the patients in the dataset.
- Analyze where a majority of the individuals are from.
- Look at the different costs between smokers vs. non-smokers.
- Figure out what the average age is for someone who has at least one child in this dataset.

3. Import your dataset
4. Save your dataset via Python variables


5. Build out analysis functions or class methods

- averagaAge()
- majorityIndividualsFrom()
- diffCostsBetweenSmokersNonSmokers()
- averageAgeWithChildrens()


```python
import csv
insurances={}
#3. Import insurance.csv into your Python file and inspect the contents
with open('insurance.csv', newline='') as csvfile:
    #4. Save the features of your dataset (the columns) from insurance.csv by storing them in variables that can be used for analysis
    reader = csv.DictReader(csvfile)   
    insurances = list(reader)
    
#5. Define analysis funtions

#-Find out the average age of the patients in the dataset.
def averagaAge():
    #define variable to sum all ages 
    TotalAge = 0
    for row in insurances:
        TotalAge += int(row["age"])
        #return AVG age of patients
    return "The average age of the patients is " + str(int(TotalAge / len(insurances)))

#- Analyze where a majority of the individuals are from.
def majorityIndividualsFrom():
    MayorFrom = ""
    #Define Dict to save count by region
    regions = {}
    #set counter to every region 
    for row in insurances:
        if not row["region"] in regions: regions[row["region"]]=0
        regions[row["region"]] += 1    
    #Order Regions by values descending and get the first key
    MayorFrom = list(dict(sorted(regions.items(), key=lambda x: x[1], reverse=True)).keys())[0]
    return "The majority of the individuals are from {_from}".format(_from = MayorFrom)

def diffCostsBetweenSmokersNonSmokers():
    Diff = ""
    #Define Dict to save sum by Smoker= "yes" or Non-Smoker = "no"
    CostSmokerYesOrNot = {"yes" : 0, "no" : 0}
    #set sum to every Smoker= "yes" or Non-Smoker = "no" into CostSmokerYesOrNot
    for row in insurances:
        CostSmokerYesOrNot[row["smoker"]] += float(row["charges"])
    #print(CostSmokerYesOrNot)
    #Set diff between Smokers or Non-Smokers
    Diff = CostSmokerYesOrNot["yes"] - CostSmokerYesOrNot["no"]
    return "The different costs between smokers vs. non-smokers is {diff}".format(diff =Diff)

def averageAgeWithChildrens():
    #define variable to sum all ages when have least one a child
    TotalAge = 0
    CanPatiens = 0
    for row in insurances:
        if int(row["children"]) >=1:
            TotalAge += int(row["age"])
            CanPatiens +=1
    #print(CanPatiens)
    #return AVG age 
    return "The average age when have least one a child is " + str(int(TotalAge / CanPatiens))
```


```python
averagaAge()
```




    'The average age of the patients is 39'




```python
majorityIndividualsFrom()
```




    'The majority of the individuals are from southeast'




```python
diffCostsBetweenSmokersNonSmokers()
```




    'The different costs between smokers vs. non-smokers is -192297.9470789954'




```python
averageAgeWithChildrens()
```




    'The average age when have least one a child is 39'




```python

```
