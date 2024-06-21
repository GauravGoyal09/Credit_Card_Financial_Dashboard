Power BI Dashboard

Project Objective -> To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends and analyze credit card operations effectively.

Prepare CSV files ---> Create tables in SQL ---> Import csv file into SQL.

DAX Quaries -->  

                IncomeGroup = AgeGroup = SWITCH(
                                                TRUE(),
                                                customer[Customer_Age]<30, "Less than 30", 
                                                customer[Customer_Age]>=30 && customer[Customer_Age]<40, "30-40",
                                                customer[Customer_Age]>=40 && customer[Customer_Age]<50, "40-50",
                                                customer[Customer_Age]>=50 && customer[Customer_Age]<60, "50-60",
                                                customer[Customer_Age]>=60, "60+",
                                                "unknown")
                                                
                Current_Week_revenue = CALCULATE(
                                                SUM(credit_card[Revenue]),
                                                FILTER(ALL(credit_card), credit_card[WeekNo] = MAX(credit_card[WeekNo])))
                                                
                Previous_Week_revenue = CALCULATE(
                                                SUM(credit_card[Revenue]),
                                                FILTER(ALL(credit_card),
                                                credit_card[WeekNo]=MAX(credit_card[WeekNo])-1))
