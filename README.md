# FineLine Ticketing System

Software Requirements Specification

Version 1.0

Date 02/05/2026


Group #17
Esteban Naranjo, Jackson Adams, Bryan Ly





Prepared for
CS 250- Introduction to Software Systems
Instructor: Gus Hanna, Ph.D.
Spring 2026


Revision History

Date
Description
Author
Comments
Feb 19, 2026
Version 1.0
Esteban Naranjo, Jackson Adams, Bryan Ly
Initial SRS Submission



























Document Approval

The following Software Requirements Specification has been accepted and approved by the following:
Signature
Printed Name
Title
Date


<Your Name>
Software Eng.




Dr. Gus Hanna
Instructor, CS 250











					
Table of Contents

Revision History	ii
Document Approval	ii
1. Introduction	1
1.1 Purpose	1
1.2 Scope	1
1.3 Definitions, Acronyms, and Abbreviations	1
1.4 References	1
1.5 Overview	1
2. General Description	2
2.1 Product Perspective	2
2.2 Product Functions	2
2.3 User Characteristics	2
2.4 General Constraints	2
2.5 Assumptions and Dependencies	2
3. Specific Requirements	2
3.1 External Interface Requirements	3
3.1.1 User Interfaces	3
3.1.2 Hardware Interfaces	3
3.1.3 Software Interfaces	3
3.1.4 Communications Interfaces	3
3.2 Functional Requirements	3
3.2.1 <Functional Requirement or Feature #1>	3
3.2.2 <Functional Requirement or Feature #2>	3
3.3 Use Cases	3
3.3.1 Use Case #1	3
3.3.2 Use Case #2	3
3.4 Classes / Objects	3
3.4.1 <Class / Object #1>	3
3.4.2 <Class / Object #2>	3
3.5 Non-Functional Requirements	4
3.5.1 Performance	4
3.5.2 Reliability	4
3.5.3 Availability	4
3.5.4 Security	4
3.5.5 Maintainability	4
3.5.6 Portability	4
3.6 Inverse Requirements	4
3.7 Design Constraints	4
3.8 Logical Database Requirements	4
3.9 Other Requirements	4
4. Analysis Models	4
4.1 Sequence Diagrams	5
4.3 Data Flow Diagrams (DFD)	5
4.2 State-Transition Diagrams (STD)	5
5. Change Management Process	5
A. Appendices	5
A.1 Appendix 1	5
A.2 Appendix 2	5



1. Introduction

This Software Requirements Specification (SRS) describes the requirements for the FineLine Cinema Ticketing System. It defines the functional and non-functional requirements needed for the design, development, testing, and maintenance of the system.
This document is intended for the development team, project stakeholders, and theater staff who will use or manage the system. It provides a complete description of what the system must do and the constraints under which it must operate.

1.1 Purpose

The purpose of this document is to provide thorough and complete information about the requirements of the FineLine Cinema Ticketing System. This document outlines the system’s requirements and the constraints under which it will operate.
The intended audience includes the development team and the cinema staff, who will use and manage the system. This document will guide the design, implementation, and testing of the system.

1.2 Scope

The software product to be developed is the FineLine Cinema Ticketing System, a web-based ticketing platform for movie theaters located in the San Diego area.

The system will allow customers to browse movies, view trailers, select theaters and showtimes, purchase tickets, select seats (for deluxe auditoriums), and order food and drinks. The system will also allow theater administrators to manage movie listings, showtimes, pricing, seating availability, and ticket data. The system will support both online and in-person ticket sales through a shared real-time database.
The system will initially serve 20 theaters with 10 auditoriums per theater operating within the Pacific time zone. Each regular auditorium contains 150 seats, and each deluxe auditorium contains 75 assigned seats. Customers may purchase up to 20 tickets per transaction and may book tickets up to two weeks in advance.
The constraints for the system are such that the system will not process refunds online, as refunds will be handled in person by theater staff. The system will not include a standalone mobile application and will operate through standard web browsers.
The primary objectives of this system are to:
Improve the efficiency of ticket purchasing and seat management
Reduce existing performance and reliability issues in the current system
Support up to 24,000 concurrent users during peak demand periods
Provide real-time updates of seat availability across all theaters
Offer a secure and user-friendly experience for customers and staff
This document defines the complete set of functional and non-functional requirements necessary to design, implement, and test the FineLine Cinema Ticketing System.

