```json vega
{
  "$schema": "https://vega.github.io/schema/vega/v5.json",
  "description": "This is the central brain of the page",
  "signals": [
    {
      "name": "monthlyRevenue",
      "value": 25000
    },
    {
      "name": "rentBudget",
      "value": 4000
    },
    {
      "name": "staffBudget",
      "value": 8000
    },
    {
      "name": "equipmentBudget",
      "value": 2000
    },
    {
      "name": "suppliesBudget",
      "value": 1500
    },
    {
      "name": "insuranceBudget",
      "value": 1200
    },
    {
      "name": "marketingBudget",
      "value": 800
    },
    {
      "name": "utilitiesBudget",
      "value": 600
    },
    {
      "name": "maintenanceBudget",
      "value": 400
    },
    {
      "name": "savingsBudget",
      "value": 1000
    },
    {
      "name": "rentActual",
      "value": 4000
    },
    {
      "name": "staffActual",
      "value": 7800
    },
    {
      "name": "equipmentActual",
      "value": 1900
    },
    {
      "name": "suppliesActual",
      "value": 1450
    },
    {
      "name": "insuranceActual",
      "value": 1200
    },
    {
      "name": "marketingActual",
      "value": 750
    },
    {
      "name": "utilitiesActual",
      "value": 580
    },
    {
      "name": "maintenanceActual",
      "value": 380
    },
    {
      "name": "savingsActual",
      "value": 1000
    },
    {
      "name": "totalBudgeted",
      "update": "rentBudget + staffBudget + equipmentBudget + suppliesBudget + insuranceBudget + marketingBudget + utilitiesBudget + maintenanceBudget + savingsBudget"
    },
    {
      "name": "totalSpent",
      "update": "rentActual + staffActual + equipmentActual + suppliesActual + insuranceActual + marketingActual + utilitiesActual + maintenanceActual + savingsActual"
    },
    {
      "name": "totalRemaining",
      "update": "totalBudgeted - totalSpent"
    },
    {
      "name": "savingsRate",
      "update": "format((savingsBudget / monthlyRevenue) * 100, '.1f') + '%'"
    }
  ],
  "data": [
    {
      "name": "budgetCategories",
      "values": [
        {"category": "Rent", "budgeted": 4000, "spent": 4000, "color": "#0284c7"},
        {"category": "Staff", "budgeted": 8000, "spent": 7800, "color": "#0369a1"},
        {"category": "Equipment", "budgeted": 2000, "spent": 1900, "color": "#0891b2"},
        {"category": "Supplies", "budgeted": 1500, "spent": 1450, "color": "#06b6d4"},
        {"category": "Insurance", "budgeted": 1200, "spent": 1200, "color": "#0ea5e9"},
        {"category": "Marketing", "budgeted": 800, "spent": 750, "color": "#22d3ee"},
        {"category": "Utilities", "budgeted": 600, "spent": 580, "color": "#67e8f9"},
        {"category": "Maintenance", "budgeted": 400, "spent": 380, "color": "#a7f3d0"},
        {"category": "Savings", "budgeted": 1000, "spent": 1000, "color": "#10b981"}
      ],
      "transform": [
        {
          "type": "formula",
          "expr": "datum.category === 'Rent' ? rentBudget : (datum.category === 'Staff' ? staffBudget : (datum.category === 'Equipment' ? equipmentBudget : (datum.category === 'Supplies' ? suppliesBudget : (datum.category === 'Insurance' ? insuranceBudget : (datum.category === 'Marketing' ? marketingBudget : (datum.category === 'Utilities' ? utilitiesBudget : (datum.category === 'Maintenance' ? maintenanceBudget : (datum.category === 'Savings' ? savingsBudget : datum.budgeted))))))))",
          "as": "adjustedBudget"
        },
        {
          "type": "formula",
          "expr": "datum.adjustedBudget - datum.spent",
          "as": "remaining"
        },
        {
          "type": "formula",
          "expr": "(datum.spent - datum.adjustedBudget) / datum.adjustedBudget",
          "as": "spentPercentage"
        }
      ]
    },
    {
      "name": "monthlyTrends",
      "values": [
        {"month": "2024-01-01", "Rent": 4000, "Staff": 7500, "Equipment": 1800, "Supplies": 1400, "Insurance": 1200, "Marketing": 700, "Utilities": 550, "Maintenance": 350, "Savings": 1000},
        {"month": "2024-02-01", "Rent": 4000, "Staff": 7800, "Equipment": 1900, "Supplies": 1450, "Insurance": 1200, "Marketing": 750, "Utilities": 580, "Maintenance": 400, "Savings": 1000},
        {"month": "2024-03-01", "Rent": 4000, "Staff": 7600, "Equipment": 2000, "Supplies": 1500, "Insurance": 1200, "Marketing": 800, "Utilities": 600, "Maintenance": 380, "Savings": 1000},
        {"month": "2024-04-01", "Rent": 4000, "Staff": 7900, "Equipment": 1850, "Supplies": 1480, "Insurance": 1200, "Marketing": 780, "Utilities": 590, "Maintenance": 420, "Savings": 1000},
        {"month": "2024-05-01", "Rent": 4000, "Staff": 7700, "Equipment": 1950, "Supplies": 1520, "Insurance": 1200, "Marketing": 820, "Utilities": 570, "Maintenance": 360, "Savings": 1000},
        {"month": "2024-06-01", "Rent": 4000, "Staff": 7800, "Equipment": 1900, "Supplies": 1450, "Insurance": 1200, "Marketing": 750, "Utilities": 580, "Maintenance": 380, "Savings": 1000}
      ],
      "transform": [
        {
          "type": "fold",
          "fields": ["Rent", "Staff", "Equipment", "Supplies", "Insurance", "Marketing", "Utilities", "Maintenance", "Savings"],
          "as": ["category", "amount"]
        },
        {
          "type": "formula",
          "expr": "toDate(datum.month)",
          "as": "date"
        }
      ]
    },
    {
      "name": "budgetVarianceData",
      "source": "budgetCategories",
      "transform": [
        {
          "type": "formula",
          "expr": "datum.category === 'Rent' ? rentBudget : (datum.category === 'Staff' ? staffBudget : (datum.category === 'Equipment' ? equipmentBudget : (datum.category === 'Supplies' ? suppliesBudget : (datum.category === 'Insurance' ? insuranceBudget : (datum.category === 'Marketing' ? marketingBudget : (datum.category === 'Utilities' ? utilitiesBudget : (datum.category === 'Maintenance' ? maintenanceBudget : (datum.category === 'Savings' ? savingsBudget : datum.budgeted))))))))",
          "as": "budgeted"
        },
        {
          "type": "formula",
          "expr": "datum.category === 'Rent' ? rentActual : (datum.category === 'Staff' ? staffActual : (datum.category === 'Equipment' ? equipmentActual : (datum.category === 'Supplies' ? suppliesActual : (datum.category === 'Insurance' ? insuranceActual : (datum.category === 'Marketing' ? marketingActual : (datum.category === 'Utilities' ? utilitiesActual : (datum.category === 'Maintenance' ? maintenanceActual : (datum.category === 'Savings' ? savingsActual : datum.spent))))))))",
          "as": "spent"
        },
        {
          "type": "formula",
          "expr": "datum.spent - datum.budgeted",
          "as": "variance"
        }
      ]
    }
  ]
}
```

