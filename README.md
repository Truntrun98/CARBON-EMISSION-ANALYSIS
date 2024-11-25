# CARBON-EMISSION-ANALYSIS
This project is aim to analize the level of carbon emission based on industry fields, countries, time and more...


## 1. The top 10 products contributing the most to the carbon emission in average
### CODE to findout:
```sql
SELECT product_name, ROUND(AVG(carbon_footprint_pcf),2) 
FROM product_emissions 
GROUP BY product_name 
ORDER BY ROUND(AVG(carbon_footprint_pcf),2) DESC
LIMIT 10;
```
### Explanation: 

### Result:
| Product name                                                                                                                       | Carbon emission amount | 
| ---------------------------------------------------------------------------------------------------------------------------------: | ---------------------: | 
| Wind Turbine G128 5 Megawats                                                                                                       | 3718044.00             | 
| Wind Turbine G132 5 Megawats                                                                                                       | 3276187.00             | 
| Wind Turbine G114 2 Megawats                                                                                                       | 1532608.00             | 
| Wind Turbine G90 2 Megawats                                                                                                        | 1251625.00             | 
| Land Cruiser Prado. FJ Cruiser. Dyna trucks. Toyoace.IMV def unit.                                                                 | 191687.00              | 
| Retaining wall structure with a main wall (sheet pile): 136 tonnes of steel sheet piles and 4 tonnes of tierods per 100 meter wall | 167000.00              | 
| TCDE                                                                                                                               | 99075.00               | 
| Mercedes-Benz GLE (GLE 500 4MATIC)                                                                                                 | 91000.00               | 
| Mercedes-Benz S-Class (S 500)                                                                                                      | 85000.00               | 
| Mercedes-Benz SL (SL 350)                                                                                                          | 72000.00               |

## 2. Which industry group do those 10 products belong to?
### CODE to findout:
```sql
SELECT ig.industry_group as "Industry group", 
	   pe.product_name as "Product name", 
	   ROUND(AVG(pe.carbon_footprint_pcf),2) as "Carbon emission amount" 
FROM product_emissions pe
	                     LEFT JOIN industry_groups ig 
				         ON pe.industry_group_id = ig.id
GROUP BY pe.product_name
ORDER BY ROUND(AVG(pe.carbon_footprint_pcf),2) DESC
LIMIT 10;
```
### Explanation: 

### Result:
| Industry group                     | Product name                                                                                                                       | Carbon emission amount | 
| ---------------------------------: | ---------------------------------------------------------------------------------------------------------------------------------: | ---------------------: | 
| Electrical Equipment and Machinery | Wind Turbine G128 5 Megawats                                                                                                       | 3718044.00             | 
| Electrical Equipment and Machinery | Wind Turbine G132 5 Megawats                                                                                                       | 3276187.00             | 
| Electrical Equipment and Machinery | Wind Turbine G114 2 Megawats                                                                                                       | 1532608.00             | 
| Electrical Equipment and Machinery | Wind Turbine G90 2 Megawats                                                                                                        | 1251625.00             | 
| Automobiles & Components           | Land Cruiser Prado. FJ Cruiser. Dyna trucks. Toyoace.IMV def unit.                                                                 | 191687.00              | 
| Materials                          | Retaining wall structure with a main wall (sheet pile): 136 tonnes of steel sheet piles and 4 tonnes of tierods per 100 meter wall | 167000.00              | 
| Materials                          | TCDE                                                                                                                               | 99075.00               | 
| Automobiles & Components           | Mercedes-Benz GLE (GLE 500 4MATIC)                                                                                                 | 91000.00               | 
| Automobiles & Components           | Mercedes-Benz S-Class (S 500)                                                                                                      | 85000.00               | 
| Automobiles & Components           | Mercedes-Benz SL (SL 350)                                                                                                          | 72000.00               | 

## 3. The top 10 industries with the hightest level of carbon emission in average
### CODE to findout:
```sql
SELECT ig.industry_group as "Industry group",  
	   ROUND(AVG(pe.carbon_footprint_pcf),2) as "Carbon emission amount" 
FROM product_emissions pe
	                     LEFT JOIN industry_groups ig 
				         ON pe.industry_group_id = ig.id
GROUP BY ig.industry_group
ORDER BY ROUND(AVG(pe.carbon_footprint_pcf),2) DESC
LIMIT 10;
```
### Explanation:

