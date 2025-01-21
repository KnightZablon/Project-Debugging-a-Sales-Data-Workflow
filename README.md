# Project-Debugging-a-Sales-Data-Workflow

In this project, I was tasked with troubleshooting and fixing a sales data pipeline that encountered issues after a recent update. The pipeline, managed by the load_and_check() function, is designed to load a sales dataset from a CSV file, perform several integrity checks, and ensure the data is accurate before further processing. These checks focus on critical fields like Total, Quantity, Unit Price, Tax, and Date, ensuring that the data is both consistent and correct.

Steps I Took:
Loading the Data: The first thing I did was load the sales data from the sales.csv file into a Pandas DataFrame. The pipeline had a step where it checked if the dataset had the expected number of columns, but after the update, the number of columns might have changed. I had to adjust the column check to ensure that the data loaded correctly.

Integrity Checks: After loading the data, I moved on to the integrity checks. The pipeline needed to calculate some statistical values—like the mean and standard deviation of Total sales for each Date—and use these to establish thresholds for valid Total values. This helped me flag any outliers in the data, such as sales amounts that were too high or too low compared to the normal range.

Recalculating Tax: One of the key issues was the Tax column. The tax should be 5% of the Subtotal, which is the product of Quantity and Unit Price. I noticed that the tax was not being calculated correctly due to the update, so I fixed this by recalculating the Tax for each row using the correct formula: Quantity * Unit Price * 0.05. I also ensured that the tax values were rounded consistently to avoid any minor floating-point discrepancies.

Condition Checks: To further ensure the integrity of the data, I implemented two condition checks:

Condition_1: This checks if the Total for each row is within an acceptable range, based on the calculated mean and standard deviation for each date.
Condition_2: This checks if the Tax value is correctly calculated as 5% of the Subtotal.
These checks help me identify whether any rows deviate from expected values, ensuring data consistency across the dataset.

Final Check and Result: The final step involved evaluating whether all rows in the dataset passed both conditions. If all rows passed the checks, the pipeline would print a success message confirming that the data integrity was intact. If any rows failed, an error message would be displayed, alerting me to potential issues that needed further investigation.

Outcome:
At the end of the process, I was able to confirm whether the sales data was clean and accurate. If everything passed, I could be confident that the data integrity was intact and ready for further analysis. If there were any issues, I would have identified which rows were problematic and could address them accordingly. This helped ensure that the data pipeline continued to work smoothly, even after the update, and that only reliable data was used for analysis.
