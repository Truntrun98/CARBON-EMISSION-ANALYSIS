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