1.3 Definitions, Acronyms, and Abbreviations

SRS – Software Requirements Specification. A document that defines the functional and non functional requirements of a software system.
FineLine Cinema Ticketing System – The web based ticketing platform described in this document.
Administrator – A theater staff member responsible for managing movies, showtimes, pricing, seating, and system data.
Customer – A user who accesses the system to browse movies, purchase tickets, or order food and drinks.
Deluxe Theater – A theater with assigned seating and 75 seats.
Regular Theater – A theater with general seating and 150 seats.
Checkout Timer – The five minute period during which selected tickets or seats are reserved before being released.
Concurrent Users – The number of users accessing the system at the same time.
Membership Account – A subscription-based account that allows customers to reserve tickets under membership benefits.
HTTPS – HyperText Transfer Protocol Secure. The encrypted communication protocol used between the client browser and the server.
Third-Party Payment Service – An external payment processing provider used to securely process credit or debit card transactions.
1.4 References
San Diego State University. (2026). CS250 Software Requirements Specification (SRS) template.
San Diego State University. (2026). Lecture 3 – Requirements gathering [PowerPoint slides].
IEEE Computer Society. (1998). IEEE 830-1998: IEEE guide to software requirements specifications. IEEE.
AMC Theatres. (n.d.). AMC Chula Vista 10 showtimes. https://www.amctheatres.com/movie-theatres/san-diego/amc-chula-vista-10/showtimes

1.5 Overview

This Software Requirements Specification (SRS) is organized into three main sections.
Section 1 provides an introduction to the document, including its purpose, scope, definitions, references, and overall organization.
Section 2 describes the general characteristics of the FineLine Cinema Ticketing System, including the product perspective, major system functions, user characteristics, constraints, and assumptions.
Section 3 presents the specific requirements of the system. This includes external interface requirements, functional requirements, use cases, classes and objects, and non-functional requirements such as performance, reliability, availability, security, maintainability, and portability.
Together, these sections define the complete set of requirements needed for the design, development, and testing of the FineLine Cinema Ticketing System.

2. General Description
This section gives a general overview of the Movie Theater Ticketing System (FineLine Cinema) and the factors that affect how the system will be built. It explains who the system is for, what it is meant to do, and the basic assumptions and limits that shape it. The system is designed to let customers buy movie tickets online using common payment methods such as credit or debit cards, and to be usable by a wide range of customers, including support for multiple languages if needed. This section does not go into detailed system rules, but instead provides background information to help understand the specific requirements described later in this document.

2.1 Product Perspective
The Movie Theater Ticketing System (FineLine Cinema) is a software system designed to support the sale and management of movie tickets for a single movie theater or theater chain. Instead of relying only on in person ticket sales, the system allows customers to view movie trailers, showtimes, select seats, and purchase tickets online. The system also allows customers to order food that will be delivered to their seats during the show, with the option to continue adding food during the movie and have the charges applied to their account. In addition, the system provides theater staff with tools to manage movies, showtimes, and seat availability. Overall, the ticketing system supports the theater’s day-to-day operations by connecting customers, staff, and payment services within a single system.

2.2 Product Functions
The Movie Theater Ticketing System (FineLine Cinema) will provide the following main functions:
Allow customers to browse movies that are now playing and coming soon
Allow customers to watch movie trailers
Allow customers to search for movies by title, genre, or showtime
Allow customers to select a theater location (optionally using device location services)
Allow customers to select showtimes and reserve seats
Allow customers to purchase tickets online
Allow customers to order food and drinks in advance or during the movie
Allow customers to view promotions, rewards, or membership options
Allow customers to create and manage an account
Allow theater staff to manage movie listings, showtimes, and seat availability
Provide an interactive seat map for assigned-seating theaters
Display seat availability status (available, selected, occupied)
Identify wheelchair and companion seating
Process electronic payments securely
Send confirmation notifications for ticket and food purchases
Provide digital tickets that can be scanned at the theater
Provide refund capabilities (in person)
2.3 User Characteristics
The primary users of the system are customers and theater administrators. Customers are general users with different levels of technical experience who want to browse movies, select showtimes, and purchase tickets. Because customers may not be highly technical, the system should be simple to use and easy to navigate.
Theater administrators are staff members responsible for managing movies, showtimes, seating availability, and basic system updates. Administrators are expected to have basic computer skills and a general understanding of theater operations.

