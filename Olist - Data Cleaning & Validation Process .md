# Data Cleaning Process

The following steps and concepts are used in order to validate and clean the Olist data :

1. **Database Selection**
   The code begins by selecting the desired database using the `USE` statement. This ensures that all subsequent operations are performed on the correct dataset.

2. **Temporary Table Creation**  
   A temporary table is created using the `CREATE TABLE` statement with the same structure as the original table. This allows for data cleaning without altering the original dataset.

3. **Data Insertion**  
   All records from the original table are inserted into the temporary table using the `INSERT INTO` statement. This creates a copy of the data for processing.

4. **Data Verification**  
   The code selects all records from the temporary table using `SELECT * FROM temp_table` to verify the data has been copied correctly.

5. **Schema Understanding**  
   The `DESCRIBE` statement is used to understand the schema of the temporary table, providing insight into the data types and structure of the columns.

6. **Data Type Adjustment**  
   The code modifies the data types of specific columns using the `ALTER TABLE` statement to ensure they are appropriate for the data.

7. **Missing Value Handling**  
   The code identifies missing values for key fields using the `SELECT` statement with conditional aggregation (`SUM` and `IF`). It counts the total records and the number of null or empty values for each relevant column.

8. **Duplicate Identification**  
   The code checks for potential duplicates based on key fields using the `SELECT` statement with `GROUP BY` and `HAVING`. It groups the records by the relevant columns and counts the number of occurrences for each combination. The `HAVING` clause filters out groups with a count greater than 1, indicating potential duplicates.

9. **Data Standardization**  
   The code selects all records from the temporary table using `SELECT * FROM temp_table` to review the data. It then updates specific columns using the `UPDATE` statement to ensure consistent formatting or capitalization. Functions like `CONCAT` can be used to manipulate the data as needed.

10. **Transaction Commit**  
    The `COMMIT` statement is used to ensure all changes made to the temporary table are saved.

11. **Original Table Truncation**  
    The original table is truncated using the `TRUNCATE` statement to prepare for the insertion of cleaned data.

12. **Cleaned Data Insertion**  
    The cleaned data from the temporary table is inserted into the original table using the `INSERT INTO` statement. This replaces the original data with the validated and cleaned version.

## MySQL Concepts Used

- `USE` statement: Used to select the database for the cleaning process.
- `CREATE TABLE`: Used to create a temporary table with the same structure as the original table.
- `INSERT INTO`: Used to copy data from the original table into the temporary table.
- `SELECT`: Used for various purposes:
  - Verifying the data in the temporary table
  - Understanding the schema of the temporary table
  - Identifying missing values and potential duplicates
- `ALTER TABLE`: Used to modify the data types of specific columns in the temporary table.
- `SUM` and `IF`: Used in combination with `SELECT` for conditional aggregation to identify missing values.
- `GROUP BY` and `HAVING`: Used with `SELECT` to identify potential duplicates based on key fields.
- `UPDATE`: Used to standardize the data by updating specific columns.
- Functions like `CONCAT`: Used within the `UPDATE` statement to manipulate data as needed.
- `COMMIT`: Used to save the changes made to the temporary table.
- `TRUNCATE`: Used to remove all data from the original table.
- `INSERT INTO`: Used to insert the cleaned data from the temporary table into the original table.
