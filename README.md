# Employee Sentiment Analysis Hub

This repository documents a no-code project that leverages Microsoft’s ecosystem to capture employee feedback, analyze sentiment using Azure Cognitive Services, and display insights via a Power BI dashboard.

> **Note:** This version focuses only on employee feedback. The Employee Recognition list is not part of this project.

---

## Table of Contents

- Project Overview
- Prerequisites
- Step 1: Set Up SharePoint List
- Step 2: Build a No-Code Form with Power Apps
- Step 3: Automate Sentiment Analysis with Power Automate
  - 3.1: Create the Flow
  - 3.2: Integrate Azure Cognitive Services (Sentiment V4)
  - 3.3: Update the SharePoint Item with Results
- Step 4: Develop a Visual Dashboard with Power BI
- Testing
- Next Steps and Enhancements

---

## Project Overview

The Employee Sentiment Analysis Hub is a no-code solution that:

- **Provides a No-Code Form** using Power Apps for users to submit their feedback.
- **Stores Employee Feedback** in a SharePoint list.
- **Automates Sentiment Analysis** using Power Automate combined with Azure Cognitive Services (Sentiment V4).
- **Visualizes Insights** through interactive Power BI dashboards.

This project allows organizations to monitor employee sentiment and gather actionable insights.

---

## Prerequisites

- A Microsoft 365 account with access to SharePoint, Power Apps, Power Automate, and Power BI.
- An Azure Cognitive Services resource with access to the Language service (for Sentiment Analysis).
- Basic familiarity with using the Microsoft Power Platform.

---

## Step 1: Set Up SharePoint List

### Create the "Employee Feedback" List

1. **List Name:** Employee Feedback

2. **Create/Configure the following columns:**

   | Column Name      | Type                  | Description                                                            |
   | ---------------- | --------------------- | -----------------------------------------------------------------------|
   | Employee Name    | Single line of text   | Capture the name of the employee giving feedback.                      |
   | Feedback Text    | Multiple lines of text| The content of the feedback.                                           |
   | Submission Date  | Date and Time         | The date/time when the feedback is submitted. (Optional)               |
   | Positive Sentiment Score  | Number       | To be updated with the sentiment analysis (confidenceScores/positive). |
   | Negative Sentiment Score  | Number       | To be updated with the sentiment analysis (confidenceScores/negative). |
   | Neutral Sentiment Score   | Number       | To be updated with the sentiment analysis (confidenceScores/neutral).  |
   | Key Phrases      | Multiple lines of text| To be populated with key phrases extracted from the feedback.          |
   

> **Tip:** Although SharePoint automatically tracks metadata like "Created" and "Created By," having dedicated fields ensures consistency when integrating with Power Automate and Power BI.

---

## Step 2: Build a No-Code Form with Power Apps

1. **Access Power Apps:**
   - Go to [Power Apps](https://make.powerapps.com) and sign in with your Microsoft 365 credentials.
   - Create a new Canvas app from blank (choose Phone or Tablet layout as needed).

2. **Connect the Data Source:**
3. **Design the Feedback Form:**
   - Exclude the **Sentiment Score** and **Key Phrases** fields because they will be updated automatically.
4. **Add and Configure the Submit Button:**
5. **Test and Publish:**
   - Submit test entries and verify they appear in SharePoint.
   - Save and publish the app. You may also embed it in your SharePoint site using the Power Apps web part.

---

## Step 3: Automate Sentiment Analysis with Power Automate

### 3.1: Create the Flow

1. **Access Power Automate:**
   - Go to [Power Automate](https://flow.microsoft.com) and sign in.
2. **Create an Automated Cloud Flow:**
3. **Configure the Trigger:**
   
### 3.2: Integrate Azure Cognitive Services (Sentiment V4)

1. **Add the Sentiment Analysis Action:**   
2. **Configure the Connection:**
3. **Map the Input:**
   - Map the text input using the dynamic content of **Feedback Text** from your SharePoint trigger. it.

### 3.3: Update the SharePoint Item with Results

1. **Add the "Update item" Action:**
2. **Configure the Update:**
   - **Site Address:** Use the same SharePoint site as before.
   - **List Name:** Select **Employee Feedback**.
   - **Id:** Use the dynamic content **ID** from the trigger.
   - **Sentiment Score:** Map this to `confidenceScores/positive` from the Sentiment (V4) action.
   - **Key Phrases:** Map this to the key phrases output.

3. **Save and Test the Flow:**
   - Save your flow.
   - Test by submitting a new feedback entry via your Power Apps form.
   - Verify in your SharePoint list that the **Sentiment Score** and **Key Phrases** fields are updated correctly.

---

## Step 4: Develop a Visual Dashboard with Power BI

1. Open Power BI Desktop:
2. Connect to SharePoint Data:
3. Build and Customize Visualizations:
4. Publish the Report:
   
---

## Testing

- **Positive Test:**  
  Use a sample feedback like:  
  > "I had an excellent experience with the new system update. The interface is intuitive and responsive, making my daily tasks much easier."

- **Mixed Test:**  
  Use a sample feedback like:  
  > "The new system design is user-friendly and modern, but some features are unresponsive and error messages appear frequently."

Submit these test entries through your Power Apps form and verify that:
- The Power Automate flow triggers correctly.
- The SharePoint list gets updated with the corresponding sentiment scores and key phrases.
- Your Power BI dashboard refreshes to reflect the new data.

---

## Next Steps and Enhancements

- **Employee Recognition:**  
  In future iterations, consider adding an Employee Recognition list and corresponding app if the project’s scope expands.

- **Additional Metrics:**  
  You can expand the Power Automate flow to store details like neutral and negative sentiment scores in separate columns for more nuanced analysis.

- **User Feedback:**  
  Before finalizing, gather user feedback to further refine the forms, flows, and dashboard visuals.

- **Advanced Analytics:**  
  Experiment with more features from Azure Cognitive Services or Power BI to further enhance insights.

---

This project offers a scalable, no-code solution to monitor employee sentiment and derive actionable insights. Enjoy building and iterating on your Employee Sentiment Analysis Hub!