2.4 General Constraints
The following general constraints apply to the Movie Theater Ticketing System (FineLine Cinema):
The Movie Theater Ticketing System must operate as a web based system and be accessible through standard internet browsers. The system must support both online ticket purchases and in-person sales, with both methods sharing the same live data and database.
The system will initially serve 20 theaters with 10 auditoriums each located in the San Diego area and operate within the Pacific time zone. Each regular auditorium contains 150 seats, while deluxe auditoriums contain 75 assigned seats. The system must support a minimum of 24,000 concurrent users during peak operational periods.
Ticket purchases are limited to a maximum of 20 tickets per transaction. Customers may book tickets up to two weeks in advance and may purchase tickets up to 10 minutes after showtime.
The project budget is approximately $500,000, and the client expects a viable prototype within four months.
These constraints may affect how the system is designed and implemented.

2.5 Assumptions and Dependencies
The development of the Movie Theater Ticketing System is based on several key assumptions and dependencies:
It is assumed that users will have access to a reliable internet connection and a supported web browser in order to use the system. The system also assumes that a centralized database will store information for all theaters, organized by location.
The system depends on secure third party payment services to process electronic transactions. It also assumes that theater administrators will maintain accurate and up to date movie schedules, pricing information, and seat availability.
Refunds will be handled in person by theater staff and will not be processed directly through the system.
Some features, such as recommending nearby theaters using location services, may be considered in future versions of the system.
If any of these assumptions change, the requirements described in this document may need to be updated.

3. Specific Requirements
This section lists the detailed requirements for the Movie Theater Ticketing System (FineLine Cinema). These requirements are written to guide the system’s design, implementation, and testing. Each requirement is stated clearly so it can be checked and verified. Requirements in this section are numbered to make them easy to reference in later documents (use cases, testing, and future updates). This section focuses on what the system must do, not how it will be built.

3.1 External Interface Requirements
This section defines how the Movie Theater Ticketing System (FineLine Cinema) interacts with users, hardware, external software, and communication networks.

3.1.1 User Interfaces

UI-1 (High Priority)
The system shall be accessible through standard modern web browsers.
UI-2 (High Priority)
The system shall allow customers to browse movies currently playing and movies available within two weeks.
UI-3 (High Priority)
The system shall display available showtimes for each movie.
UI-4 (High Priority)
The system shall allow customers to select the number of tickets (maximum of 20 per transaction).
UI-5 (High Priority)
For deluxe auditoriums, the system shall display a visual seating chart showing available, selected, and occupied seats.
UI-6 (High Priority)
The system shall visually distinguish wheelchair accessible seats and companion seats on the seating chart.
UI-7 (High Priority)
The system shall allow customers to select seats in deluxe auditoriums.
UI-8 (Medium Priority)
For regular auditoriums, the system shall allow ticket purchase without assigned seating.
UI-9 (High Priority)
The system shall provide a five minute timer once the customer begins the checkout process.
UI-10 (High Priority)
The system shall allow customers to enter payment information and complete a purchase.
UI-11 (Medium Priority)
The system shall allow customers to purchase food and drinks during checkout.
UI-12 (Medium Priority)
The system shall allow customers to add additional food and drinks during the movie, which will be charged to their account.
UI-13 (Low Priority)
The system shall display movie ratings and review scores (e.g., Rotten Tomatoes or IMDb scores).
UI-14 (Medium Priority)
The system shall display a feedback option (e.g., smiley face rating) after purchase.
UI-15 (High Priority)
The system shall provide an administrator interface for managing movies, showtimes, pricing, and seat availability.


3.1.2 Hardware Interfaces

HW-1 (High Priority)
The system shall operate on customer devices including desktop computers, laptops, and tablets.
HW-2 (High Priority)
The system shall support a centralized database server used by all 20 theaters.
HW-3 (Medium Priority)
The system shall share ticket information with the theater’s in person sales system to keep seat availability updated in real time.

