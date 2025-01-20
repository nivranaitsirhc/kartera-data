![Shared Expenses Preview](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/preview.png)

# Shared Expenses 
A Spreadsheet for calculating utilities and other expenses with breakdown between multiple household/parties. <br/>

## Features 
1. Supports multiple sharing types
    - **Fixed**
    - **Equal Share**
    - **Sub-Metered**
2. Automatically re-adjust computation based on sharing types.
3. Each billing month can be adjusted to a different sharing types.
4. Sub-Meter can calculate even if reading dates are not aligned with the billing reading dates.

## Sharing Types 
- **Fixed** <br/>
This will force an amount regardless of what sharing type the other parties will use.
- **Equal Share** <br/>
This will distribute the remaining balance between parties using this sharing type.
- **Sub-Metered** <br/>
The most accurate. This will use the billing info properties to calculate the right amount to be shared. <br/>
This will use the sub-meter readings and calculate the proportionate amount versus the main meter. <br/>
In an event that the sub-meter readings dates will not align, Shared Expenses will use what available reading dates are available <br/>
to get the average daily and use it to generate the appropriate amount.<br/>
Note: To ensure the best accuracy, use the available reading dates within the reading dates of the main meter.

