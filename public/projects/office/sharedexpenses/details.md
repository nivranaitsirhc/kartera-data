![Shared Expenses Preview](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/preview.png)

# Shared Expenses 
A Spreadsheet for calculating utilities and other expenses with breakdown between multiple tenant/household/individual. <br/>

<h3><a alt="Shared Expenses Demo" href="https://docs.google.com/spreadsheets/d/1G4vPJlfiQnKyDakvv3_n3C0w5dtwjeZ9vzos4oEsgQk">Shared Expenses Demo</a></h3>
<em>Notes:<br/>
- There might be a slight modification from what is available here. <br/>
- This is a live demonstration and is actively used.</em><br/>

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

## Shared Expenses Parts
- **Bill Records Sheet** <br/>
Stores all the information regarding the bill, payment info, and sharing allotment. <br/>
  * <strong>Billing Records</strong> <br/>
  Properties regaring the bill. It should show the billing dates, reading data, amount, overdue amount. <br/>
  ![Billing Info](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/billing-info.png)<br/>

  * <strong>Bill Payment Info</strong> <br/>
  Status of payment info and other relevant information. The <strong>Overdue</strong> column will affect the calculation of other sheets, it is important that this data is accurate by supplying the relevant data to payment dates. <br/>
  ![Payment Info](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/payment-info.png)<br/>

  * <strong>Bill Allotment</strong> <br/>
  Shows the breakdown of the bill amount with respect to each individuals individual sharing type configuration. <br/>
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
  ![Sub-Meter Adjustment](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/sub-meter-adjustment.png)<br/>
  <strong>How does it work?</strong> <br/>
    1. It works by getting the daily avarage consumption from the available used ```KW/H``` or <code>m<sup>3</sup></code> data from <strong>Option - Metered (Sub-Meter)</strong>. <br/>
    2. Once a daily average is available, multiply it to the total reading days of the billing period. <br/>
    - <em>Note: To get an accurate average, the reading dates must be not less than 50% of the reading days and must atleast be near the billing period of the main meter.</em> <br/>

- **Sub-Meter Reading Sheet** <br/>
Contains all the sub-meter reading values and corresponding date for a specific tenant/household/individual. <br/>
![Sub Meter Reading Sheet](https://raw.githubusercontent.com/nivranaitsirhc/kartera-data/refs/heads/master/public/projects/office/sharedexpenses/details/sub-meter-reading.png)