3.1.3 Software Interfaces

SW-1 (High Priority)
The system shall interface with secure third party payment processing services.
SW-2 (High Priority)
The system shall connect to a centralized database partitioned by theater location.
SW-3 (Medium Priority)
The system shall support integration with membership accounts for subscription based reservations.
SW-4 (Low Priority)
The system shall interface with external movie rating services to retrieve review scores.

3.1.4 Communications Interfaces

COM-1 (High Priority)
The system shall operate over standard internet protocols (HTTPS).
COM-2 (High Priority)
All communication between the client browser and server shall be encrypted.
COM-3 (High Priority)
The system shall support at least 24,000 concurrent users while maintaining consistent response times, transaction reliability, and overall system stability.
COM-4 (Medium Priority)
The system shall provide real-time updates to seat availability across online and in-person sales systems.

3.2 Functional Requirements
This section describes the specific functional features of the FineLine Cinema Ticketing System. Each feature is defined in terms of inputs, processing, outputs, and error handling.
3.2.1 Ticket Purchase Management #1

3.2.1.1 Introduction
This feature allows customers to select a movie, choose a showtime, select the number of tickets (up to 20), and complete a secure purchase through the web based system.
This feature is critical to the primary function of the system.

3.2.1.2 Inputs
Selected movie
Selected theater location
Selected showtime
Number of tickets (1–20)
Ticket type (regular, student, military, senior)
Payment information (credit/debit card)
Membership ID (if applicable)
3.2.1.3 Processing

The system shall:
Verify ticket availability
Validate the ticket quantity does not exceed 20 per transaction
Apply any applicable discounts
Start a five minute checkout timer
Process payment through third party payment service
Confirm transaction success or failure
Update seat/ticket availability in real time
3.2.1.4 Outputs
Digital ticket confirmation
Order receipt
Confirmation email/notification
Updated seat availability in system
3.2.1.5 Error Handling

The system shall:
Display an error message if ticket quantity exceeds 20
Display an error message if payment fails
Release selected tickets if checkout timer expires
Prevent purchase if showtime exceeds allowed purchase window
3.2.2 Seat Selection Management #2

3.2.2.1 Introduction
This feature allows customers to view seat availability in real time and select seats for the deluxe auditorium.
3.2.2.2 Inputs
Selected theater
Selected movie
Selected showtime
Seat selection (for deluxe auditorium)
3.2.2.3 Processing
The system shall:
Display interactive seat map
Show seat status (available, selected, occupied)
Mark wheelchair accessible and companion seats
Prevent selection of occupied seats
Reserve selected seats during checkout timer
3.2.2.4 Outputs
Visual confirmation of selected seats
Reserved seat status during checkout
Updated seat availability after successful purchase
3.2.2.5 Error Handling
The system shall:
Prevent selection of unavailable seats.
Display a message if a seat becomes unavailable during checkout.
Release reserved seats if the checkout timer expires before payment confirmation.
3.3 Use Cases 

3.3.1 Use Case #1- Purchase Tickets
Primary Actor: Customer
Description:
This use case describes the process of a customer purchasing one or more movie tickets through the FineLine Cinema Ticketing System.
Preconditions:
The system is operational.
The selected movie and showtime exist in the system.
Tickets are available for purchase.
Main Flow:
The customer selects a theater location.
The customer selects a movie.
The customer selects a showtime.
The customer selects the number of tickets (maximum of 20).
If applicable, the customer selects ticket type (regular, student, military, senior).
The system displays a checkout page.
The system starts a five minute checkout timer.
The customer enters payment information.
The system processes payment through third party payment service.
The system confirms successful transactions.
The system generates digital tickets and receipts.
The system updates ticket availability in real time.
Alternative Flow:
If payment fails, the system displays an error message and allows retry.
If the checkout timer expires, selected tickets are released.
Postconditions:
Ticket purchase is recorded in the database.
Seat or ticket availability is updated.
Confirmation notification is sent to the customer.
3.3.2 Use Case #2 – Select Seat (Deluxe Auditorium)
Primary Actor: Customer
Description:
This use case describes how a customer selects specific seats in a deluxe auditorium with assigned seating.
Preconditions:
Deluxe auditorium selected.
Seats are available for the selected showtime.
Main Flow:
The customer selects theater location
The customer selects movies and showtime.
The system displays an interactive seating chart.
The system shows seat status (available, selected, occupied).
The system identifies wheelchair accessible and companion seats.
The customer selects available seats.
The system temporarily reserves selected seats during checkout timer.
Alternative Flow:
If a selected seat becomes unavailable, the system displays a message and prompts reselection.
If the checkout timer expires, reserved seats are released.
Postconditions:
Selected seats are confirmed upon successful payment.
Seat status is updated in the database.