### Result:
| Industry group                                   | Carbon emission amount | 
| -----------------------------------------------: | ---------------------: | 
| Electrical Equipment and Machinery               | 891050.73              | 
| Automobiles & Components                         | 35373.48               | 
| "Pharmaceuticals, Biotechnology & Life Sciences" | 24162.00               | 
| Capital Goods                                    | 7391.77                | 
| Materials                                        | 3208.86                | 
| "Mining - Iron, Aluminum, Other Metals"          | 2727.00                | 
| Energy                                           | 2154.80                | 
| Chemicals                                        | 1949.03                | 
| Media                                            | 1534.47                | 
| Software & Services                              | 1368.94                | 

## 4. Top 10 companies with the highest contribution to carbon emssion in average
### CODE to findout:
```sql
SELECT c.company_name as "Company name",  
	   ROUND(AVG(pe.carbon_footprint_pcf),2) as "Carbon emission amount" 
FROM product_emissions pe
	                     LEFT JOIN companies c
				         ON pe.company_id = c.id
GROUP BY c.company_name
ORDER BY ROUND(AVG(pe.carbon_footprint_pcf),2) DESC
LIMIT 10;
```
### Explanation:

### Result:
| Company name                           | Carbon emission amount | 
| -------------------------------------: | ---------------------: | 
| "Gamesa Corporación Tecnológica, S.A." | 2444616.00             | 
| "Hino Motors, Ltd."                    | 191687.00              | 
| Arcelor Mittal                         | 83503.50               | 
| Weg S/A                                | 53551.67               | 
| Daimler AG                             | 43089.19               | 
| General Motors Company                 | 34251.75               | 
| Volkswagen AG                          | 26238.40               | 
| Waters Corporation                     | 24162.00               | 
| "Daikin Industries, Ltd."              | 17600.00               | 
| CJ Cheiljedang                         | 15802.83               | 

## 5. Top 10 countries with the highest contribution to carbon emssion in average
### CODE to findout:
```sql
SELECT ct.country_name as "Country",  
	   ROUND(AVG(pe.carbon_footprint_pcf),2) as "Carbon emission amount" 
FROM product_emissions pe
	                     LEFT JOIN countries ct
				         ON pe.country_id = ct.id
GROUP BY ct.country_name
ORDER BY ROUND(AVG(pe.carbon_footprint_pcf),2) DESC
LIMIT 10;
```
### Explanation:
### Result:
| Country      | Carbon emission amount | 
| -----------: | ---------------------: | 
| Spain        | 699009.29              | 
| Luxembourg   | 83503.50               | 
| Germany      | 33600.37               | 
| Brazil       | 9407.61                | 
| South Korea  | 5665.61                | 
| Japan        | 4600.26                | 
| Netherlands  | 2011.91                | 
| India        | 1535.88                | 
| USA          | 1332.60                | 
| South Africa | 1119.27                | 

## 6. Average Carbon emission trend over year
### CODE to findout:
```sql
SELECT year as Year,
	   ROUND(AVG(carbon_footprint_pcf),2) as "Carbon emission amount"
FROM product_emissions
GROUP BY year
ORDER BY year;
```
### Explanation:
### Result:
| Year | Carbon emission amount | 
| ---: | ---------------------: | 
| 2013 | 2399.32                | 
| 2014 | 2457.58                | 
| 2015 | 43188.90               | 
| 2016 | 6891.52                | 
| 2017 | 4050.85                | 

