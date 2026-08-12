# 🚗 Car Sales Data Analysis | Power BI

An interactive **Power BI dashboard** built to analyze car sales performance, manufacturer trends, pricing, vehicle type mix, fuel efficiency, and vehicle value.

![Car Sales Dashboard](images/car-sales-dashboard.png)

## 📊 Project Overview

This project transforms raw vehicle-level data into a business-focused Power BI dashboard that helps answer questions such as:

- Which car models generate the highest sales?
- Which manufacturers perform best?
- How are sales distributed across vehicle types?
- How does vehicle price relate to sales?
- Is fuel efficiency associated with sales performance?
- Which vehicles show strong resale-value retention?

**Dataset:** 157 records and 16 fields.

## 🎯 Business Objectives

- Identify top-performing vehicle models and manufacturers.
- Analyze sales contribution by vehicle type.
- Understand price-volume patterns.
- Compare average vehicle prices across vehicle types.
- Explore fuel efficiency versus sales.
- Evaluate resale value as an additional product-value indicator.
- Present the results through an interactive dashboard.

## 🛠️ Tools & Technologies

- **Microsoft Power BI**
- **Power Query**
- **DAX**
- **CSV / Excel**
- **Data Cleaning & Transformation**
- **Data Visualization**
- **Business Intelligence**

## 📁 Dataset

The dataset contains fields covering:

| Field | Description |
|---|---|
| Manufacturer | Vehicle manufacturer |
| Model | Vehicle model |
| Sales_in_thousands | Sales volume |
| Price_in_thousands | Listed vehicle price |
| Vehicle_type | Vehicle category |
| Engine_size | Engine displacement |
| Horsepower | Engine horsepower |
| Wheelbase / Width / Length | Vehicle dimensions |
| Curb_weight | Vehicle weight |
| Fuel_capacity | Fuel tank capacity |
| Fuel_efficiency | Fuel efficiency |
| Latest_Launch | Latest launch date |
| Power_perf_factor | Vehicle performance factor |
| Resale_value | Estimated resale value |

## 🧹 Data Preparation

Key preparation steps included:

- Validating numeric data types.
- Converting `Latest_Launch` to Date type.
- Reviewing missing values.
- Reviewing potential duplicate records.
- Creating a Power Query Index column from 1 to 157 for row-level scatter-plot granularity.
- Creating calculated fields for dashboard analysis.

## 📐 Key DAX Measures

### Total Sales

```DAX
Total Sales =
SUM(Car_sales[Sales_in_thousands])
```

### Average Sales

```DAX
Average Sales =
AVERAGE(Car_sales[Sales_in_thousands])
```

### Average Price

```DAX
Average Price =
AVERAGE(Car_sales[Price_in_thousands])
```

### Manufacturers

```DAX
Manufacturers =
DISTINCTCOUNT(Car_sales[Manufacturer])
```

### Total Models

```DAX
Total Models =
DISTINCTCOUNT(Car_sales[Model])
```

### Average Fuel Efficiency

```DAX
Average Fuel Efficiency =
AVERAGE(Car_sales[Fuel_efficiency])
```

### Sales Percentage

```DAX
Sales % =
DIVIDE(
    [Total Sales],
    CALCULATE(
        [Total Sales],
        ALL(Car_sales[Vehicle_type])
    )
)
```

### Price Segment

```DAX
Price Segment =
SWITCH(
    TRUE(),
    Car_sales[Price_in_thousands] < 20, "Budget",
    Car_sales[Price_in_thousands] < 35, "Mid-Range",
    Car_sales[Price_in_thousands] < 50, "Premium",
    "Luxury"
)
```

## 📊 Dashboard Features

### KPI Cards
- **Total Models:** 156
- **Manufacturers:** 30
- **Average Price:** 27.39K
- **Total Sales:** 8.32K
- **Average Sales:** 53.00K

### Visuals
- Top Model
- Top Manufacturer
- Fuel Efficiency vs Sales
- Vehicle Type Sales Mix
- Average Price by Vehicle Type
- Vehicle Performance Matrix

## 🔎 Key Insights

- Total reported sales are approximately **8.32 million units**.
- Average sales per record are approximately **53.00K units**.
- **Ford** is the leading manufacturer by reported sales.
- **F-Series** is the best-selling model at approximately **540.56K units**.
- Budget vehicles contribute approximately **4.03 million reported units**.
- Mid-Range vehicles contribute approximately **3.66 million reported units**.
- Price and sales show a correlation of approximately **-0.30** in the dataset.
- Fuel efficiency and sales show a correlation of approximately **-0.02**, indicating little linear association in this sample.
- Price and resale value show a strong correlation of approximately **0.95** among available records.

## 💡 Business Takeaways

The dashboard shows that:

1. Sales are concentrated more heavily in lower-priced vehicle segments.
2. A small number of models account for a large share of reported sales.
3. Manufacturer performance varies significantly across the dataset.
4. Fuel efficiency alone does not explain sales differences in this sample.
5. Resale value provides a useful product-value perspective alongside sales volume.

## 🚀 Future Enhancements

- Add manufacturer benchmarking.
- Add a dedicated Top 10 resale-retention visual.
- Create a power-to-weight performance metric.
- Add launch-year trend analysis.
- Add historical sales data for true time-series analysis.
- Add richer drill-through pages for manufacturer and model analysis.

## 📂 Suggested Repository Structure

```text
car-sales-data-analysis/
│
├── data/
│   └── Car_sales.csv
│
├── dashboard/
│   └── Car_Sales_Dashboard.pbix
│
├── images/
│   └── car-sales-dashboard.png
│
├── documentation/
│   └── Car_Sales_Data_Analysis_Project_Documentation.docx
│
└── README.md
```

## 👨‍💻 Author

**Gnanendra Upputholla**

Aspiring Data Analyst  
SQL | Python | Power BI | Excel

📍 Hyderabad, India

---

⭐ **If you found this project useful, consider starring the repository.**