<style>
body { 
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
  margin: 0; 
  padding: 20px; 
  background: #f0f9ff; 
}

body { 
  display: grid; 
  grid-template-areas: 
    'header header' 
    'overview overview' 
    'allocation variance' 
    'controls categories' 
    'trends trends'; 
  grid-template-columns: 1fr 1fr; 
  gap: 20px; 
  max-width: 1400px; 
  margin: 0 auto; 
}

.group { 
  background: white; 
  padding: 20px; 
  border-radius: 12px; 
  box-shadow: 0 2px 8px rgba(0,0,0,0.1); 
  border: 1px solid #e2e8f0; 
}

#header { 
  grid-area: header; 
  background: linear-gradient(135deg, #0284c7 0%, #0369a1 100%); 
  color: white; 
  text-align: center; 
}

#overview { grid-area: overview; text-align: center; }
#allocation { grid-area: allocation; min-width: 0; overflow: hidden; }
#variance { grid-area: variance; min-width: 0; overflow: hidden; }
#controls { grid-area: controls; min-width: 0; overflow: hidden; }
#categories { grid-area: categories; min-width: 0; overflow: hidden; }
#trends { grid-area: trends; min-width: 0; overflow: hidden; }

h1 { 
  margin: 0; 
  padding: 20px 0; 
  font-size: 2em; 
  font-weight: 600; 
  font-family: 'Inter', sans-serif; 
}

h2 { 
  margin: 10px 0; 
  font-size: 2em; 
  color: #0369a1; 
  font-weight: 600; 
}

h3 { 
  margin: 0 0 15px 0; 
  font-size: 1.2em; 
  color: #0284c7; 
  font-weight: 500; 
  text-transform: uppercase; 
  letter-spacing: 0.5px; 
}

