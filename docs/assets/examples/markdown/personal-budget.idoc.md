```json vega```json vega

{{

  "$schema": "https://vega.github.io/schema/vega/v5.json",  "$schema": "https://vega.github.io/schema/vega/v5.json",

  "description": "This is the central brain of the page",  "description": "This is the central brain of the page",

  "signals": [  "signals": [

    {    {

      "name": "monthlyRevenue",      "name": "monthlyRevenue",

      "value": 25000      "value": 25000

    },    },

    {    {

      "name": "rentBudget",      "name": "rentBudget",

      "value": 4000      "value": 4000

    },    },

    {    {

      "name": "staffBudget",      "name": "staffBudget",

      "value": 8000      "value": 8000

    },    },

    {    {

      "name": "equipmentBudget",      "name": "equipmentBudget",

      "value": 2000      "value": 2000

    },    },

    {    {

      "name": "suppliesBudget",      "name": "suppliesBudget",

      "value": 1500      "value": 1500

    },    },

    {    {

      "name": "insuranceBudget",      "name": "insuranceBudget",

      "value": 1200      "value": 1200

    },    },

    {    {

      "name": "marketingBudget",      "name": "marketingBudget",

      "value": 800      "value": 800

    },    },

    {    {

      "name": "utilitiesBudget",      "name": "utilitiesBudget",

      "value": 600      "value": 600

    },    },

    {    {

      "name": "maintenanceBudget",      "name": "maintenanceBudget",

      "value": 400      "value": 400

    },    },

    {    {

      "name": "savingsBudget",      "name": "savingsBudget",

      "value": 1000      "value": 1000

    },    },

    {    {

      "name": "rentActual",      "name": "rentActual",

      "value": 4000      "value": 4000

    },    },

    {    {

      "name": "staffActual",      "name": "staffActual",

      "value": 7800      "value": 7800

    },    },

    {    {

      "name": "equipmentActual",      "name": "equipmentActual",

      "value": 1900      "value": 1900

    },    },

    {    {

      "name": "suppliesActual",      "name": "suppliesActual",

      "value": 1450      "value": 1450

    },    },

    {    {

      "name": "insuranceActual",      "name": "insuranceActual",

      "value": 1200      "value": 1200

    },    },

    {    {

      "name": "marketingActual",      "name": "marketingActual",

      "value": 750      "value": 750

    },    },

    {    {

      "name": "utilitiesActual",      "name": "utilitiesActual",

      "value": 580      "value": 580

    },    },

    {    {

      "name": "maintenanceActual",      "name": "maintenanceActual",

      "value": 380      "value": 380

    },    },

    {    {

      "name": "savingsActual",      "name": "savingsActual",

      "value": 1000      "value": 1000

    },    },

    {    {

      "name": "totalBudgeted",      "name": "totalBudgeted",

      "update": "rentBudget + staffBudget + equipmentBudget + suppliesBudget + insuranceBudget + marketingBudget + utilitiesBudget + maintenanceBudget + savingsBudget"      "update": "rentBudget + staffBudget + equipmentBudget + suppliesBudget + insuranceBudget + marketingBudget + utilitiesBudget + maintenanceBudget + savingsBudget"

    },    },

    {    {

      "name": "totalSpent",      "name": "totalSpent",

      "update": "rentActual + staffActual + equipmentActual + suppliesActual + insuranceActual + marketingActual + utilitiesActual + maintenanceActual + savingsActual"      "update": "rentActual + staffActual + equipmentActual + suppliesActual + insuranceActual + marketingActual + utilitiesActual + maintenanceActual + savingsActual"

    },    },

    {    {

      "name": "totalRemaining",      "name": "totalRemaining",

      "update": "totalBudgeted - totalSpent"      "update": "totalBudgeted - totalSpent"

    },    },

    {    {

      "name": "savingsRate",      "name": "savingsRate",

      "update": "format((savingsBudget / monthlyRevenue) * 100, '.1f') + '%'"      "update": "format((savingsBudget / monthlyRevenue) * 100, '.1f') + '%'"

    }    }

  ],  ],

  "data": [    {

    {      "name": "foodActual",

      "name": "budgetCategories",      "value": 650

      "values": [    },

        {"category": "Rent", "budgeted": 4000, "spent": 4000, "color": "#0284c7"},    {

        {"category": "Staff", "budgeted": 8000, "spent": 7800, "color": "#0369a1"},      "name": "transportationActual",

        {"category": "Equipment", "budgeted": 2000, "spent": 1900, "color": "#0891b2"},      "value": 380

        {"category": "Supplies", "budgeted": 1500, "spent": 1450, "color": "#06b6d4"},    },

        {"category": "Insurance", "budgeted": 1200, "spent": 1200, "color": "#0ea5e9"},    {

        {"category": "Marketing", "budgeted": 800, "spent": 750, "color": "#22d3ee"},      "name": "entertainmentActual",

        {"category": "Utilities", "budgeted": 600, "spent": 580, "color": "#67e8f9"},      "value": 280

        {"category": "Maintenance", "budgeted": 400, "spent": 380, "color": "#a7f3d0"},    },

        {"category": "Savings", "budgeted": 1000, "spent": 1000, "color": "#10b981"}    {

      ],      "name": "savingsActual",

      "transform": [      "value": 800

        {    },

          "type": "formula",    {

          "expr": "datum.category === 'Rent' ? rentBudget : (datum.category === 'Staff' ? staffBudget : (datum.category === 'Equipment' ? equipmentBudget : (datum.category === 'Supplies' ? suppliesBudget : (datum.category === 'Insurance' ? insuranceBudget : (datum.category === 'Marketing' ? marketingBudget : (datum.category === 'Utilities' ? utilitiesBudget : (datum.category === 'Maintenance' ? maintenanceBudget : (datum.category === 'Savings' ? savingsBudget : datum.budgeted))))))))",      "name": "healthcareActual",

          "as": "adjustedBudget"      "value": 200

        },    },

        {    {

          "type": "formula",      "name": "utilitiesActual",

          "expr": "datum.adjustedBudget - datum.spent",      "value": 180

          "as": "remaining"    },

        },    {

        {      "name": "clothingActual",

          "type": "formula",      "value": 120

          "expr": "(datum.spent - datum.adjustedBudget) / datum.adjustedBudget",    },

          "as": "spentPercentage"    {

        }      "name": "personalCareActual",

      ]      "value": 90

    },    },

    {    {

      "name": "monthlyTrends",      "name": "adjustedBudgetData",

      "values": [      "update": "data('adjustedBudgetData')"

        {"month": "2024-01-01", "Rent": 4000, "Staff": 7500, "Equipment": 1800, "Supplies": 1400, "Insurance": 1200, "Marketing": 700, "Utilities": 550, "Maintenance": 350, "Savings": 1000},    },

        {"month": "2024-02-01", "Rent": 4000, "Staff": 7800, "Equipment": 1900, "Supplies": 1450, "Insurance": 1200, "Marketing": 750, "Utilities": 580, "Maintenance": 400, "Savings": 1000},    {

        {"month": "2024-03-01", "Rent": 4000, "Staff": 7600, "Equipment": 2000, "Supplies": 1500, "Insurance": 1200, "Marketing": 800, "Utilities": 600, "Maintenance": 380, "Savings": 1000},      "name": "monthlyTrendsLong",

        {"month": "2024-04-01", "Rent": 4000, "Staff": 7900, "Equipment": 1850, "Supplies": 1480, "Insurance": 1200, "Marketing": 780, "Utilities": 590, "Maintenance": 420, "Savings": 1000},      "update": "data('monthlyTrendsLong')"

        {"month": "2024-05-01", "Rent": 4000, "Staff": 7700, "Equipment": 1950, "Supplies": 1520, "Insurance": 1200, "Marketing": 820, "Utilities": 570, "Maintenance": 360, "Savings": 1000},    },

        {"month": "2024-06-01", "Rent": 4000, "Staff": 7800, "Equipment": 1900, "Supplies": 1450, "Insurance": 1200, "Marketing": 750, "Utilities": 580, "Maintenance": 380, "Savings": 1000}    {

      ],      "name": "budgetVarianceData",

      "transform": [      "update": "data('budgetVarianceData')"

        {    },

          "type": "fold",    {

          "fields": ["Rent", "Staff", "Equipment", "Supplies", "Insurance", "Marketing", "Utilities", "Maintenance", "Savings"],      "name": "savingsRate",

          "as": ["category", "amount"]      "value": "0%",

        },      "update": "format((savingsBudget / monthlyIncome) * 100, '.1f') + '%'"

        {    },

          "type": "formula",    {

          "expr": "toDate(datum.month)",      "name": "totalBudgeted",

          "as": "date"      "value": 0,

        }      "update": "toNumber(housingBudget) + toNumber(foodBudget) + toNumber(transportationBudget) + toNumber(entertainmentBudget) + toNumber(savingsBudget) + toNumber(healthcareBudget) + toNumber(utilitiesBudget) + toNumber(clothingBudget) + toNumber(personalCareBudget)"

      ]    },

    },    {

    {      "name": "totalSpent",

      "name": "budgetVarianceData",      "value": 0,

      "source": "budgetCategories",      "update": "toNumber(housingActual) + toNumber(foodActual) + toNumber(transportationActual) + toNumber(entertainmentActual) + toNumber(savingsActual) + toNumber(healthcareActual) + toNumber(utilitiesActual) + toNumber(clothingActual) + toNumber(personalCareActual)"

      "transform": [    },

        {    {

          "type": "formula",      "name": "totalRemaining",

          "expr": "datum.category === 'Rent' ? rentBudget : (datum.category === 'Staff' ? staffBudget : (datum.category === 'Equipment' ? equipmentBudget : (datum.category === 'Supplies' ? suppliesBudget : (datum.category === 'Insurance' ? insuranceBudget : (datum.category === 'Marketing' ? marketingBudget : (datum.category === 'Utilities' ? utilitiesBudget : (datum.category === 'Maintenance' ? maintenanceBudget : (datum.category === 'Savings' ? savingsBudget : datum.budgeted))))))))",      "value": 0,

          "as": "budgeted"      "update": "toNumber(totalBudgeted) - toNumber(totalSpent)"

        },    },

        {    {

          "type": "formula",      "name": "budgetCategories",

          "expr": "datum.category === 'Rent' ? rentActual : (datum.category === 'Staff' ? staffActual : (datum.category === 'Equipment' ? equipmentActual : (datum.category === 'Supplies' ? suppliesActual : (datum.category === 'Insurance' ? insuranceActual : (datum.category === 'Marketing' ? marketingActual : (datum.category === 'Utilities' ? utilitiesActual : (datum.category === 'Maintenance' ? maintenanceActual : (datum.category === 'Savings' ? savingsActual : datum.spent))))))))",      "update": "data('budgetCategories')"

          "as": "spent"    },

        },    {

        {      "name": "monthlyTrends",

          "type": "formula",      "update": "data('monthlyTrends')"

          "expr": "datum.spent - datum.budgeted",    }

          "as": "variance"  ],

        }  "data": [

      ]    {

    }      "name": "monthlyTrends",

  ]      "values": []

}    },

```    {

      "name": "budgetCategories",

<style>      "values": []

body {     },

  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;     {

  margin: 0;       "name": "adjustedBudgetData",

  padding: 20px;       "source": [

  background: #f0f9ff;         "budgetCategories"

}      ],

      "transform": [

body {         {

  display: grid;           "type": "formula",

  grid-template-areas:           "expr": "datum.category === 'Housing' ? housingBudget : (datum.category === 'Food' ? foodBudget : (datum.category === 'Transportation' ? transportationBudget : (datum.category === 'Entertainment' ? entertainmentBudget : (datum.category === 'Savings' ? savingsBudget : (datum.category === 'Healthcare' ? healthcareBudget : (datum.category === 'Utilities' ? utilitiesBudget : (datum.category === 'Clothing' ? clothingBudget : (datum.category === 'Personal Care' ? personalCareBudget : datum.budgeted))))))))",

    'header header'           "as": "adjustedBudget"

    'overview overview'         },

    'allocation variance'         {

    'controls categories'           "type": "formula",

    'trends trends';           "expr": "datum.adjustedBudget - datum.spent",

  grid-template-columns: 1fr 1fr;           "as": "remaining"

  gap: 20px;         },

  max-width: 1400px;         {

  margin: 0 auto;           "type": "formula",

}          "expr": "(datum.spent - datum.adjustedBudget) / datum.adjustedBudget",

          "as": "spentPercentage"

.group {         }

  background: white;       ]

  padding: 20px;     },

  border-radius: 12px;     {

  box-shadow: 0 2px 8px rgba(0,0,0,0.1);       "name": "monthlyTrendsLong",

  border: 1px solid #e2e8f0;       "source": [

}        "monthlyTrends"

      ],

#header {       "transform": [

  grid-area: header;         {

  background: linear-gradient(135deg, #0284c7 0%, #0369a1 100%);           "type": "fold",

  color: white;           "fields": [

  text-align: center;             "Housing",

}            "Food",

            "Transportation",

#overview { grid-area: overview; text-align: center; }            "Entertainment",

#allocation { grid-area: allocation; min-width: 0; overflow: hidden; }            "Healthcare",

#variance { grid-area: variance; min-width: 0; overflow: hidden; }            "Savings",

#controls { grid-area: controls; min-width: 0; overflow: hidden; }            "Utilities",

#categories { grid-area: categories; min-width: 0; overflow: hidden; }            "Clothing",

#trends { grid-area: trends; min-width: 0; overflow: hidden; }            "Personal Care"

          ],

h1 {           "as": [

  margin: 0;             "category",

  padding: 20px 0;             "amount"

  font-size: 2em;           ]

  font-weight: 600;         }

  font-family: 'Inter', sans-serif;       ]

}    },

    {

h2 {       "name": "budgetVarianceData",

  margin: 10px 0;       "source": [

  font-size: 2em;         "budgetCategories"

  color: #0369a1;       ],

  font-weight: 600;       "transform": [

}        {

          "type": "filter",

h3 {           "expr": "datum.category === 'Housing' || datum.category === 'Food' || datum.category === 'Transportation' || datum.category === 'Entertainment' || datum.category === 'Healthcare' || datum.category === 'Savings' || datum.category === 'Utilities' || datum.category === 'Clothing' || datum.category === 'Personal Care'"

  margin: 0 0 15px 0;         },

  font-size: 1.2em;         {

  color: #0284c7;           "type": "formula",

  font-weight: 500;           "expr": "datum.category === 'Housing' ? housingBudget : (datum.category === 'Food' ? foodBudget : (datum.category === 'Transportation' ? transportationBudget : (datum.category === 'Entertainment' ? entertainmentBudget : (datum.category === 'Healthcare' ? healthcareBudget : (datum.category === 'Savings' ? savingsBudget : (datum.category === 'Utilities' ? utilitiesBudget : (datum.category === 'Clothing' ? clothingBudget : (datum.category === 'Personal Care' ? personalCareBudget : datum.budgeted))))))))",

  text-transform: uppercase;           "as": "budgeted"

  letter-spacing: 0.5px;         },

}        {

          "type": "formula",

.tabulator { max-width: 100%; overflow: auto; }          "expr": "datum.category === 'Housing' ? housingActual : (datum.category === 'Food' ? foodActual : (datum.category === 'Transportation' ? transportationActual : (datum.category === 'Entertainment' ? entertainmentActual : (datum.category === 'Healthcare' ? healthcareActual : (datum.category === 'Savings' ? savingsActual : (datum.category === 'Utilities' ? utilitiesActual : (datum.category === 'Clothing' ? clothingActual : (datum.category === 'Personal Care' ? personalCareActual : datum.spent))))))))",

.tabulator .tabulator-table { min-width: fit-content; }          "as": "spent"

.slider-container { margin: 15px 0; }        },

.slider-label { font-weight: 500; color: #2d3748; margin-bottom: 8px; display: block; }        {

          "type": "formula",

@media (max-width: 768px) {           "expr": "datum.spent - datum.budgeted",

  body {           "as": "variance"

    grid-template-columns: 1fr;         }

    grid-template-areas:       ]

      'header'     }

      'overview'   ]

      'allocation' }

      'variance' ```

      'controls' 

      'categories' 

      'trends'; ```css

  } body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 0; padding: 20px; background: #f8fafc; }

}body { display: grid; grid-template-areas: 'header header' 'overview overview' 'allocation variance' 'controls categories' 'trends trends'; grid-template-columns: 1fr 1fr; gap: 20px; max-width: 1400px; margin: 0 auto; }

</style>.group { background: white; padding: 20px; border-radius: 12px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); border: 1px solid #e2e8f0; }

#header { grid-area: header; background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; text-align: center; }

:::: {#header .group}#overview { grid-area: overview; text-align: center; }

# 🦷 Dental Clinic Budget Planner#allocation { grid-area: allocation; min-width: 0; overflow: hidden; }

#variance { grid-area: variance; min-width: 0; overflow: hidden; }

**Interactive budget planning tool for your dental practice's financial wellness**#controls { grid-area: controls; min-width: 0; overflow: hidden; }

::::#categories { grid-area: categories; min-width: 0; overflow: hidden; }

#trends { grid-area: trends; min-width: 0; overflow: hidden; }

:::: {#overview .group}h1 { margin: 0; padding: 20px 0; font-size: 2em; font-weight: 600; }

### 📊 Budget Overviewh2 { margin: 10px 0; font-size: 2em; color: #2d3748; font-weight: 600; }

h3 { margin: 0 0 15px 0; font-size: 1.2em; color: #4a5568; font-weight: 500; text-transform: uppercase; letter-spacing: 0.5px; }

Monthly Revenue: {monthlyRevenue | range: 15000, 50000, 1000}.tabulator { max-width: 100%; overflow: auto; }

.tabulator .tabulator-table { min-width: fit-content; }

**Total Budgeted:** ${totalBudgeted | number}  .slider-container { margin: 15px 0; }

**Total Spent:** ${totalSpent | number}  .slider-label { font-weight: 500; color: #2d3748; margin-bottom: 8px; display: block; }

**Remaining Budget:** ${totalRemaining | number}  @media (max-width: 768px) { body { grid-template-columns: 1fr; grid-template-areas: 'header' 'overview' 'allocation' 'variance' 'controls' 'categories' 'trends'; } }

**Savings Rate:** {savingsRate}```

::::



:::: {#allocation .group}::: group {#header}

### 🥧 Budget Allocation

# 💰 Personal Budget Planner

```vega-lite**Interactive budget planning tool for financial wellness**

{:::

  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",::: group {#overview}

  "width": "container",

  "height": 300,### 📊 Budget Overview

  "data": {"name": "budgetCategories"},

  "mark": {

    "type": "arc",```yaml slider

    "innerRadius": 50,variableId: monthlyIncome

    "stroke": "white",value: 5500

    "strokeWidth": 2label: Monthly Income

  },min: 3000

  "encoding": {max: 10000

    "theta": {step: 250

      "field": "adjustedBudget",```

      "type": "quantitative",

      "title": "Budget Amount"

    },**Total Budgeted:** ${{totalBudgeted}}

    "color": {**Total Spent:** ${{totalSpent}}

      "field": "category",**Remaining Budget:** ${{totalRemaining}}

      "type": "nominal",**Savings Rate:** {{savingsRate}}

      "scale": {:::

        "range": [::: group {#allocation}

          "#0284c7", "#0369a1", "#0891b2", "#06b6d4", "#0ea5e9",

          "#22d3ee", "#67e8f9", "#a7f3d0", "#10b981"### 🥧 Budget Allocation

        ]

      },

      "legend": {```json vega-lite

        "orient": "right",{

        "title": "Categories"  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",

      }  "width": "container",

    },  "height": 300,

    "tooltip": [  "data": {

      {"field": "category", "type": "nominal", "title": "Category"},    "name": "adjustedBudgetData"

      {"field": "adjustedBudget", "type": "quantitative", "title": "Budgeted", "format": "$,.0f"},  },

      {"field": "spent", "type": "quantitative", "title": "Spent", "format": "$,.0f"},  "mark": {

      {"field": "remaining", "type": "quantitative", "title": "Remaining", "format": "$,.0f"}    "type": "arc",

    ]    "innerRadius": 50,

  }    "stroke": "white",

}    "strokeWidth": 2

```  },

::::  "encoding": {

    "theta": {

:::: {#variance .group}      "field": "adjustedBudget",

### 📊 Budget vs Actual      "type": "quantitative",

      "title": "Budget Amount"

```vega-lite    },

