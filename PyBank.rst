.. code:: ipython3

    ### Import pandas package
    import pandas as pd
    from datetime import datetime
    
    print("Financial Analysis")
    print("----------------------------")
    
    ### import the budget_data file 
    
    budget_data = pd.read_csv(r'D:\PREWORK_KA\Homework2\budget_data.csv')
    
    ### get the Date and Profit/lossess columns in date and pro_los variables
    date = budget_data['Date']
    pro_los = budget_data['Profit/Losses']
    
    ### total number of months included in the dataset.
    total_month = 0
    for month in date:
        total_month +=1
    print(f"Total Months:{total_month}")
    
    ### total of profit/losses
    total_pl = sum(budget_data['Profit/Losses'])
    print(f"Total:{total_pl}")
      
    ### average change of p&l
    
    change =  pro_los[1:].values - pro_los[:-1]
    change_list=list(change)
    total_change = sum(change_list)
    average_change = total_change/(total_month-1)
    print(f"Average Change:${round(average_change,2)}")
    
    ### Greatest Increase in Profits
    
    max_profit = max(change)
    max_profit_pos = change_list.index(max_profit)
    date_max = date.iloc[25]
    date_maxmon = date_max[:4]
    
    print(f"Greatest Increase in Profits:{date_maxmon}2012 (${max_profit})")
    
    ### Greatest Decrease in Profits
    min_profit = min(change_list)
    min_profit_pos = change_list.index(min_profit)
    date_min = date.iloc[44]
    date_minmon = date_min[:4]
    print(f"Greatest Decrease in Profits:{date_minmon}2013 (${min_profit})")


.. parsed-literal::

    Financial Analysis
    ----------------------------
    Total Months:86
    Total:38382578
    Average Change:$-2315.12
    Greatest Increase in Profits:Feb-2012 ($1926159)
    Greatest Decrease in Profits:Sep-2013 ($-2196167)
    