.tabulator { max-width: 100%; overflow: auto; }
.tabulator .tabulator-table { min-width: fit-content; }
.slider-container { margin: 15px 0; }
.slider-label { font-weight: 500; color: #2d3748; margin-bottom: 8px; display: block; }

@media (max-width: 768px) { 
  body { 
    grid-template-columns: 1fr; 
    grid-template-areas: 
      'header' 
      'overview' 
      'allocation' 
      'variance' 
      'controls' 
      'categories' 
      'trends'; 
  } 
}
</style>

:::: {#header .group}
# 🦷 Dental Clinic Budget Planner

**Interactive budget planning tool for your dental practice's financial wellness**
::::

:::: {#overview .group}
### 📊 Budget Overview

Monthly Revenue: {monthlyRevenue | range: 15000, 50000, 1000}

**Total Budgeted:** ${totalBudgeted | number}  
**Total Spent:** ${totalSpent | number}  
**Remaining Budget:** ${totalRemaining | number}  
**Savings Rate:** {savingsRate}
::::

:::: {#allocation .group}
### 🥧 Budget Allocation

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",
  "width": "container",
  "height": 300,
  "data": {"name": "budgetCategories"},
  "mark": {
    "type": "arc",
    "innerRadius": 50,
    "stroke": "white",
    "strokeWidth": 2
  },
  "encoding": {
    "theta": {
      "field": "adjustedBudget",
      "type": "quantitative",
      "title": "Budget Amount"
    },
    "color": {
      "field": "category",
      "type": "nominal",
      "scale": {
        "range": [
          "#0284c7", "#0369a1", "#0891b2", "#06b6d4", "#0ea5e9",
          "#22d3ee", "#67e8f9", "#a7f3d0", "#10b981"
        ]
      },
      "legend": {
        "orient": "right",
        "title": "Categories"
      }
    },
    "tooltip": [
      {"field": "category", "type": "nominal", "title": "Category"},
      {"field": "adjustedBudget", "type": "quantitative", "title": "Budgeted", "format": "$,.0f"},
      {"field": "spent", "type": "quantitative", "title": "Spent", "format": "$,.0f"},
      {"field": "remaining", "type": "quantitative", "title": "Remaining", "format": "$,.0f"}
    ]
  }
}
```
::::

:::: {#variance .group}
### 📊 Budget vs Actual

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",
  "description": "Budget variance bar chart with negative values. Shows budget vs actual spending differences.",
  "width": "container",
  "height": 300,
  "data": {"name": "budgetVarianceData"},
  "encoding": {
    "y": {
      "field": "category",
      "type": "nominal",
      "axis": {
        "domain": false,
        "ticks": false,
        "labelAngle": 0,
        "labelPadding": 4
      },
      "title": "Category"
    },
    "x": {
      "field": "variance",
      "type": "quantitative",
      "scale": {"padding": 20},
      "axis": {
        "gridColor": {
          "condition": {"test": "datum.value === 0", "value": "black"},
          "value": "#ddd"
        }
      },
      "title": "Variance (Actual - Budget)"
    }
  },
  "layer": [
    {
      "mark": "bar",
      "encoding": {
        "color": {
          "condition": {"test": "datum.variance < 0", "value": "#22c55e"},
          "value": "#ef4444"
        }
      }
    },
    {
      "mark": {
        "type": "text",
        "align": {"expr": "datum.variance < 0 ? 'right' : 'left'"},
        "dx": {"expr": "datum.variance < 0 ? -2 : 2"}
      },
      "encoding": {
        "text": {"field": "variance", "type": "quantitative", "format": "$,.0f"}
      }
    }
  ]
}
```
::::

:::: {#controls .group}
### 🏥 Budget Category Adjustments

Rent: {rentBudget | range: 2000, 8000, 200}

Staff: {staffBudget | range: 4000, 15000, 200}

Equipment: {equipmentBudget | range: 1000, 5000, 100}

Supplies: {suppliesBudget | range: 500, 3000, 50}

Insurance: {insuranceBudget | range: 500, 2500, 100}

Marketing: {marketingBudget | range: 200, 2000, 50}

Utilities: {utilitiesBudget | range: 300, 1500, 50}

Maintenance: {maintenanceBudget | range: 200, 1000, 50}

Savings: {savingsBudget | range: 500, 3000, 100}
::::

:::: {#categories .group}
### 📋 Track This Month's Spending

Rent Actual: {rentActual | number}

Staff Actual: {staffActual | number}

Equipment Actual: {equipmentActual | number}

Supplies Actual: {suppliesActual | number}

Insurance Actual: {insuranceActual | number}

Marketing Actual: {marketingActual | number}

Utilities Actual: {utilitiesActual | number}

Maintenance Actual: {maintenanceActual | number}

Savings Actual: {savingsActual | number}
::::

:::: {#trends .group}
### 📈 Spending Trends

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",
  "width": "container",
  "height": 300,
  "data": {"name": "monthlyTrends"},
  "mark": {
    "type": "line",
    "point": true,
    "strokeWidth": 2
  },
  "encoding": {
    "x": {
      "field": "date",
      "type": "temporal",
      "title": "Month",
      "axis": {"format": "%b %Y"}
    },
    "y": {
      "field": "amount",
      "type": "quantitative",
      "title": "Amount Spent ($)"
    },
    "color": {
      "field": "category",
      "type": "nominal",
      "scale": {
        "range": [
          "#0284c7", "#0369a1", "#0891b2", "#06b6d4", "#0ea5e9",
          "#22d3ee", "#67e8f9", "#a7f3d0", "#10b981"
        ]
      },
      "legend": {"title": "Category"}
    },
    "tooltip": [
      {"field": "date", "type": "temporal", "title": "Month", "format": "%B %Y"},
      {"field": "category", "type": "nominal", "title": "Category"},
      {"field": "amount", "type": "quantitative", "title": "Amount", "format": "$,.0f"}
    ]
  }
}
```
::::