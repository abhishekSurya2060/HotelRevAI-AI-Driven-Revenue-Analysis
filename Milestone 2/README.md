📊 Hotel Revenue & Guest Insights Dashboard
Milestone 2 – Understand & Improve Revenue

📌 Project Overview
This project extends the Milestone 1 Power BI model to deliver a comprehensive revenue and guest analytics dashboard for a hotel business.
All calculations are implemented using DAX, and insights are presented through interactive and well-labeled visuals.

The dashboard focuses on:

Revenue & occupancy performance
Booking behavior and trends
Guest segmentation and characteristics
🧱 Data Model
The analysis is built on the existing Fact_Bookings table, containing:

revenue
reserved rooms
total rooms
booking
new bookings
booking channel
room type
guest country
customer.customer.id.1
booking duration
date
season
👉 No calculated columns are used; all logic is implemented via DAX measures.

🧮 DAX Measures – Revenue & Occupancy
Total Rooms
Total rooms = SUM(Fact_Bookings[Available_Rooms])

Rooms Occupied
Rooms Occupied = 
SUM ( 'Fact_Bookings'[Reserved_Rooms] )
Occupancy %
Occupancy % = 
DIVIDE (
    [Rooms Occupied],
    [Total Rooms],
    0
)
Total Revenue
Total Revenue = 
SUM ( Fact_Bookings[Revenue] )
Average Daily Rate (ADR)
ADR_new = 
DIVIDE (
    [Total Revenue],
    [Rooms Occupied],
    0
)
Revenue per Available Room (RevPAR)
RevPAR_new = 
DIVIDE (
    [Total Revenue],
    [Total Rooms],
    0
)
Total Bookings
Total Bookings = 
SUM ( 'Fact_Bookings'[New_Bookings] )
DAX Measures – Guest Segmentation
Bookings per Guest
Bookings per Guest = CALCULATE (
    COUNT ( 'Fact_Bookings'[Bookings] ),
    ALLEXCEPT ( 'Fact_Bookings', 'Fact_Bookings'[Customer.Customer.id.1] )
)
Guest Category (First-Time vs Loyal)
Guest Category = 
IF (
    [Bookings per Guest] = 1,
    "First-time Guest",
    "Loyal Guest"
)
Revenue per Guest
Revenue per Guest = 
CALCULATE (
    SUM ( 'Fact_Bookings'[Revenue]),
    ALLEXCEPT ( 'Fact_Bookings', 'Fact_Bookings'[Customer.Customer.id.1] )
)
Spender Category
Spender Category = 
IF (
    [Revenue per Guest] >= 500000,
    "High Spender",
    "Regular Guest"
)
Hotel Revenue & Guest Insights Dashboard
📈 Visuals & Their Purpose
🔝 KPI Cards
Total Revenue – Overall revenue generated
Occupancy % – Room utilization efficiency
ADR (Average Daily Rate) – Revenue per occupied room
RevPAR – Revenue performance considering availability
📈 Booking & Revenue Trends
Daily Booking Trend – Short-term demand fluctuations
Monthly Revenue Trend – Long-term revenue performance
Seasonal Revenue & Occupancy Trend – Peak vs off-peak analysis
🔄 Booking Channel Analysis
Direct vs OTA – Booking Comparison

Analyzes booking volume by channel

Direct vs OTA – Revenue Contribution

Evaluates channel profitability

👥 Guest Insights
Guest Type Distribution (First-Time vs Loyal Guests) Measures customer retention behavior

Spender Segmentation (High vs Regular Guests) Identifies high-value customers

Revenue by Guest Nationality Shows geographic revenue contribution

Guests by Booking Channel Highlights guest booking preferences

Length of Stay vs Revenue / Bookings Evaluates impact of stay duration on revenue

🎛 Interactive Slicers
The dashboard includes slicers to enable dynamic analysis:

Room Type

Hotel Branch / Location

Booking Source

All visuals respond interactively to slicer selections.

📈 Key Business Insights
Loyal guests drive repeat revenue and long-term value

High spenders contribute disproportionately to total revenue

Direct bookings are generally more profitable than OTA bookings

Clear seasonal patterns help optimize pricing and inventory

Longer stays positively impact total revenue

🛠 Tools & Technologies
Power BI
DAX
Data Modeling
Interactive Dashboards
✅ Conclusion
This dashboard provides a complete view of hotel performance, combining revenue, occupancy, booking behavior, and guest segmentation. It supports data-driven decision-making for pricing, marketing strategy, and customer retention.
