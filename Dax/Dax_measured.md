COGS = SUMX(Sales_Fact,Sales_Fact[Manufacturing Price]* Sales_Fact[Units Sold])
FV of Total Revenue for a  discount rate 2 % in 10 years = FV(0.02,10,0,-[Total reveue in 2021])
FV of Total Revenue for a  discount rate 5 % = FV(0.05,10,0,-[Total reveue in 2021])
Gross sales Scenario = SUMX('Sales_Fact',(Sales_Fact[Gross Sales])*(1+'Change in sales'[Change in sales  Value]))
Total Net Revenue After Discount = SUM(Sales_Fact[Revenue])-SUM(Sales_Fact[Discount/Premium])
Total Revenue Last Year = CALCULATE([Total Revenue],SAMEPERIODLASTYEAR(Sales_Fact[Order Date]))
Total Revenue = SUMX(Sales_Fact,Sales_Fact[Revenue])  
Calender = CALENDAR(MIN(Sales_Fact[Order Date]),MAX(Sales_Fact[Order Date])+365)
Calender 2 = CALENDAR(MIN(Sales_Fact[Order Date])+4*365,MAX(Sales_Fact[Order Date])+10*365)
Change in sales = GENERATESERIES(-0.05, 0.05, 0.01)
Revenue factor = CALCULATE( SUMX(Sales_Fact,Sales_Fact[Gross Sales]*(1+'Change in sales'[Change in sales  Value])))
Email = 
 VAR commaposition =SEARCH(",",Employees[Name],1,-1)
 VAR NameAfterComma =IF(commaposition=-1,Employees[Name],TRIM(MID(Employees[Name],commaposition+1,LEN(Employees[Name]))))
RETURN NameAfterComma & "@data.com"

Revenue Growth % = DIVIDE([Total Revenue]-[Total Revenue Last Year],[Total Revenue Last Year],0)*100
