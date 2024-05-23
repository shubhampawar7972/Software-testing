def next_date(day, month, year):
    if day < 1 or day > 31 or month < 1 or month > 12 or year < 1812 or year > 9999:
        return "Invalid input"
    if month in [1,3,5,7,8,10]:
        if day < 31:
            return day + 1, month, year
        else:
            return 1, month + 1, year
    elif month in [4,6,9,11]:
        if day < 30:
            return day + 1, month + 1, year
        else:
            return 1, month + 1, year
    elif month ==2:
        if (year % 400 == 0) or (year % 4 == 0 and year %100 != 0):
            if day < 29:
                return day + 1, month, year
            else:
                return 1, month + 1,year
        else:
             if day < 28:
                return day + 1, month, year
             else:
                return 1, month + 1,year
    elif month == 12:
        if day < 31:
            return day + 1, month, year
        else:
            return 1, 1, year + 1
    else:
        return "Invalid input"
test_cases = [
    
    (1, 1, 2022),
    (31, 1, 2022),
    (28, 2, 2022),
    (28, 2, 2020),
    (30, 4, 2022),
    (31, 12, 2022),   
    (15, 8, 2022),
    (15, 10, 1812),
    (15, 10, 9999),
    
    
    (0, 1, 2022),
    (32, 1, 2022),
    (15, 0, 2022),
    (15, 13, 2022),
    (29, 2, 2021),
    (30, 2, 2020),
    (31, 4, 2022),
    (31, 6, 2022),
    (31, 9, 2022),
    (31, 11, 2022),
    (15, 8, 1811),
    (15, 8, 10000),
            
]
for test_case in test_cases:
    day , month, year = test_case
    result = next_date(day, month, year)  
    print (f"Input: {test_case} - output: {result}")