## 7. Which industry groups has demonstrated the most notable decrease in carbon footprints (PCFs) over time?
### CODE to findout:
```sql
SELECT ig.industry_group as "Industry group",
	   ROUND(AVG(CASE WHEN year = 2013 THEN pe.carbon_footprint_pcf ELSE NULL END), 2) AS "2013 emission",
       ROUND(AVG(CASE WHEN year = 2014 THEN pe.carbon_footprint_pcf ELSE NULL END), 2) AS "2014 emission",
       ROUND(AVG(CASE WHEN year = 2015 THEN pe.carbon_footprint_pcf ELSE NULL END), 2) AS "2015 emission",
       ROUND(AVG(CASE WHEN year = 2016 THEN pe.carbon_footprint_pcf ELSE NULL END), 2) AS "2016 emission",
       ROUND(AVG(CASE WHEN year = 2017 THEN pe.carbon_footprint_pcf ELSE NULL END), 2) AS "2017 emission"
FROM product_emissions pe
						 LEFT JOIN industry_groups ig
						 ON pe.industry_group_id = ig.id
GROUP BY ig.industry_group
ORDER BY ig.industry_group;
```
### Explanation:
### Result:
| Industry group                                                         | 2013 emission | 2014 emission | 2015 emission | 2016 emission | 2017 emission | 
| ---------------------------------------------------------------------: | ------------: | ------------: | ------------: | ------------: | ------------: | 
| "Consumer Durables, Household and Personal Products"                   | [NULL]        | [NULL]        | 116.38        | [NULL]        | [NULL]        | 
| "Food, Beverage & Tobacco"                                             | 94.25         | 99.44         | 0.00          | 4011.56       | 143.73        | 
| "Forest and Paper Products - Forestry, Timber, Pulp and Paper, Rubber" | [NULL]        | [NULL]        | 685.31        | [NULL]        | [NULL]        | 
| "Mining - Iron, Aluminum, Other Metals"                                | [NULL]        | [NULL]        | 2727.00       | [NULL]        | [NULL]        | 
| "Pharmaceuticals, Biotechnology & Life Sciences"                       | 16135.50      | 40215.00      | [NULL]        | [NULL]        | [NULL]        | 
| "Textiles, Apparel, Footwear and Luxury Goods"                         | [NULL]        | [NULL]        | 14.33         | [NULL]        | [NULL]        | 
| Automobiles & Components                                               | 26037.80      | 20910.45      | 37146.68      | 40138.09      | [NULL]        | 
| Capital Goods                                                          | 5015.83       | 10411.00      | 3505.00       | 796.13        | 18989.80      | 
| Chemicals                                                              | [NULL]        | [NULL]        | 1949.03       | [NULL]        | [NULL]        | 
| Commercial & Professional Services                                     | 144.63        | 119.25        | [NULL]        | 96.33         | 370.50        | 
| Consumer Durables & Apparel                                            | 286.70        | 113.10        | [NULL]        | 40.07         | [NULL]        | 
| Containers & Packaging                                                 | [NULL]        | [NULL]        | 373.50        | [NULL]        | [NULL]        | 
| Electrical Equipment and Machinery                                     | [NULL]        | [NULL]        | 891050.73     | [NULL]        | [NULL]        | 
| Energy                                                                 | 750.00        | [NULL]        | [NULL]        | 2506.00       | [NULL]        | 
| Food & Beverage Processing                                             | [NULL]        | [NULL]        | 7.05          | [NULL]        | [NULL]        | 
| Food & Staples Retailing                                               | [NULL]        | 77.30         | 70.60         | 0.50          | [NULL]        | 
| Gas Utilities                                                          | [NULL]        | [NULL]        | 61.00         | [NULL]        | [NULL]        | 
| Household & Personal Products                                          | 0.00          | [NULL]        | [NULL]        | [NULL]        | [NULL]        | 
| Materials                                                              | 4177.35       | 1513.56       | [NULL]        | 1401.06       | 11217.74      | 
| Media                                                                  | 2411.25       | 2411.25       | 479.75        | 602.67        | [NULL]        | 
| Retailing                                                              | [NULL]        | 6.33          | 5.50          | [NULL]        | [NULL]        | 
| Semiconductors & Semiconductor Equipment                               | [NULL]        | 16.67         | [NULL]        | 2.00          | [NULL]        | 
| Semiconductors & Semiconductors Equipment                              | [NULL]        | [NULL]        | 1.00          | [NULL]        | [NULL]        | 
| Software & Services                                                    | 1.50          | 29.20         | 1523.73       | 2538.44       | 690.00        | 
| Technology Hardware & Equipment                                        | 1053.45       | 1780.44       | 1895.66       | 65.25         | 788.34        | 
| Telecommunication Services                                             | 52.00         | 45.75         | 45.75         | [NULL]        | [NULL]        | 
| Tires                                                                  | [NULL]        | [NULL]        | 1011.00       | [NULL]        | [NULL]        | 
| Tobacco                                                                | [NULL]        | [NULL]        | 1.00          | [NULL]        | [NULL]        | 
| Trading Companies & Distributors and Commercial Services & Supplies    | [NULL]        | [NULL]        | 39.83         | [NULL]        | [NULL]        | 
| Utilities                                                              | 61.00         | [NULL]        | [NULL]        | 61.00         | [NULL]        | 

