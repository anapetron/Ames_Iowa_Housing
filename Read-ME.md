# Project 2
_Author: Ana Petronijevic

---
## Problem Stateent
What are the top and bottom features of the top two and bottom two neighborhoods and what is their affect on the sales price.

### Executive Summary
- Imported training data
- Looked for corrupted columns and missing data
- Replaced missing data with the appropriate type
- Exported clean data as a csv.
- Additional EDA on outlier data per [Data Dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)
- Correlation matrix on entire set and graphical representation of data, including a linear regression describing the relationship between Sales Price and a particularly strongly correlated variable.
- Additional graphs specific for categorical data,
- Seperated Neighborhoods Series into dummy columns inorder to represent a categorical data numerically, and be able to utilize it in models.
- Train test split based on features selected, which were described in the EDA.
- Interpreting MSE, intercept, and coef scores
- Imported testing set and cleaned the data the same way as the training set
- Created predictions based on the features selected in the training set.

I recieved a dataset with over 80 features of homes in Ames, Iowa.  The dataset had about 26 columns that had missing information in there. For the purpose of this dataset I decided to fill in the missing information. I saved this as a new dataset to conduct EDA on a cleaned csv file which I can always reference.
The rows that I did choose to drop were from the data description we recieved. So, I droped any houses with more than 4000 sqft.
"I would recommend removing any houses with more than 4000 square feet from the data set (which eliminates these 5 unusual observations) before assigning it to students." - data description
I am doing this in the cleaned version instead of in the original file in case I want to come back and include outliers for a specific reason.
After looking through numerical and categorical columns, I wanted to see if there was any underlying information that I could learn from in a categorical column, Neighborhoods to be specific. Some seaborn plots can take categorical data and interpret it into graphs (see.)
Next, I wanted to specifically look at the top two most expensive and least expensive Neighborhoods.
Top
'Neighborhood_NridgHt',
'Neighborhood_NoRidge'
Bottom
'Neighborhood_NAmes'
'Neighborhood_OldTown'
Through conduting correlation matrix's and different graphs I was able to find the top features realted to the Neighborhoods I was researching.

I original onehotencoded the Neighborhood series originally, but it actually gave order to the Neighborhoods, where there actually isn't one. So I decided to pd.get_dummies instead.
I used the .iloc[:, 1:] method to state that I would like all rows, and columns from the 1st to the end, since Python is 0-indexed, it drops the '0th' column. Then I added the new colomn on the DataFrame using pandas concat, and axis=1 means it's added on the columns

- Nridght
  -  Top(Besides Sale price @ 45%)            Bottom besides pid at -25%
  -  Overall Qual - 38%                       Overall Cond - (-13%)
  -  Mas Vnr Area - 34%                       Enclosed Porch- (-9.5%)
  -  Total Bsmt Sqft - 34%                    Kitchen abv gr - (-5.1%)
  -  Garage Area 33%                          Bsmt .5 bath - (-6.3%)
  -  Garage Cars - 31%                        Bsmt Fin 2 - (-5.4%)

- NoRidge
  -  Top(besides sale price, 2nd 26%)         Bottom
  -  Gr Liv Area - 31%                        Overall cond - (-5.3%)
  -  2nd Floor Sqft - 24%                     Bsmt .5 bath - (-3.9%)
  -  Mass Vrn Area - 24%                      Kitch Abv Fr - (-3.2%)
  -  Top Rms Abv Gr - 21%                     Low Qual Fin Sf - (-1.7%)
  -  Overall Qual - 19%                       3Ssn Porch - (-1.6%)

- OldTown
  -  Top(besides pid at 20%)                  Bottom(bsides sale price,2nd at -21%)
  -  Enclosed Porch - 24%                     Yr Built - (-47%)
  -  Overall Cond - 18%                       Total Bsmt Sqft - (-18%)
  -  Low Qual Fin Sqft - 11%                  Overall Qual - (-18%)
  -  2nd flr sqft - 9.6%                      1st flr sqft - (-17%)
  -  Kitc abv gr - 7.7%                       Yr remod add & Garage Cars - (-16%)

- NAmes
   - Top                                      Bottom(besides pid 40%)
   - Overall Cond - 9.2%                      Yr Remod Add - (-29%)
   - Bsmt Fin sqft 2 - 8.4%                   Full Bath - (-26%)
   - Lot Frontage - 8.4%                      Overall Qual - (-23%)
   - Screenporch - 8.3%                       2nd flor sqft - (-22%)
   - Bsmt fin sqft 1 - 4.6%                   Gr Liv Area - (-19%)
