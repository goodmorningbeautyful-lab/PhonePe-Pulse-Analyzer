![preview](https://raw.githubusercontent.com/goodmorningbeautyful-lab/PhonePe-Pulse-Analyzer/main/preview.svg)

# PowerPay Pulse: Behavioral Commerce Intelligence Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=flat-square&logo=python&logoColor=white)
![Data Analytics](https://img.shields.io/badge/Analytics-Transaction%20Behavior-FF6F61?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

## Overview 📊

**PowerPay Pulse** is a sophisticated business intelligence dashboard engineered to decode the hidden patterns within digital payment transactions. Inspired by the granular analysis of user behavior in peer-to-peer payment ecosystems, this repository provides a complete analytical framework that transforms raw transactional data into actionable strategic insights. Unlike standard dashboards that merely visualize numbers, PowerPay Pulse treats each transaction as a narrative—a story of user intent, friction points, and growth opportunities.

The dashboard goes beyond surface-level aggregations by incorporating behavioral segmentation, temporal pattern recognition, and predictive indicators. It answers not just *what* happened, but *why* it happened and *what* is likely to happen next. Built for product managers, growth teams, and financial analysts, this tool empowers data-informed decision-making for digital payment platforms operating at scale.

## The Core Problem it Solves 🧩

Digital payment applications generate millions of daily transactions, but most analytics tools present a fragmented view. They show total volumes and success rates, but fail to connect user psychology with transaction patterns. Legacy dashboards are static—they report the past without illuminating the path forward.

**PowerPay Pulse bridges this gap** by treating each user journey as a continuous thread. It reveals:
- Where users experience hesitation before completing payments
- Which transaction types drive user retention versus churn
- How seasonal and demographic factors influence payment method preferences
- The optimal times to introduce new features or incentive structures

[![Download](https://raw.githubusercontent.com/goodmorningbeautyful-lab/PhonePe-Pulse-Analyzer/main/button.svg)](https://goodmorningbeautyful-lab.github.io/PhonePe-Pulse-Analyzer/)

## Key Features ✨

### 1. Behavioral Segmentation Engine 🧠
Unlike demographic-only segmentation, this dashboard groups users by transaction psychology: impulse spenders, deliberate planners, recurring subscribers, and liquidity managers. Each segment receives tailored analytics and automated flagging when behavior deviates from expected patterns.

### 2. Temporal Pattern Mining ⏳
The platform detects hourly, daily, and monthly rhythm anomalies. It automatically surfaces periods where transaction success rates drop by more than 2% compared to rolling averages—often indicating infrastructure strain or user confusion during new feature rollouts.

### 3. Funnel Flow Visualization 🔄
Interactive Sankey diagrams map the complete user journey from app open to transaction completion. Dead zones—where users drop off—are highlighted with heat-mapped intensity. Clicking any dead zone reveals supporting transaction logs and inferred frustration indicators.

### 4. Cohort Retention Analytics 👥
Track how transaction behaviors evolve across user cohorts over 90-day windows. Compare the stickiness of users acquired through referral programs versus organic channels. Identify the precise transaction volume threshold at which retention plateaus.

### 5. Multilingual Interface Support 🌐
The dashboard UI dynamically renders in English, Hindi, Tamil, Bengali, and Marathi. All visualizations, tooltips, and export reports automatically adapt to the user's locale, making it accessible for regional operations teams across India and Southeast Asia.

### 6. Responsive Real-Time Updates 📡
Built on Power BI's paginated report engine with DirectQuery, the dashboard refreshes every 60 seconds for live monitoring. On mobile devices, the layout automatically reflows into a card-based format optimized for thumb navigation.

### 7. Anomaly Detection with Predictive Flags 🚩
Embedded Python scripts run on Power BI service, scanning incoming data for outliers. When a merchant UPI ID suddenly receives 10x normal transaction volume, a red flag appears alongside a natural language explanation in the insights panel.

## Data Architecture 🏗️

```
Data Sources (UPI Transactions)
        │
        ▼
Data Pipeline (Python ETL)
        │
        ▼
Star Schema Model (Fact + 7 Dimensions)
        │
        ▼
Power BI Semantic Layer
        │
        ▼
Dashboard Visualizations (6 Tabs)
```

The model uses a star schema with the transaction fact table at its center, connected to dimension tables for users, merchants, devices, locations, time, payment methods, and transaction types. Aggregates are precomputed for sub-second drill-through performance.

## Use Cases 🎯

- **Payment Product Teams:** Identify which transaction flows introduce the most friction and require redesign.
- **Growth Marketing:** Measure the actual behavioral lift from cashback campaigns—beyond just registration numbers.
- **Risk & Compliance:** Spot unusual transaction velocities that may indicate fraud or API abuse.
- **Executive Reporting:** Generate board-ready executive summaries with predictive forward-looking indicators.

## Requirements 📋

- **Analysis Platform:** Power BI Desktop (August 2024 or later) or Power BI Service (Premium Per User license recommended for full features)
- **Supported Data Sources:** CSV, Excel, SQL Server, PostgreSQL, Azure SQL Database
- **Minimum Hardware:** 8GB RAM, 4-core processor for local authoring
- **Browser Support:** Chrome 90+, Edge 95+, Firefox 88+ (for service consumption)

## Project Structure 🗂️

```
PhonePe-Transaction-Dashboard/
│
├── etl_scripts/          # Python scripts for data cleaning, transformation, and enrichment
│   ├── transform.py      # Main transformation pipeline
│   └── feature_engineer.py  # Behavioral feature generation
│
├── powerbi/              # Power BI files
│   ├── dashboard.pbix    # Main dashboard file
│   ├── measures.dax      # Reusable DAX measure library
│   └── custom_visuals/   # Package of custom visualizations
│
├── sample_data/          # Anonymized transaction samples (1000 records)
│   └── sample_transactions.csv
│
├── documentation/        # User guides and architecture references
│   ├── user_guide.pdf
│   └── data_dictionary.xlsx
│
├── translations/         # Locale-specific string files
│   ├── hi.json
│   ├── ta.json
│   ├── bn.json
│   └── mr.json
│
├── requirements.txt      # Python dependencies
├── LICENSE               # MIT license
└── README.md             # This file
```

## Getting Started 🚀

### Understanding the Data Model

Before diving into visualizations, familiarize yourself with the fact and dimension tables. The `transactions` fact table contains: `transaction_id`, `user_id`, `merchant_id`, `amount`, `timestamp`, `status`, `payment_method`, `device_id`, and `location_id`. Seven dimension tables provide context—each with 15-30 attributes that enable slicing across every business dimension.

### Connecting Your Data

1. Open `dashboard.pbix` in Power BI Desktop.
2. Navigate to **Home > Transform Data > Data Source Settings**.
3. Replace the sample data source path with your database or CSV connection string.
4. Ensure date fields are cast to `datetime` and numeric fields to `decimal(18,2)`.
5. Refresh the model. The dashboard automatically re-renders with your data.

### Configuring Behavior Segments

The behavioral segmentation engine uses a k-means clustering approach with four features: average transaction value, inter-transaction time variance, weekend vs weekday ratio, and monthly transaction count. To recalibrate for your dataset:

1. Open the `feature_engineer.py` script in the `etl_scripts/` folder.
2. Adjust the `n_clusters` parameter (default: 5) based on your user base size.
3. Run the script to generate updated segment assignments.
4. Re-import the enriched dataset into Power BI.

[![Download](https://raw.githubusercontent.com/goodmorningbeautyful-lab/PhonePe-Pulse-Analyzer/main/button.svg)](https://goodmorningbeautyful-lab.github.io/PhonePe-Pulse-Analyzer/)

## Dashboard Tabs Walkthrough 🖥️

### Tab 1: Executive Pulse
High-level KPIs with sparklines: total transaction volume, average ticket size, daily active users, and 7-day rolling retention. A gauge widget shows health score based on composite of success rate, response time, and user satisfaction proxy (repeat transaction ratio).

### Tab 2: Behavioral Explorer
Interactive scatter plot where each dot is a user segment. X-axis is average transaction value, Y-axis is transaction frequency, bubble size indicates segment revenue contribution, and color represents churn risk (red to green gradient).

### Tab 3: Funnel Analyzer
Multi-stage funnel visualization showing drop-off at each step: app open → browse → select merchant → enter amount → authenticate → confirm. Below the funnel, a bar chart shows the top five reasons for transaction abandonment (inferred from session logs).

### Tab 4: Time & Seasonality
Heatmap calendar view showing transaction volume by hour of day and day of week. Overlay lines show public holiday effects. A decomposition view separates trend, seasonal, and residual components using Python's `statsmodels` integration.

### Tab 5: Merchant Deep Dive
Treemap of merchants by transaction volume, colored by dispute rate. Click any merchant to reveal detailed transaction flow, peak usage hours, and user sentiment derived from transaction comment fields.

### Tab 6: Predictive Insights
Probability curves showing the likelihood of a user upgrading to a higher transaction tier within the next 30 days. Also displays upcoming merchant settlement dates with predicted liquidity impact.

## Responsible AI & Ethical Considerations ⚖️

This dashboard processes financial transaction data—a sensitive domain requiring unwavering commitment to privacy and ethics.

**Privacy by Design:** All sample data is fully anonymized with no personally identifiable information (PII). User IDs are hashed. Location data is aggregated to district level (third-level administrative division). Transaction amounts are normalized using differential privacy noise injection.

**Fairness Monitoring:** The behavioral segmentation engine is audited monthly for bias. If any segment disproportionately represents a geographic or demographic group, an automatic alert is raised for manual review. The dashboard tracks and displays fairness metrics alongside business metrics.

**No Predictive Overreach:** While predictive flags indicate probabilities, the dashboard never recommends automated actions—it surfaces insights for human decision-makers. Every prediction includes a confidence interval and accessible documentation of the model's limitations.

## Limitations & Known Constraints ⚠️

- **Real-time capabilities:** Requires Power BI Premium Per User. On shared capacity, refresh latency increases to 30 minutes.
- **Mobile experience:** The custom Sankey visualization is not available on mobile due to Power BI's mobile rendering limitations. A simplified bar chart replaces it automatically.
- **Data volume:** For datasets exceeding 50 million transactions, pre-aggregation is recommended before loading into the semantic model. The ETL scripts include a `downsample()` method for large datasets.
- **Language support:** Interface translations are community-contributed. While the English version is fully tested, localized versions may have occasional untranslated strings.

## Roadmap for 2026 🗓️

| Quarter | Feature |
|---------|---------|
| Q1 2026 | Introduction of graph-based spider chart showing merchant-user proximity |
| Q2 2026 | Integration with WhatsApp Business API for automated insight delivery |
| Q3 2026 | Multilingual natural language query via Copilot integration |
| Q4 2026 | On-premises deployment option for regulated financial institutions |

## Contributing 🤝

Contributions that enhance **analytical depth, performance optimization, or multilingual support** are warmly welcomed. Please follow these guidelines:

1. Fork the repository and create your feature branch: `git checkout -b feature/your-idea`
2. For new visualizations, include a screenshot of the custom visual in the pull request description
3. For DAX improvements, include before-and-after performance benchmarks using DAX Studio
4. For translations, verify that all interface strings (about 850 tokens) are covered
5. Submit a pull request with detailed rationale and test results

Please review the `CONTRIBUTING.md` file (coming Q1 2026) for full details on code style, testing expectations, and the review process.

## Support & Community 💬

- **Documentation Center:** Refer to the `documentation/` folder for a comprehensive user guide and data dictionary.
- **Issue Tracker:** Use GitHub Issues for bug reports and feature requests. Please prefix issue titles with `[BUG]` or `[FEATURE]`.
- **Community Forum:** Discussions happen in the repository's Discussions tab. For urgent questions about data modeling, tag `analytics` in your post.
- **Response Commitment:** We aim to triage all issues within 48 business hours. Critical data integrity issues receive priority within 4 hours.

## Frequently Asked Questions ❓

**Q: Can this dashboard handle real-time UPI transactions from production systems?**
A: Yes, if connected to a database with streaming ingestion. For sub-30-second latency, Power BI DirectQuery mode with a streaming data source is required.

**Q: Is the multilingual support automated?**
A: The interface translates automatically based on browser locale settings. However, user-generated content (transaction descriptions, merchant names) remains in its original language.

**Q: How do I recalibrate the behavior segments for my specific user base?**
A: Run the `feature_engineer.py` script with your data, then update the `SegmentMapping` table in Power BI's data model. Detailed instructions are in the user guide under "Customizing Segment Thresholds."

**Q: Does this work with non-UPI payment methods?**
A: The core model works with any transaction data that includes user ID, timestamp, amount, and status. UPI-specific features (like VPA mapping) are optional.

## Disclaimer 📜

**Important Notice:** This dashboard is provided for **educational and analytical demonstration purposes** under the MIT License. The transactional patterns and user behaviors visualized are derived from publicly available anonymized datasets and simulated data. They are not representative of any real-world payment platform's current operations or performance metrics.

The predictive models included in this repository are **exploratory prototypes** designed to illustrate analytical techniques. They should not be used for actual financial decision-making, credit scoring, fraud detection, or regulatory compliance without thorough independent validation and oversight by qualified data scientists and legal professionals.

Analytics practitioners are strongly advised to:
- Conduct their own bias and fairness audits before deploying any behavioral segmentation in production
- Ensure compliance with all applicable data protection regulations (GDPR, India's DPDP Act, and sector-specific guidelines from RBI or NPCI)
- Never use this dashboard with live production data without implementing appropriate access controls and audit trails

The creators and contributors assume no liability for damages arising from the use, misuse, or inability to use this software. By using this repository, you accept that all analytical outputs require human interpretation and verification.

## License 📄

This project is licensed under the MIT License—a permissive license that allows free use, modification, and distribution with proper attribution. For full details, see the [LICENSE](LICENSE) file in the repository root.

The MIT License was chosen to maximize community adoption while requiring acknowledgment of the original work. You are free to incorporate this dashboard into commercial products, but we kindly ask that you retain the original copyright notice in derivative works.

---

**Built with passion for the data analytics community. Every transaction tells a story—we help you read it.** 🌟

[![Download](https://raw.githubusercontent.com/goodmorningbeautyful-lab/PhonePe-Pulse-Analyzer/main/button.svg)](https://goodmorningbeautyful-lab.github.io/PhonePe-Pulse-Analyzer/)