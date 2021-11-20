Data analysis:
    - trans:
        - Likely connection between at least a pair in ["type", "operation", "k_symbol"] parameters
            - Should check this connections not only for "trans_train" data but also "trans_test" to see if pattern maintains or if there are new patterns
                - No new patterns would allow for merge of these variables
        - Possible vars extracted from data:
            - income per month (avg)
            - expenses per month (avg)
            - total revenue per month (avg)
            - income in last X months - X needs to be defined 
                - This may not be that useful since even unemployed people can have income, but can be replaced by "revenue in last X months" which complements other vars
            - amount of credit introduced in each transaction (avg)
                - Would allow to see if the person has a steady income or if it is rocky
                - Might not be that useful, need to see if this var will amount to a significant data
                - This var can be changed to not be a simple avg but also relate it to the total income per month
    - loan:
        - Possible vars extracted from data:
            - amount / duration / payments
                - Check if relationships are a constant throughout the data
            - the variables extracted in this table can be further compared with data obtained from the "trans" data
    - card:
        - Identify meaning of each type:
            - data needs to be categorized
    - account:
        - Discover meaning issuance:
            - tax of credit transaction?
            - extract of information?
            - ?
    - client:
        - Extract gender from birth_number variable
            - birth_number format
                - Men: YYMMDD
                - Women: YY(MM+50)DD
        - Use age instead of birth_number as an attribute of model
    - disp:
        - Check meaning of "DISPONENT"
            - "only owner can issue permanent orders and ask for a loan"
                - Do DISPONENT clients have loans for these accounts?
    - district:
        - Possible vars extracted from data:
            - variance in:
                - unemployment rate 
                - crimes committed (in %)
        - Verify correlations between columns
            - Check if no. of municipalities relates to anything
                

Assumptions:
    - household payments are monthly
    - all accounts start with 0 as balance

Data treatment:
    - District:
        - replaced "?" values with region average for unemployment rate and no. committed crimes
    - Trans (both train and test):
        - Aggregated table by sum of "credit" and "withdrawal" (both types included) operations
        - Acquired "Min Date" by checking date of first transaction
        - Final balance will be calculated by subtracting sum of "credit" with sum of "withdrawal"
        - Aggregated household operations by average
            - accounts with NaN values of "household" assumed to not have "household" expenses (0)

Data Analysis Conclusions:


