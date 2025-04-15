# Hotel Booking Analysis Project

## Overview
This project analyzes hotel booking data to understand patterns in reservations and cancellations. The dataset contains information about bookings for two hotels (Resort Hotel and City Hotel) in Portugal, including customer details, booking characteristics, and reservation status.

## Dataset Description
The dataset contains 119,390 entries with 32 features including:
- Hotel type (Resort or City)
- Booking status (canceled or not)
- Customer details (adults, children, country)
- Booking characteristics (lead time, room type, meal type)
- Reservation details (dates, status)

## Key Findings

### Data Cleaning & Preprocessing
- Removed invalid records (bookings with 0 guests)
- Handled missing values:
  - Dropped 'agent' and 'company' columns due to high missingness
  - Filled missing 'children' values with 0
  - Filled missing 'country' values with 'PRT' (Portugal)
- Addressed outliers in:
  - Number of adults, children, and babies
  - Lead time (capped at 350 days)
  - Stay duration (weekend and week nights)
  - ADR (average daily rate)
- Removed duplicate records (32,052 duplicates found)

### Exploratory Data Analysis
1. **Seasonal Trends**:
   - Both hotels see peak bookings in summer (July-August)
   - Winter months have lowest occupancy
   - Cancellation rates follow similar seasonal patterns

2. **Hotel Differences**:
   - City Hotel has more bookings but higher cancellation rate (30%) vs Resort Hotel (24%)
   - Cancellation rates vary by booking channel (highest for online travel agencies)

3. **Customer Insights**:
   - 40.9% of cancellations come from Portuguese customers
   - Customers with children tend to cancel less
   - Transient customers have highest cancellation rates

4. **Key Correlations**:
   - Strongest predictors of cancellation:
     - Reservation status (0.89 correlation)
     - Lead time (0.19)
     - Parking spaces required (0.18)
     - Market segment (0.18)

## Machine Learning Models
We built several models to predict booking cancellations:

| Model               | Accuracy | Precision | Recall | F1 Score |
|---------------------|----------|-----------|--------|----------|
| SVC (Linear)        | 0.988    | 1.000     | 0.956  | 0.977    |
| KNN                 | 0.998    | 0.998     | 0.996  | 0.997    |
| Logistic Regression | 0.984    | 0.984     | 0.956  | 0.970    |
| XGBoost             | 0.270    | 0.270     | 1.000  | 0.426    |

**Best Performing Model**: K-Nearest Neighbors achieved 99.8% accuracy

## How to Use This Project

### Requirements
- Python 3.x
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost

### Running the Analysis
1. Clone the repository
2. Install dependencies: `pip install -r requirements.txt`
3. Run the Jupyter notebook: `jupyter notebook Hotel_Booking_Analysis.ipynb`

