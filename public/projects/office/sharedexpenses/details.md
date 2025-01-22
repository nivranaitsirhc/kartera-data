![Shared Expenses Preview](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/preview.png)

# Shared Expenses 
A Spreadsheet for calculating utilities and other expenses with breakdown between multiple tenant/household/individual. <br/>

<h3 style="font-size:3rem"><a alt="Shared Expenses Demo" href="https://docs.google.com/spreadsheets/d/1G4vPJlfiQnKyDakvv3_n3C0w5dtwjeZ9vzos4oEsgQk">Shared Expenses Demo</a></h3>
<em><sup>
Notes:<br/>
- The demo above is active. <br/>
- There might be a subtle differences between what is available here and on the demo above. <br/>
</sup></em>

## Features 
1. ✅ Supports multiple sharing types
    - **Fixed**
    - **Equal Share**
    - **Sub-Metered**
2. ✅ Automatically re-adjust computation based on sharing types.
3. ✅ Each billing month can be adjusted to a different sharing types.
4. ✅ Sub-Meter can calculate even if reading dates are not aligned with the billing reading period.

## Sharing Types 
- **Fixed** <br/>
A fixed amount that an individual will share.
- **Equal Share** <br/>
Equally distribute the remaining balance between individuals using the same sharing type.
- **Sub-Metered** <br/>
<b>The most accurate!</b> <br/>
Uses the billing info properties to calculate the right amount to be shared. <br/>
Uses the sub-meter readings and calculate the proportionate amount versus the main meter. <br/>
In an event that the sub-meter readings dates will not align, Shared Expenses will use the available reading dates near the billing period and generate the appropriate amount.<br/>
<em>Note: To ensure the best accuracy, use the available reading dates within the reading dates of the main meter.</em>

## Shared Expenses Components
- **Overview Sheet** <br/>
A simple dashboard to view the monthly distribution.<br/>
<sup><em>Note: Only added to show an overview of Rent Sheet.</em></sup>
- **Rent Sheet** <br/>
A custom Sheet to show the breakdown of utilities deductable to the payable rent. <br/>
<sup><em>Note: Only added to calculate the rent of House A less the utilities of the other households to the Landlord.</em></sup>

- **Bill Records Sheet** <br/>
Stores all the information regarding the bill, payment info, and sharing allotment. <br/>
  * <strong>Billing Records</strong> <br/>
  Properties regarding the bill. It should show the billing dates, reading data, amount, overdue amount. <br/>
  ![Billing Info](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/billing-info.png)<br/>

  * <strong>Bill Payment Info</strong> <br/>
  Status of payment info and other relevant information. The <strong>Overdue</strong> column will affect the calculation of other sheets, it is important that this data is accurate by supplying the relevant data to payment dates. <br/>
  ![Payment Info](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/payment-info.png)<br/>

  * <strong>Bill Allotment</strong> <br/>
  Shows the breakdown of the bill amount with respect to each individual sharing type configuration. <br/>
  ![Bill Allotment](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/bill-allotment.png)<br/>

  * <strong>Verification</strong> <br/>
  Verifies the breakdown if it aligns with the bill amount.<br/>
  <b style="color:green;">✅ PASSED</b> will show if the total allotment matches the bill amount.<br/>
  <b style="color:red;">❌ INCONSISTENT</b> will show if the total allotment does not match the bill amount.<br/>
  ![Verification](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/verification.png)<br/>