3.4 Classes / Objects (recommended set)
CustomerAcount
- accountId : String
- membershipId : String
- fullName : String
- emailAddress : String
- phoneNumber : String
- passwordHash : String
- storedPaymentMethods : List<PaymentMethod>
- membershipId : String
- purchaseHistory : List<TicketOrder>
+ AddPaymentMethod(String cardNumber, String cardName, String, String CVV, String ExperationDate) : Void
+ CreateAccount(String fullName, String email, String password) : CustomerAccount
+ UpdateAccount(String fullName, String email, String phoneNumber) : Void
+ DeleteAccount() : Void
+ Login() : Boolean
+ Logout() : Void
+ ViewOrders() : List<TicketOrder>

References: Use Case 3.3.1 (Purchase Tickets)

Movie
- movieId : String
- title : String
- genre : String
- runtimeMinutes : Integer
- rating : String
- description : String
- trailerURL : String
- reviewScore : Float
+ GetShowtimes(String theaterId) : List<Showtime>
+ GetDetails() : Movie

References: Use Case 3.3.1 (Purchase Tickets)




Showtime
- showTimeId : String
- movieId : String
- theaterId : String
- auditoriumId : String
- startTime : DateTime
- endTime : DateTime
- isSoldOut : Boolean
- ticketPriveRegular : Float
- purchaseCutoffTime : DateTime
+ IsPurchasable(DateTime currentTime) : Boolean
+ GetAvailability() : Integer
+ UpdateShowtime(String adminId, DateTime startTime, DateTime endTime) : Void

References: Use Case 3.3.1 (Purchase Tickets)

Seat
- theaterId : String
- auditoriumId : String
- seatId : String
- row : String
- seatNumber : Integer
- seatType : String // standard, wheelchair, companion
- seatStatus : String // available, unavailable, selected
+ Reserve(String orderId) : Boolean
+ ReleaseSeat() : Void
+ MarkOccupied() : Void

References: Use Case 3.3.2 (Select Seat)






TicketOrder
- orderId : String
- accountId : String
- showTimeId : String
- ticketCount : Integer
- ticketTypeCounts : Map<String, Integer>
- selectedSeats: List<Seat> // deluxe only
- ticketPrice : Float
- localTaxes : Float
- paymentStatus : String
- checkoutStartTime : DateTime
- confirmationCode : String
- qrCode : String
+ CalculateTotal() : Float
+ StartCheckoutTimer() : Void
+ ConfirmPayment(String paymentToken) : Boolean
+ GenerateQRCode() : String
+ SendConfirmation() : Void

References: Use Case 3.3.1 (Purchase Tickets)

FoodOrder
- ticketOrderId : String
- orderStatus: String
- orderType : String
- allergies : String
- orderPreperationTime : Integer
+ FoodOrder(List<String> items) : FoodOrder
+ CompleteOrder() : Void






Auditorium
- auditoriumId : String
- theaterId : String
- numberOfSeats : Integer
- currentMovieId : Movie
+ Auditorium() : Auditorium
+ ChangeMovie(Movie newMovie) : Void



Theater
- theaterId : String
- theaterAddress : String
- numberOfAuditoriums : Integer // const
+ Theater() : Theater
+ GetTheaterAddress() : String



3.5 Non-Functional Requirements
This section outlines the non-functional requirements for the FineLine Cinema Ticketing System: operational constraints, performance characteristics, and quality attributes. All requirements are testable and measurable. 

3.5.1 Performance
The system shall support a minimum of 24,000 concurrent users during peak demand.
Payment transactions shall be completed within 5 seconds
processing at least 4,800 ticket purchase transactions per minute during peak demand
support scaling to accommodate high-demand movie releases without system failure

