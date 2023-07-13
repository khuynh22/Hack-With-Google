# Device Performance Monitoring

### 1. Introduction:
Attending Hack With Google event, sponsored by BeMyApp, Google, and Onix, the hackathon aims to expand people's knowledge about AppSheet and other generative AI features in Google Workspace, AppSheet, and Google Cloud products.

There are two main challenges: the Independent Developer track and the Emerging Mid-Market Track, with the focus theme being **Manufacturing**

<img width="869" alt="Screenshot 2023-07-13 at 17 57 16" src="https://github.com/khuynh22/Hack-With-Google/assets/57774658/52633ea6-729e-47e2-a593-5c78f1e1ef84">

Our team chose the idea of developing a Device Performance Monitoring application (track 1). We end up winning 1st place with a $5,000 prize from Google.


### 2. Ideas:
Our project leverages the power of AppSheet to create a comprehensive device performance monitoring system. It enables companies and electricians to track the status of meters and transformers in the field, allowing them to report artificial outages, non-technical losses, errors, and warnings. By implementing features such as views, dashboards, graphs, and actions, along with integrating Google Maps, OCR, and Automatic Bots, our project aims to streamline operations, optimize the budget, and maximize the performance of utility companies. Additionally, it seeks to contribute to energy conservation efforts by monitoring and reducing energy consumption. This solution has the potential to save 30% of the workload for over a million electricians across the United States.

Our solution will benefit the following stakeholders with significant impacts:

&nbsp; &nbsp; &nbsp; &nbsp; Devices Manufacturing Companies: By implementing our product during device testing, manufacturing companies can achieve substantial benefits. With real-time performance analysis and status tracking, they can make instant adjustments and optimizations, resulting in a reduction of testing time by up to 25% and cost savings of approximately 15% on average. The ability to quickly identify and resolve issues during the manufacturing process leads to improved device quality and customer satisfaction.

&nbsp; &nbsp; &nbsp; &nbsp; Utilities Companies / Electricity Provider Companies: Our solution offers utility companies the ability to efficiently monitor the performance of their installed devices, such as meters, transformers, and circuits. This proactive monitoring approach leads to a reduction in downtime and maintenance costs. By utilizing our product, utility companies can decrease outage durations by up to 20%, resulting in improved service reliability for their customers.

&nbsp; &nbsp; &nbsp; &nbsp; Electricians: Electricians will greatly benefit from our product's features. By instantly filling in required information into the audit log using OCR technology, they can save an average of 30 minutes per inspection, allowing them to focus on critical tasks. This time savings translates to increased productivity of electricians by approximately 15%, enabling them to handle more inspections and service requests efficiently.

### 3. Implementations:
The project focuses on using Google Products (G-Suite, AppSheets, etc.) where the main interface is developed using AppSheet and the data is simulated in Google Sheet.

This is the mobile view version of the application:

![Screenshot 2023-07-13 at 18 28 49](https://github.com/khuynh22/Hack-With-Google/assets/57774658/bcceae53-1079-4487-a2da-dac9501f9bff)

#### a) Overview
- This is the landing page, which shows useful information about their devices (Average Power, Number of Active Meters, Number of Errors/Warnings, Number of Power Outages during the last 24 hours)
- The user can click on each card to view more information about that

#### b) Map
![Screenshot 2023-07-13 at 18 42 18](https://github.com/khuynh22/Hack-With-Google/assets/57774658/a5a6d199-0c9e-436b-bb22-b0dbdb8f75ea)

The Map Tabs integrated Google Maps API to display the location and the status of the meters, where the green pin means the meter is working well, the yellow pin means the meter is not in a warning situation that needs to be checked and the red pin means the meter is down or broken. The purpose of this is for both the electricians' end and the company's end to respond to changes in meters' status as fast as possible.

When you click on the pin, you can also edit the information and status, as well as view who last come there to check/fix or any specific notes.

![Screenshot 2023-07-13 at 18 53 56](https://github.com/khuynh22/Hack-With-Google/assets/57774658/49f02609-3f78-4753-9059-83f6b98bc907) ![Screenshot 2023-07-13 at 18 54 30](https://github.com/khuynh22/Hack-With-Google/assets/57774658/b19576ab-7d46-4387-9877-35a4ef6b6d34)




