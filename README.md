# Parks Canada Strategic Data Consultation Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/Status-Completed-success)

> A comprehensive Power BI solution designed for Parks Canada to enable data-driven decision-making across ecological health monitoring, visitor experience management, and conservation target tracking.

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Business Context](#business-context)
- [Key Features](#key-features)
- [Data Architecture](#data-architecture)
- [Technical Implementation](#technical-implementation)
- [Installation & Setup](#installation--setup)
- [Usage](#usage)
- [Key Insights & KPIs](#key-insights--kpis)
- [Project Structure](#project-structure)
- [Data Sources](#data-sources)
- [Future Enhancements](#future-enhancements)
- [About](#about)

---

## 🌲 Project Overview

**OH-DEER Data Consulting** developed this Power BI solution as part of Phase Two of the Parks Canada Strategic Data Consultation project. The dashboard consolidates data from 48 national parks and reserves across Canada to support three critical decision-making areas:

1. **Ecological Health & Threat Assessment** - Monitor vegetation health, invasive species, and endangered species across the park system
2. **Visitor Experience Management** - Optimize visitor satisfaction while managing facility utilization and minimizing ecological impact
3. **2030 Preservation Commitments** - Track progress toward Canada's land and marine conservation targets

This proof-of-concept demonstrates how unified data access can eliminate silos, enable real-time insights, and drive strategic resource allocation.

---

## 💼 Business Context

Parks Canada manages a vast portfolio of protected areas critical to preserving Canada's ecological and cultural heritage. Key challenges include:

- **Fragmented Data Systems** - Data scattered across multiple sources making comprehensive analysis difficult
- **Resource Allocation Decisions** - Need for data-driven insights to prioritize ecological restoration efforts
- **Conservation Targets** - Pressure to meet national and global biodiversity commitments by 2030
- **Visitor Management** - Balancing public access with ecological preservation at high-traffic locations

### Scope Change (March 3, 2025)

The original scope was adjusted due to:
- Delays in trail camera sensor network deployment (3600 thermal sensors postponed)
- Internal data audit revealing gaps in initially planned data sources
- Client request to focus on proof-of-concept with available data

**Current Focus Areas:**
- Ecological health monitoring across 48 parks
- Visitor experience and parking capacity analysis
- Progress tracking toward 2030 conservation commitments

---

## ✨ Key Features

### 1. Ecological Health Dashboard
- **Invasive Species Tracking** - Monitor purple loosestrife and non-native vegetation across multiple parks
- **Species Biodiversity Metrics** - Simpson's Index calculations for Odonata, Bank Swallows, and fish populations
- **Threat Assessment** - Real-time visibility into ecological threats requiring intervention
- **Data Accuracy KPIs** - Quality metrics ensuring reliable conservation decisions

### 2. Visitor Experience Analytics
- **Facility Utilization Rates** - Track campsite and trail usage against designed capacity
- **Net Promoter Score (NPS)** - Measure visitor satisfaction and loyalty
- **Traffic Flow Analysis** - Banff traffic data integration for congestion management
- **Seasonal Trends** - Identify peak visitation periods for resource planning

### 3. Conservation Progress Tracking
- **2030 Target Visualization** - Clear progress indicators toward national/global conservation commitments
- **Ecosystem Representation** - Track protected area coverage by ecosystem type
- **Cost Efficiency Metrics** - Monitor cost per hectare for new protected area establishment
- **Landscape Connectivity Scores** - Assess wildlife corridor effectiveness

---

## 🗄️ Data Architecture

### Data Model Design

The semantic model implements a **star schema** with:
- **37 dimension and fact tables** organized for optimal query performance
- **Relationships** defined between parks, species, visitor metrics, and temporal dimensions
- **DAX measures** calculating complex KPIs like Simpson's Index, NPS, and facility utilization rates
- **Expressions** for dynamic filtering and drill-through capabilities

### Key Tables Include:
- Park dimensions (location, size, type, regional grouping)
- Species biodiversity data (Odonata, Bank Swallow, fish populations)
- Invasive species monitoring (purple loosestrife, non-native vegetation)
- Visitor statistics (attendance, traffic, satisfaction scores)
- Conservation targets (protected area goals, ecosystem representation)

### Data Integration

Data sourced from:
- Parks Canada internal systems
- Open Canada datasets (14 CSV sources)
- Direct communications with Parks Canada personnel
- Natural Resources Canada climate/forestry data
- Traffic monitoring systems (Banff)

---

## 🛠️ Technical Implementation

### Built With
- **Power BI Desktop** - Primary development platform (PBIP format)
- **DAX (Data Analysis Expressions)** - Advanced calculations and KPIs
- **Power Query M** - Data transformation and preparation
- **TMDL (Tabular Model Definition Language)** - Model definition files

### Data Model Highlights

**Measures Created:**
```dax
Data Accuracy (%) = 
    DIVIDE(
        [Number of Correct Data Points],
        [Total Number of Data Points]
    ) * 100

Vegetation Health (%) = 
    DIVIDE(
        [Area of Healthy Vegetation],
        [Total Area Surveyed]
    ) * 100

Facility Utilization Rate (%) = 
    DIVIDE(
        [Actual Usage],
        [Designated Capacity]
    ) * 100

Net Promoter Score = 
    [% Promoters] - [% Detractors]

Simpson's Index of Diversity = 
    SUMX(
        Species,
        Species[Count] * (Species[Count] - 1)
    ) / ([Total Individuals] * ([Total Individuals] - 1))
```

### Performance Optimizations
- Aggregations for large datasets
- Calculated columns minimized in favor of measures
- Appropriate data types for reduced memory footprint
- Relationships leveraging directional filtering

---

## 📦 Installation & Setup

### Prerequisites
- Power BI Desktop (latest version recommended)
- Windows 10/11 or compatible OS
- Minimum 8GB RAM (16GB recommended for optimal performance)

### Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone https://github.com/yourusername/PBICapstone.git
   cd PBICapstone
   ```

2. **Open the Power BI Project**
   - Navigate to the project folder
   - Double-click `Capstone ParksCanada V8.pbip` to open in Power BI Desktop
   - The project will automatically reference the semantic model

3. **Data Refresh**
   - Data sources are pre-configured to CSV files in `Capstone Documentation/CapstoneDataSource/`
   - Click **Refresh** in Power BI Desktop to load the latest data
   - No credentials required for CSV sources

4. **Explore the Dashboard**
   - Navigate between report pages using tabs at the bottom
   - Use slicers and filters to drill into specific parks or time periods
   - Hover over visuals for tooltips and additional context

---

## 📊 Usage

### For Parks Canada Executives
- **Strategic Overview** - High-level KPIs on the main dashboard page
- **Drill-Through Analysis** - Right-click any data point to explore underlying details
- **Export Capabilities** - Export visualizations or underlying data for presentations

### For Lead Ecologists
- **Species-Level Detail** - Biodiversity metrics by park and species type
- **Threat Prioritization** - Visual indicators of areas requiring immediate intervention
- **Trend Analysis** - Historical data showing vegetation health over time

### For Operations Teams
- **Resource Allocation** - Facility utilization rates inform staffing and infrastructure decisions
- **Visitor Flow** - Traffic patterns support congestion management strategies
- **Seasonal Planning** - Historical trends guide preparation for peak periods

---

## 📈 Key Insights & KPIs

### Ecological Health Metrics
- **Data Accuracy**: Target >95% for decision-making confidence
- **Vegetation Health**: Percentage of healthy vegetation vs. total surveyed area
- **Invasive Species Control**: Tracking reductions in purple loosestrife and non-native vegetation
- **Simpson's Diversity Index**: Biodiversity measurement across parks (higher = more diverse)

### Visitor Experience Metrics
- **Facility Utilization Rate**: Optimize capacity without overcrowding (target 70-85%)
- **Net Promoter Score (NPS)**: Visitor satisfaction benchmark (industry standard >30 is "good")
- **Parking Availability**: Real-time tracking prevents visitor frustration at high-traffic locations

### Conservation Progress Metrics
- **Ecosystem Representation**: Percentage of each ecosystem type protected vs. total in Canada
- **Global Target Contribution**: Progress toward 30% land and water protection by 2030
- **Cost Per Hectare**: Financial efficiency in acquiring new protected areas

---

## 📁 Project Structure

```
PBICapstone/
│
├── Capstone Documentation/
│   ├── CapstoneDataSource/          # 14 CSV data files
│   └── PhaseTwo Report/             # Project documentation (.pdf, .docx)
│
├── Capstone ParksCanada V8.Report/
│   ├── .pbi/
│   │   └── localSettings.json
│   ├── StaticResources/
│   │   └── RegisteredResources/     # Images (.png, .svg)
│   ├── definition.pbir              # Report definition
│   └── report.json                  # Report layout and visuals
│
├── Capstone ParksCanada V8.SemanticModel/
│   ├── .pbi/
│   │   ├── cache.abf                # (gitignored)
│   │   ├── editorSettings.json      # (gitignored)
│   │   └── localSettings.json       # (gitignored)
│   ├── definition/
│   │   ├── cultures/
│   │   │   └── en-US.tmdl
│   │   ├── tables/                  # 37 table definitions (.tmdl)
│   │   ├── database.tmdl            # Database properties
│   │   ├── expressions.tmdl         # DAX expressions
│   │   ├── model.tmdl               # Model metadata
│   │   └── relationships.tmdl       # Table relationships
│   ├── definition.pbism             # Semantic model definition
│   └── diagramLayout.json           # Model diagram layout
│
├── .gitignore                       # Git ignore rules
├── Capstone ParksCanada V8.pbip     # Power BI Project file
└── README.md                        # This file
```

---

## 📚 Data Sources

This project integrates data from 17 authoritative sources:

1. **Direct Communications** - Parks Canada personnel (email/phone)
2. **Forest Non-Native Vegetation** - Kootenay & Yoho National Parks (Open Canada)
3. **Visitor Statistics** - Fundy National Park 2011-2014
4. **Climate & Forestry Data** - Natural Resources Canada
5. **Tourism Information** - New Brunswick Travel
6. **Conservation Reports** - Parks Canada CoRe Program (2023)
7. **Invasive Species Monitoring** - Purple Loosestrife (PEI National Park)
8. **Species at Risk** - SARA Public Registry
9. **Conservation Areas** - Land and Marine protected areas dataset
10. **Biodiversity Data** - PEI Odonata, Bank Swallow, Fish populations
11. **Traffic Data** - Town of Banff (2023)
12. **Visitor Data** - Banff National Park (Parks Canada email)
13. **Net Promoter Score** - Dummy data based on Banff annual report

Full citations available in Phase Two Report (see `/Capstone Documentation/PhaseTwo Report/`).

---

## 🚀 Future Enhancements - outline coming soon...

---

## 👥 About

**Project Team: OH-DEER Data Consulting**
- Taya
- Matt W.
- Josh
- William
- Matt Gillanders

**Client:** Parks Canada

**Project Timeline:**
- Phase One: Initial consultation and requirements gathering
- Phase Two: Data modeling and proof-of-concept development
- Scope Change: March 3, 2025
- Demo Presentation: April 17, 2025

**Technologies Used:**
- Power BI Desktop (PBIP format)
- DAX (Data Analysis Expressions)
- Power Query M

---

## 📄 License

This project was developed as part of an educational capstone project. Data sources are publicly available.

---

