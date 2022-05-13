The Earth offers a finite amount of copper. 
The first model just takes into account the world copper stock.

In order to find these parameters we need to find the data for the past production per year from the beginning of the production
The used data are taken from 1925 to 2020. 

production data sources: [^2] 

### Copper data

|Year |Copper [Mt]|
| :------- | :---------- | 
|1925|1.761|
|...|...|
|2020|20.6|

### Fitting [^3]

To fit the curve with the maximum reserve estimated by US Geological Survey we adjust the beginning year of the regression in order to take the year start at the beginning of the current peak and get realistic values for maximal stock.

### Extraction Price [^4]

We start with the price of 2020.
If the demand is higher than what is available for 2 years straight, the price rises.
It rises according to a sigmoid function :
![](Sigmoid.PNG)

with the ratio used_stock/demand as the argument. Ratio = 1 (demand fully answered) means x = -10 and ratio = 0 (nothing can be used) means x = 10. The upper bound is a constant (default is 50000), the lower bound is the price the previous year.
If after a recent raise, the demand is satisfied for 2 years straight, the price decreases (default : 0.95 * price previous year).
If the demand is answered to and the price is still 2020's, it can't go lower, therefore is maintained.


### Other data [^3]

The following data are integrated into the model

|  Region  | material type | current Reserve | Reserve unit |
| :------- | :--------:| ---------: | :-----------------: |
| World | copper | 2100 | million_tonnes |

### Sector using copper [^5]

| Sector |proportion of the global demand per year in %|demand in Million tonnes|
|:------- | :--------:|:-----------------:|
|Power generation|9.86|2.47|
|Power distribution and transmission|35.14|8.78|
|Construction|20|5|
|Appliance & electronics|12.5|3.125|
|Transports|12.5|3.125|
|Other|10|2.5|

Data implemented in the copper input.

### References 

[^1]: Jon Claerbout and Francis Muir - "Hubbert math" (2020) - Retrieved from: 'http://sepwww.stanford.edu/sep/jon/hubbert.pdf'
[^2]: US Geological Survey - "Copper Statistics and Information" - Retrieved from: 'https://www.usgs.gov/centers/national-minerals-information-center/copper-statistics-and-information'
[^3]: US Geological Survey - Mineral Commodity Summaries 2022 Copper - Retrieved from: 'https://pubs.usgs.gov/periodicals/mcs2022/mcs2022-copper.pdf'
[^4]: Macrotrends - Copper Prices, 45 Year Historical Chart - Retrieved from : 'https://www.macrotrends.net/1476/copper-prices-historical-chart-data'
[^5]: Copper Alliance - Copper Environmental Profile - Retrieved from : https://copperalliance.org/sustainable-copper/about-copper/copper-environmental-profile/
