# Online-Advertising-Platform

This repository contains the implementation of an Online-Advertising-Platform, which consists of various components for managing ad campaigns, displaying ads to users, collecting feedback, and generating bill reports.

## Components

### Campaign Manager Interface
The Campaign Manager Interface allows campaign managers to run and stop ad campaigns by publishing ad instructions to a Kafka queue.

### Ad Manager
The Ad Manager component reads messages from the Kafka queue, updates the MySQL store accordingly, and manages the overall ad campaign lifecycle.

### Ad Server
The Ad Server holds the auction for displaying ads to user devices. It determines the winning ad and charges the second-highest bid amount.

### User Simulator
The User Simulator component hits the Ad Server API to request and display ads, simulating user interactions.

### Feedback Handler
The Feedback Handler receives user interaction feedback from the User Simulator and publishes it to another Kafka queue. It also updates the leftover budget for the ad campaign in MySQL.

### User Feedback Writer
The User Feedback Writer component reads feedback events from the Kafka queue and writes them to HIVE for billing and archiving purposes.

### Report Generator
The Report Generator generates a bill report for all ads displayed during the system's runtime.

## Tools Used

- Kafka: Used for message queuing and event-driven communication between components.
- MySQL: Stores ad campaign data and updates the database based on instructions received.
- HIVE: Used for storing and archiving user feedback events for billing purposes.
- API: Provides interfaces for communication between components (e.g., Campaign Manager Interface, Ad Server API, Feedback API).

## Difficulties Faced

During the implementation of this Ad Campaign Management System, we encountered several challenges, including:

1. Integration Complexity: Integrating multiple components and ensuring seamless communication between them required careful planning and coordination.
2. Real-time Data Processing: Handling real-time ad requests, feedback collection, and updates to the campaign budget in MySQL required efficient data processing and synchronization.
3. Scalability and Performance: Ensuring that the system can handle a high volume of ad requests, feedback events, and database updates while maintaining performance and responsiveness was a significant challenge.
4. Billing and Reporting: Designing the billing and reporting functionality to accurately calculate costs based on ad auctions and user interactions required careful consideration of various factors.

Overcoming these difficulties involved thorough testing, performance optimization, and continuous monitoring to ensure the system's reliability and effectiveness.

## Conclusion

The Ad Campaign Management System described in this repository provides a comprehensive solution for managing ad campaigns, displaying ads to users, collecting feedback, and generating bill reports. The utilization of various components and tools allows for efficient ad campaign management and analysis.