*payment two different systems; online and in person*
The system shall support credit and debit card payment through a secure third party payment provider.


3.5.2 Reliability
The system shall maintain reliable operation under normal and peak load conditions.
The system shall achieve a Mean Time Between Failures (MTBF) greater than 30 days.


In the event of a server failure, core system functionality shall be restored within 60 seconds.


Automated database backups shall occur at intervals not exceeding 15 minutes.


Backup data shall be stored securely and recoverable without data corruption.


No completed transaction shall be lost due to system failure.


3.5.3 Availability
The system shall be accessible to users with minimal downtime.
The system shall maintain at least 99% uptime per calendar month, excluding scheduled maintenance.


The system shall be available 24 hours per day, 7 days per week outside of scheduled maintenance windows.


Scheduled maintenance shall not exceed 2 hours per week.


In the event of infrastructure failure, automatic failover shall occur within 60 seconds.


3.5.4 Security
The system shall implement security mechanisms to protect user data, payment information, and system integrity.
Secure Communication
All communication between client devices and the server shall use HTTPS with TLS encryption.


No sensitive data shall be transmitted over unencrypted channels.


Payment Security
The system shall comply with PCI-DSS standards for processing and storing payment information.


Payment information shall not be permanently stored in the system database unless tokenized by the third party payment provider.


Authentication and Authorization
Users shall be required to authenticate using a valid username and password before accessing personal account information.


The system shall enforce strong password requirements (minimum length, character complexity).


Multi-factor authentication (MFA) shall be supported for administrator accounts.


Bot Protection
The system shall implement CAPTCHA or equivalent human-verification mechanisms during checkout.


The system shall enforce rate limiting to prevent automated ticket purchasing.


The system shall monitor abnormal purchasing behavior and flag suspicious activity.


Data Protection
User passwords shall be stored using secure hashing algorithms (e.g., bcrypt or Argon2).


Sensitive user data shall be encrypted at rest.

3.5.5 Maintainability
The system shall be designed to allow efficient updates, bug fixes, and feature enhancements.
The system shall follow a modular architecture in which components are logically separated to reduce interdependencies.


Source code shall follow consistent coding standards and naming conventions.


All major modules shall include inline documentation and API level documentation sufficient for future developers to understand system functionality.


System logs shall be generated for critical events (e.g., failed payments, authentication attempts, system errors).


System logs shall be retained for a minimum of 30 days.


The system shall allow updates to movie listings, pricing, and showtimes without requiring system downtime.

3.5.6 Portability
The system shall be deployable and accessible across multiple environments and platforms.
The system shall operate through modern web browsers including Chrome, Safari, Microsoft Edge, and Firefox.


The system shall be accessible on desktop computers, laptops, tablets, and mobile browsers.


The system shall support deployment on Linux based cloud server environments.


The system shall not require installation of additional client side software.


3.6 Brief Overview of System
The FineLine Cinima Ticketing System is a web-based client-server application that will enable customers and theater administrators to interact with a ticketing and management system in real time.

From a user perspective…

From an administrative perspective…
3.7 Design Constraints
Specify design constrains imposed by other standards, company policies, hardware limitation, etc. that will impact this software project.
3.8 Logical Database Requirements
Will a database be used?  If so, what logical requirements exist for data formats, storage capabilities, data retention, data integrity, etc.
3.9 Other Requirements
Catchall section for any additional requirements.
4. Analysis Models
List all analysis models used in developing specific requirements previously given in this SRS.  Each model should include an introduction and a narrative description.  Furthermore, each model should be traceable the SRS’s requirements.
4.1 Sequence Diagrams
4.3 Data Flow Diagrams (DFD)
4.2 State-Transition Diagrams (STD)
5. Change Management Process
Identify and describe the process that will be used to update the SRS, as needed, when project scope or requirements change.  Who can submit changes and by what means, and how will these changes be approved.
A. Appendices
Appendices may be used to provide additional (and hopefully helpful) information.  If present, the SRS should explicitly state whether the information contained within an appendix is to be considered as a part of the SRS’s overall set of requirements.

Example Appendices could include (initial) conceptual documents for the software project, marketing materials, minutes of meetings with the customer(s), etc.
A.1 Appendix 1
A.2 Appendix 2