- **Individuals Record Sheet** <br/>
Configures all the relevant data for a particular tenant/household/individual.
  * <strong>Billing Records & Bill Payment Info</strong> <br/>
  Has the same data with the <strong>Bill Records Sheet</strong>. All changes from there will also be reflected here. <br/>
  * <strong>Contribution</strong> <br/>
  Where the sharing type is selected. <br/>
  <em>Note: Selecting a <b>Sharing Type</b> will use the relavant amount from either <b>Option - Non Metered</b> or <b>Option - Metered (Sub Meter)/Sub Meter Adjustment</b></em> <br/>
  ![Contribution](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/contribution.png)<br/>

  * <strong>Option - Non-Metered</strong> <br/>
  Where you set the amount if <b>Fixed</b> sharing type is used. <br/>
  This is also where the Equal Sharing computation are displayed. <br/>
  ![Non-Metered](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/non-metered.png)<br/>
  <strong>How does it work?</strong> <br/>
    - <strong>Fixed</strong> <br/> 
    Fixed will use the value defined in ``(Fixed) Amount``. <br/>
    - <strong>Equal Share</strong> <br/> 
    Equal Share will use the value defined in ``(Equal Share) Individual Amount``. <br/>
    This value is computed from getting the total amount of non-sharing types and dividing this value the total sharing types. <br/>
    <b>Example:</b> <br/>
      - For the billing period of ``2024-Dec`` we have a total bill amount of ``2485.71``, ``1`` total of no. of Sharing Type, ``1`` total no. of Non-Sharing Type, and a total amount of ``700`` for the Non-Sharing Type. <br/>
      - Subtracting the total bill amount by the total amount of the non-sharing we get ``1785.71 = 2485.71 - 700`` to be shared equally by the sharing types. <br/>
      - Dividing this ``1785.71`` to the no. sharing type, we can get the individual share amount of ``1785.71 = 1785.71 / 1``. <br/>
    <em>Note: Since we only have two tenant/household/individuals in this example the sole sharing individual will get the difference from the Fixed individual. </em> <br/><br/>

  * <strong>Option - Metered (Sub-Meter)</strong> <br/>
  This is where you set the relevant data if you are using the Sub-Meter Sharing Type. <br/>
  <em>Note: The specific Sub-Meter sheet for this particular individual must be present/linked, and contains the relevant sub-meter reading.</em> <br/>
  ![Metered](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/metered.png)<br/>
    * <strong>Aligned</strong> <br/>
    Select <b>YES</b> or <b>No</b> whethere the reading dates exactly matches the reading dates for the sub-meter. <br/>
    Yes means an exact match, No means otherwise. <br/>
    * <strong>Reading From</strong> <br/>
    Select the date for the start reading date. <br/>
    * <strong>Reading To</strong> <br/>
    Select the date for the end reading date. <br/>

  * <strong>Sub Meter Adjustment</strong> <br/>
  Where the sub-meter is re-calculated and adjusted to match the actual sub-meter reading. <br/>
  This part will be populated when <strong>Aligned</strong> is set to <strong>No</strong> and all the relevant data is present in <strong>Option - Metered (Sub-Meter)</strong> <br/>
  ![Sub-Meter Adjustment](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/sub-meter-adjustment.png)![Metered](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/metered.png) <br/>
  <strong>How does it work?</strong> <br/>
    1. It works by getting the daily avarage consumption from the available used ```KW/H``` or <code>m<sup>3</sup></code> data from <strong>Option - Metered (Sub-Meter)</strong>. <br/>
    2. Once a daily average is available, multiply it to the total reading days of the billing period. <br/>
    <b>Example:</b> <br/>
       - For billing period ``2024-Dec`` we have a ``29 days`` of reading period, and a sub-meter reading of ``141 KW/H`` with ``31 days`` of reading period. <br/>
       - Dividing ```141``` by ```31 days``` we get an average of ```4.55 KW/H``` daily consumption for the sub-meter. <br/>
       - Multiplying ```4.55 KW/H per Day``` to the no. reading period of  ```29 days```, our new adjusted KW/H will be ```131.95 KW/H = 4.55 KW/H/days x 29 days```. <br/>
       - In summary we adjusted the ```31 days``` of ```141 KW/H``` to ```29 days``` with ```131.95 KW/H``` to match the ```29 days``` reading period of the main meter. <br/>
       <em>Note: To get an accurate average, the reading dates must be not less than 50% of the reading days and must atleast be near the billing period of the main meter.</em> <br/><br/>

- **Sub-Meter Reading Sheet** <br/>
Contains all the sub-meter reading values and corresponding date for a specific tenant/household/individual. <br/>
![Sub Meter Reading Sheet](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/sub-meter-reading.png)
