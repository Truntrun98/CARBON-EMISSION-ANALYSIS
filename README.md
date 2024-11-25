# CARBON-EMISSION-ANALYSIS
This project is aim to analize the level of carbon emission based on industry fields, countries, time and more...


## The top 10 products contributing the most to the carbon emission:
### CODE to findout:
```sql
SELECT product_name, ROUND(AVG(carbon_footprint_pcf),2) 
FROM product_emissions 
GROUP BY product_name 
ORDER BY ROUND(AVG(carbon_footprint_pcf),2) DESC
LIMIT 10;
```
### Explanation: 

### Result
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
