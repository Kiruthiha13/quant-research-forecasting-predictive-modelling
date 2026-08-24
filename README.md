# Natural Gas Storage Contract Pricing

## Project Overview

This project was completed as part of the **JPMorgan Chase Quantitative Research Job Simulation** on Forage.

The project focuses on **natural gas price analysis and commodity storage contract pricing**. The objective was to analyze historical natural gas price data, estimate prices for dates beyond the available market data, and develop a prototype model to value a natural gas storage contract.

The project consists of two tasks:

* **Task 1 – Investigate and Analyze Price Data**
* **Task 2 – Price a Commodity Storage Contract**

---

## Business Objective

Natural gas storage contracts allow market participants to purchase gas when prices are relatively low, store it, and withdraw and sell it at a later date when prices may be higher.

For a trading desk, accurately estimating gas prices across historical and future dates is important for determining the potential value of these contracts.

This project therefore addresses two key requirements:

1. Develop a method to estimate natural gas prices for dates where market observations are unavailable.
2. Use those price estimates to calculate the value of a storage contract while considering operational constraints and associated costs.

---

## Task 1 – Investigate and Analyze Price Data

### Objective

Analyze the available natural gas price data and develop a price estimation approach that can return a gas price for a given date, including dates beyond the available historical observations.

### Approach

The analysis includes:

* Loading and cleaning the historical natural gas price data.
* Converting and sorting the date information.
* Exploring historical price trends.
* Visualizing the observed price series.
* Using interpolation to estimate prices between observed market dates.
* Incorporating seasonal patterns in natural gas prices.
* Extrapolating prices beyond the available dataset to provide indicative future estimates.
* Creating a price estimation function that accepts a date and returns an estimated price.

### Key Considerations

Natural gas prices can exhibit seasonal behavior because demand for heating and other factors can vary throughout the year. Therefore, the price estimation approach considers the relationship between price movements and the time of year rather than relying only on a simple linear trend.

The resulting price function provides the estimated commodity price required by the storage contract pricing model in Task 2.

---

## Task 2 – Price a Commodity Storage Contract

### Objective

Develop a prototype pricing function that calculates the value of a natural gas storage contract based on injection and withdrawal activities.

### Pricing Concept

The basic value of the contract is determined by the difference between the selling price and purchasing price, multiplied by the quantity of gas traded.
Additional costs associated with storing and handling the commodity are deducted from the contract value.

Conceptually:

**Contract Value = Withdrawal Revenue − Injection Cost − Storage Costs − Other Applicable Costs**

### Model Inputs

The pricing function takes into account:

* Injection dates
* Withdrawal dates
* Gas prices on injection dates
* Gas prices on withdrawal dates
* Injection quantities
* Withdrawal quantities
* Injection and withdrawal rates
* Maximum storage capacity
* Storage costs
* Price estimation function

### Storage Constraints

The model considers operational constraints such as:

* Maximum storage capacity
* Injection rate
* Withdrawal rate
* Available inventory
* Storage costs
* Multiple injection and withdrawal dates

The model also checks that the storage schedule is consistent with the available inventory and storage capacity.

### Output

The function returns the calculated **value of the storage contract** based on the specified trading strategy and assumptions.

Sample scenarios were used to test the pricing function with different injection and withdrawal dates and quantities.

---

## Methodology

### Price Analysis

The price analysis workflow can be summarized as:

```text
Historical Market Data
        ↓
Data Cleaning & Preparation
        ↓
Exploratory Price Analysis
        ↓
Seasonality Analysis
        ↓
Interpolation
        ↓
Future Price Extrapolation
        ↓
Price Estimation Function
```

### Storage Contract Pricing

```text
Injection / Withdrawal Schedule
              ↓
       Price Estimation
              ↓
       Storage Constraints
              ↓
    Revenue & Purchase Costs
              ↓
        Storage Costs
              ↓
      Contract Valuation
```

---

## Technologies Used

* **Python**
* **Pandas** – Data manipulation and preparation
* **NumPy** – Numerical calculations
* **Matplotlib** – Data visualization
* **SciPy** – Interpolation
* **Scikit-learn** – Regression-based price estimation
* **Jupyter Notebook** – Analysis and implementation

---

## Repository Structure

```text
quant-research-forecasting-predictive-modelling/
│
├── scripts/
│   └── Commodity_Price_Forecasting_and_Storage_Contract_Pricing.ipynb
│
└── README.md
```

**Task 1 – Price Analysis and Forecasting**

Contains the analysis of historical natural gas prices, seasonal patterns, interpolation, and future price estimation.

**Task 2 – Commodity Storage Contract Pricing**

Contains the storage contract pricing function, storage constraints, cost calculations, and sample contract scenarios.

---

## Assumptions

The prototype follows the assumptions provided for the exercise:

* No transport delays.
* Interest rates are assumed to be zero.
* Weekends and market holidays are not explicitly modeled.
* The available market data is used to estimate prices where direct observations are unavailable.
* The model is intended as a prototype and would require further validation and testing before production use.

## Future Improvements

Potential improvements to the prototype include:

* More robust time-series forecasting techniques.
* Formal model validation and backtesting.
* Improved treatment of seasonality.
* Incorporation of additional market variables.
* More extensive testing of storage constraints and edge cases.
* Sensitivity analysis to understand how contract value changes with gas prices, storage costs, and quantities.
* Discounting of future cash flows when non-zero interest rates are introduced.

---
