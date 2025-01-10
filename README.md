# Online Advertising Platform

This repository contains the implementation of an Online Advertising Platform designed to facilitate the management of ad campaigns, ad display mechanisms, feedback collection, and billing report generation.

## System Components

### Campaign Manager Interface
The Campaign Manager Interface enables campaign managers to start and stop ad campaigns by sending ad-related instructions to a Kafka message queue.

### Ad Manager
The Ad Manager is responsible for processing messages from the Kafka queue, updating the MySQL database accordingly, and overseeing the entire ad campaign lifecycle.

### Ad Server
The Ad Server conducts auctions to determine which ads get displayed on user devices. The winner is determined based on bids, and the second-highest bid amount is charged.

### User Simulator
The User Simulator interacts with the Ad Server API to request and display ads, mimicking user engagement.

### Feedback Handler
The Feedback Handler collects user interaction data from the User Simulator, publishes it to another Kafka queue, and updates the ad campaign’s remaining budget in MySQL.

### User Feedback Writer
The User Feedback Writer retrieves feedback events from Kafka and stores them in HIVE for billing and long-term archiving.

### Report Generator
The Report Generator compiles billing reports based on ad displays throughout the system’s operational period.

## Technologies Used

- **Kafka**: Facilitates event-driven communication between system components.
- **MySQL**: Manages ad campaign data and maintains updates from various interactions.
- **HIVE**: Serves as a storage and archival system for user feedback data, supporting billing processes.
- **APIs**: Enable seamless interaction between different system components (e.g., Campaign Manager Interface, Ad Server API, Feedback API).

## Challenges Encountered

### 1. Component Integration
Ensuring smooth interaction among different modules required detailed planning and coordination to prevent inconsistencies.

### 2. Real-Time Data Processing
Efficient handling of real-time ad requests, user feedback, and campaign budget updates in MySQL demanded optimized data processing techniques.

### 3. Scalability & Performance
The system needed to support a high volume of ad requests, feedback events, and database operations without compromising performance.

### 4. Billing & Reporting Accuracy
Developing an accurate billing and reporting mechanism based on auction results and user interactions required careful computation and validation.

Overcoming these challenges involved rigorous testing, optimization techniques, and continuous monitoring to enhance reliability and efficiency.

## Conclusion

This Online Advertising Platform offers a structured approach to managing ad campaigns, handling real-time bidding, collecting user interaction data, and generating financial reports. By integrating key technologies and components, it ensures seamless ad management and analytics for an effective advertising ecosystem.
