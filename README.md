# Device Performance Monitoring

### 1. Introduction:
Attending Hack With Google event, sponsored by BeMyApp, Google, and Onix, the hackathon aims to expand people's knowledge about AppSheet and other generative AI features in Google Workspace, AppSheet, and Google Cloud products.

There are two main challenges: the Independent Developer track and the Emerging Mid-Market Track, with the focus theme being **Manufacturing**

<img width="869" alt="Screenshot 2023-07-13 at 17 57 16" src="https://github.com/khuynh22/Hack-With-Google/assets/57774658/52633ea6-729e-47e2-a593-5c78f1e1ef84">

Our team chose the idea of developing a Device Performance Monitoring application (track 1). We end up winning 1st place with a $5,000 prize from Google.
Here is the link to the event: https://googleworkspace-hackathon.bemyapp.com/?utm_source=bma&utm_medium=1to1&leadid=%7B%7Blead_id%7D%7D

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

#### c) Audit Log
![Screenshot 2023-07-13 at 18 55 32](https://github.com/khuynh22/Hack-With-Google/assets/57774658/3a3ec58f-dcbf-4dc7-9e6f-1ab45b86c59e)

The purpose of this is to reduce the physical paperwork for electricians since after checking or changing any information, they can directly modify and submit the form using this application.

Besides that, we integrated autofill, which is very time-efficient, given the fact that the electricians usually have to work with thousands of meters.

We also incorporate the use of OCR, where when the electrician takes a picture, it automatically reads and fills out as much information as it could on the form. In this way, the electrician just has to check, sign, and submit. This will both saves a lot of time and reduces human errors.

#### d) Performance Chart
![Screenshot 2023-07-13 at 19 25 25](https://github.com/khuynh22/Hack-With-Google/assets/57774658/0362d34b-3dda-4a35-be61-dec0c8195894)

This integrated the data from Google Sheets to build and displays the charts about overall information that is needed for the company. The chart can be filtered in datetime and specific device ID.

#### e) Automated Bots
![Screenshot 2023-07-13 at 19 28 09](https://github.com/khuynh22/Hack-With-Google/assets/57774658/1ee0c569-a679-41c1-a5a7-dd98c5627821)

In the event of any device change from Green Status to Yellow and Red status, the automatic Bots are trained to send the email with specific contents to the electricians. 

This helps companies and businesses save a lot of money and energy with a fast response system that automatedly done.

### 4. Next Steps:

We tried to develop the product into a fully functional with full features and pitch the ideas to companies that want this solution. The features we want to implement deeper including:
- Outage and Billing reports
- User interactive maps: a) When you click on implanted devices, it leads you to connected devices and provides metrics related to them. b) Technicians can go to the exact geo-locations to work on the devices.
- New devices like solar panels to reduce energy consumption.
- Interconnected dynamic charts
- Train the OCR so that it can read even more data from the meter. (Right now, it just read in voltage and power)

### 5. Experience App Sources:
Due to the limitation of AppSheet, it is not possible to share the sources coding and app implementing files here. To experience the usage of the app right now, please follow these steps:

1. Create an AppSheet account.
2. Access this link: https://www.appsheet.com/start/23ffc642-1353-4874-ac16-c94ab17b59ba.
3. The related pseudo-simulated data can be found in this GitHub repo.

Want to collaborate to develop more this product, please email me at timhuynhwork@gmail.com

### 6. Acknowledgment:
I want to give special thanks to Hayden and the Google team, Lucas and the BeMyApp team, and Solange Jacob and the whole Onix team for their special help in mentoring and holding the event. It has been a great opportunity to learn for me.

I want to give special thanks to the Power Ranger team who work really well with me for the completion of the project. 

### 7. Licenses:
The project is possessed by Khang Nguyen Huynh. Please do not copy or duplicate in any form without permission.