{    "color": {

  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",      "field": "category",

  "description": "Budget variance bar chart with negative values. Shows budget vs actual spending differences.",      "type": "nominal",

  "width": "container",      "scale": {

  "height": 300,        "range": [

  "data": {"name": "budgetVarianceData"},          "#667eea",

  "encoding": {          "#764ba2",

    "y": {          "#f093fb",

      "field": "category",          "#4ecdc4",

      "type": "nominal",          "#45b7d1",

      "axis": {          "#96ceb4",

        "domain": false,          "#feca57",

        "ticks": false,          "#ff9ff3",

        "labelAngle": 0,          "#54a0ff"

        "labelPadding": 4        ]

      },      },

      "title": "Category"      "legend": {

    },        "orient": "right",

    "x": {        "title": "Categories"

      "field": "variance",      }

      "type": "quantitative",    },

      "scale": {"padding": 20},    "tooltip": [

      "axis": {      {

        "gridColor": {        "field": "category",

          "condition": {"test": "datum.value === 0", "value": "black"},        "type": "nominal",

          "value": "#ddd"        "title": "Category"

        }      },

      },      {

      "title": "Variance (Actual - Budget)"        "field": "adjustedBudget",

    }        "type": "quantitative",

  },        "title": "Budgeted",

  "layer": [        "format": "$,.0f"

    {      },

      "mark": "bar",      {

      "encoding": {        "field": "spent",

        "color": {        "type": "quantitative",

          "condition": {"test": "datum.variance < 0", "value": "#22c55e"},        "title": "Spent",

          "value": "#ef4444"        "format": "$,.0f"

        }      },

      }      {

    },        "field": "remaining",

    {        "type": "quantitative",

      "mark": {        "title": "Remaining",

        "type": "text",        "format": "$,.0f"

        "align": {"expr": "datum.variance < 0 ? 'right' : 'left'"},      }

        "dx": {"expr": "datum.variance < 0 ? -2 : 2"}    ]

      },  }

      "encoding": {}

        "text": {"field": "variance", "type": "quantitative", "format": "$,.0f"}```

      }

    }

  ]:::

}::: group {#variance}

```

::::### 📊 Budget vs Actual



:::: {#controls .group}

### 🏥 Budget Category Adjustments```json vega-lite

{

Rent: {rentBudget | range: 2000, 8000, 200}  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",

  "description": "Budget variance bar chart with negative values. Shows budget vs actual spending differences.",

Staff: {staffBudget | range: 4000, 15000, 200}  "width": "container",

  "height": 300,

Equipment: {equipmentBudget | range: 1000, 5000, 100}  "data": {

    "name": "budgetVarianceData"

Supplies: {suppliesBudget | range: 500, 3000, 50}  },

  "encoding": {

Insurance: {insuranceBudget | range: 500, 2500, 100}    "y": {

      "field": "category",

Marketing: {marketingBudget | range: 200, 2000, 50}      "type": "nominal",

      "axis": {

Utilities: {utilitiesBudget | range: 300, 1500, 50}        "domain": false,

        "ticks": false,

Maintenance: {maintenanceBudget | range: 200, 1000, 50}        "labelAngle": 0,

        "labelPadding": 4

Savings: {savingsBudget | range: 500, 3000, 100}      },

::::      "title": "Category"

    },

:::: {#categories .group}    "x": {

### 📋 Track This Month's Spending      "field": "variance",

      "type": "quantitative",

Rent Actual: {rentActual | number}      "scale": {

        "padding": 20

Staff Actual: {staffActual | number}      },

      "axis": {

Equipment Actual: {equipmentActual | number}        "gridColor": {

          "condition": {

Supplies Actual: {suppliesActual | number}            "test": "datum.value === 0",

            "value": "black"

Insurance Actual: {insuranceActual | number}          },

          "value": "#ddd"

Marketing Actual: {marketingActual | number}        }

      },

Utilities Actual: {utilitiesActual | number}      "title": "Variance (Actual - Budget)"

    }

Maintenance Actual: {maintenanceActual | number}  },

  "layer": [

Savings Actual: {savingsActual | number}    {

::::      "mark": "bar",

      "encoding": {

:::: {#trends .group}        "color": {

### 📈 Spending Trends          "condition": {

            "test": "datum.variance < 0",

```vega-lite            "value": "#22c55e"

{          },

  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",          "value": "#ef4444"

  "width": "container",        }

  "height": 300,      }

  "data": {"name": "monthlyTrends"},    },

  "mark": {    {

    "type": "line",      "mark": {

    "point": true,        "type": "text",

    "strokeWidth": 2        "align": {

  },          "expr": "datum.variance < 0 ? 'right' : 'left'"

  "encoding": {        },

    "x": {        "dx": {

      "field": "date",          "expr": "datum.variance < 0 ? -2 : 2"

      "type": "temporal",        }

      "title": "Month",      },

      "axis": {"format": "%b %Y"}      "encoding": {

    },        "text": {

    "y": {          "field": "variance",

      "field": "amount",          "type": "quantitative",

      "type": "quantitative",          "format": "$,.0f"

      "title": "Amount Spent ($)"        }

    },      }

    "color": {    }

      "field": "category",  ]

      "type": "nominal",}

      "scale": {```

        "range": [

          "#0284c7", "#0369a1", "#0891b2", "#06b6d4", "#0ea5e9",

          "#22d3ee", "#67e8f9", "#a7f3d0", "#10b981":::

        ]::: group {#controls}

      },

      "legend": {"title": "Category"}### 🏠 Budget Category Adjustments

    },

    "tooltip": [

      {"field": "date", "type": "temporal", "title": "Month", "format": "%B %Y"},```yaml slider

      {"field": "category", "type": "nominal", "title": "Category"},variableId: housingBudget

      {"field": "amount", "type": "quantitative", "title": "Amount", "format": "$,.0f"}value: 2000

    ]label: Housing

  }min: 800

}max: 4000

```step: 50

::::```


```yaml slider
variableId: foodBudget
value: 600
label: Food
min: 200
max: 1200
step: 25
```


```yaml slider
variableId: transportationBudget
value: 400
label: Transportation
min: 100
max: 800
step: 25
```


```yaml slider
variableId: entertainmentBudget
value: 300
label: Entertainment
min: 50
max: 600
step: 25
```


```yaml slider
variableId: savingsBudget
value: 800
label: Savings
min: 200
max: 2000
step: 50
```


```yaml slider
variableId: healthcareBudget
value: 250
label: Healthcare
min: 100
max: 500
step: 25
```


```yaml slider
variableId: utilitiesBudget
value: 200
label: Utilities
min: 100
max: 400
step: 25
```


```yaml slider
variableId: clothingBudget
value: 150
label: Clothing
min: 50
max: 300
step: 25
```


```yaml slider
variableId: personalCareBudget
value: 100
label: Personal Care
min: 25
max: 200
step: 25
```


:::
::: group {#categories}

### 📋 Track This Month's Spending


```yaml number
variableId: housingActual
value: 1950
label: Housing Actual
```


```yaml number
variableId: foodActual
value: 650
label: Food Actual
```


```yaml number
variableId: transportationActual
value: 380
label: Transportation Actual
```


```yaml number
variableId: entertainmentActual
value: 280
label: Entertainment Actual
```


```yaml number
variableId: healthcareActual
value: 200
label: Healthcare Actual
```


```yaml number
variableId: savingsActual
value: 800
label: Savings Actual
```


```yaml number
variableId: utilitiesActual
value: 180
label: Utilities Actual
```


```yaml number
variableId: clothingActual
value: 120
label: Clothing Actual
```


```yaml number
variableId: personalCareActual
value: 90
label: Personal Care Actual
```


:::
::: group {#trends}

### 📈 Spending Trends


```json vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v6.json",
  "width": "container",
  "height": 300,
  "data": {
    "name": "monthlyTrendsLong"
  },
  "mark": {
    "type": "line",
    "point": true,
    "strokeWidth": 2
  },
  "encoding": {
    "x": {
      "field": "month",
      "type": "temporal",
      "title": "Month",
      "axis": {
        "format": "%b %Y"
      }
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
          "#667eea",
          "#764ba2",
          "#f093fb",
          "#4ecdc4",
          "#45b7d1",
          "#96ceb4",
          "#feca57",
          "#ff9ff3",
          "#54a0ff"
        ]
      },
      "legend": {
        "title": "Category"
      }
    },
    "tooltip": [
      {
        "field": "month",
        "type": "temporal",
        "title": "Month",
        "format": "%B %Y"
      },
      {
        "field": "category",
        "type": "nominal",
        "title": "Category"
      },
      {
        "field": "amount",
        "type": "quantitative",
        "title": "Amount",
        "format": "$,.0f"
      }
    ]
  }
}
```


:::


```csv budgetCategories
category,budgeted,spent,color
Housing,2000,1950,#667eea
Food,600,650,#764ba2
Transportation,400,380,#f093fb
Entertainment,300,280,#4ecdc4
Healthcare,250,200,#45b7d1
Savings,800,800,#96ceb4
Utilities,200,180,#feca57
Clothing,150,120,#ff9ff3
Personal Care,100,90,#54a0ff
```


```csv monthlyTrends
month,Housing,Food,Transportation,Entertainment,Healthcare,Savings,Utilities,Clothing,Personal Care
2024-01,1980,620,390,250,180,800,190,100,80
2024-02,1950,580,370,320,220,800,175,150,95
2024-03,1950,640,400,280,160,800,185,80,85
2024-04,1950,610,420,300,240,800,170,200,110
2024-05,1950,650,380,280,200,800,180,120,90
2024-06,1950,680,350,350,190,800,160,180,100
```