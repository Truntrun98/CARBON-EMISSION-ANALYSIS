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
### Step 1: Retrieve all the data of each Industry group's yearly emission:
### CODE to findout:
```sql
SELECT ig.industry_group as "Industry group",
       ROUND(AVG(CASE WHEN year = 2013 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS "2013 emission",
       ROUND(AVG(CASE WHEN year = 2014 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS "2014 emission",
       ROUND(AVG(CASE WHEN year = 2015 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS "2015 emission",
       ROUND(AVG(CASE WHEN year = 2016 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS "2016 emission",
       ROUND(AVG(CASE WHEN year = 2017 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS "2017 emission"
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
| "Consumer Durables, Household and Personal Products"                   | 0.00          | 0.00          | 116.38        | 0.00          | 0.00          | 
| "Food, Beverage & Tobacco"                                             | 39.02         | 20.98         | 0.00          | 783.51        | 24.70         | 
| "Forest and Paper Products - Forestry, Timber, Pulp and Paper, Rubber" | 0.00          | 0.00          | 685.31        | 0.00          | 0.00          | 
| "Mining - Iron, Aluminum, Other Metals"                                | 0.00          | 0.00          | 2727.00       | 0.00          | 0.00          | 
| "Pharmaceuticals, Biotechnology & Life Sciences"                       | 10757.00      | 13405.00      | 0.00          | 0.00          | 0.00          | 
| "Textiles, Apparel, Footwear and Luxury Goods"                         | 0.00          | 0.00          | 14.33         | 0.00          | 0.00          | 
| Automobiles & Components                                               | 1783.41       | 3150.89       | 11194.89      | 19244.29      | 0.00          | 
| Capital Goods                                                          | 1719.71       | 2677.11       | 100.14        | 181.97        | 2712.83       | 
| Chemicals                                                              | 0.00          | 0.00          | 1949.03       | 0.00          | 0.00          | 
| Commercial & Professional Services                                     | 26.30         | 10.84         | 0.00          | 65.68         | 16.84         | 
| Consumer Durables & Apparel                                            | 42.16         | 48.24         | 0.00          | 17.09         | 0.00          | 
| Containers & Packaging                                                 | 0.00          | 0.00          | 373.50        | 0.00          | 0.00          | 
| Electrical Equipment and Machinery                                     | 0.00          | 0.00          | 891050.73     | 0.00          | 0.00          | 
| Energy                                                                 | 150.00        | 0.00          | 0.00          | 2004.80       | 0.00          | 
| Food & Beverage Processing                                             | 0.00          | 0.00          | 7.05          | 0.00          | 0.00          | 
| Food & Staples Retailing                                               | 0.00          | 32.21         | 29.42         | 0.08          | 0.00          | 
| Gas Utilities                                                          | 0.00          | 0.00          | 61.00         | 0.00          | 0.00          | 
| Household & Personal Products                                          | 0.00          | 0.00          | 0.00          | 0.00          | 0.00          | 
| Materials                                                              | 1113.96       | 420.43        | 0.00          | 490.37        | 1184.09       | 
| Media                                                                  | 643.00        | 643.00        | 127.93        | 120.53        | 0.00          | 
| Retailing                                                              | 0.00          | 3.80          | 2.20          | 0.00          | 0.00          | 
| Semiconductors & Semiconductor Equipment                               | 0.00          | 10.00         | 0.00          | 0.80          | 0.00          | 
| Semiconductors & Semiconductors Equipment                              | 0.00          | 0.00          | 1.00          | 0.00          | 0.00          | 
| Software & Services                                                    | 0.18          | 4.29          | 672.24        | 671.94        | 20.29         | 
| Technology Hardware & Equipment                                        | 228.84        | 626.82        | 397.59        | 5.87          | 103.34        | 
| Telecommunication Services                                             | 5.78          | 20.33         | 20.33         | 0.00          | 0.00          | 
| Tires                                                                  | 0.00          | 0.00          | 1011.00       | 0.00          | 0.00          | 
| Tobacco                                                                | 0.00          | 0.00          | 1.00          | 0.00          | 0.00          | 
| Trading Companies & Distributors and Commercial Services & Supplies    | 0.00          | 0.00          | 39.83         | 0.00          | 0.00          | 
| Utilities                                                              | 30.50         | 0.00          | 0.00          | 30.50         | 0.00          |
### Step 2: To findout the Industry groups having the lower carbon emission in the comparision of 2017's emission and 2013's emission
### CODE to findout:
```sql
SELECT ig.industry_group as "Industry group",
       ROUND(AVG(CASE WHEN year = 2013 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS "2013 emission",
       ROUND(AVG(CASE WHEN year = 2014 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS "2014 emission",
       ROUND(AVG(CASE WHEN year = 2015 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS "2015 emission",
       ROUND(AVG(CASE WHEN year = 2016 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS "2016 emission",
       ROUND(AVG(CASE WHEN year = 2017 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) AS "2017 emission"
FROM product_emissions pe
                         LEFT JOIN industry_groups ig
                         ON pe.industry_group_id = ig.id
GROUP BY ig.industry_group
HAVING
	  ROUND(AVG(CASE WHEN year = 2017 THEN pe.carbon_footprint_pcf ELSE 0 END), 2) < ROUND(AVG(CASE WHEN year = 2013 THEN pe.carbon_footprint_pcf ELSE 0 END), 2)
ORDER BY ig.industry_group;
```
### Explanation:
### Result:
| Industry group                                   | 2013 emission | 2014 emission | 2015 emission | 2016 emission | 2017 emission | 
| -----------------------------------------------: | ------------: | ------------: | ------------: | ------------: | ------------: | 
| "Food, Beverage & Tobacco"                       | 39.02         | 20.98         | 0.00          | 783.51        | 24.70         | 
| "Pharmaceuticals, Biotechnology & Life Sciences" | 10757.00      | 13405.00      | 0.00          | 0.00          | 0.00          | 
| Automobiles & Components                         | 1783.41       | 3150.89       | 11194.89      | 19244.29      | 0.00          | 
| Commercial & Professional Services               | 26.30         | 10.84         | 0.00          | 65.68         | 16.84         | 
| Consumer Durables & Apparel                      | 42.16         | 48.24         | 0.00          | 17.09         | 0.00          | 
| Energy                                           | 150.00        | 0.00          | 0.00          | 2004.80       | 0.00          | 
| Media                                            | 643.00        | 643.00        | 127.93        | 120.53        | 0.00          | 
| Technology Hardware & Equipment                  | 228.84        | 626.82        | 397.59        | 5.87          | 103.34        | 
| Telecommunication Services                       | 5.78          | 20.33         | 20.33         | 0.00          | 0.00          | 
| Utilities                                        | 30.50         | 0.00          | 0.00          | 30.50         | 0.00          | 
