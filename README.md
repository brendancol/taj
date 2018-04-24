Tables As JSON
-------


#### Simple Tables
```json
{
  "schema": {
    "fields": [
      {
        "name": "index",
        "type": "integer"
      },
      {
        "name": "sepal_length",
        "type": "number"
      },
      {
        "name": "sepal_width",
        "type": "number"
      },
      {
        "name": "petal_length",
        "type": "number"
      },
      {
        "name": "petal_width",
        "type": "number"
      },
      {
        "name": "species",
        "type": "string"
      }
    ],
    "primaryKey": [
      "index"
    ]
  },
  "data": {
    "sepal_length": {
      "0": 5.1,
      "1": 4.9,
      "2": 4.7,
      "3": 4.6,
      "4": 5
    },
    "sepal_width": {
      "0": 3.5,
      "1": 3,
      "2": 3.2,
      "3": 3.1,
      "4": 3.6
    },
    "petal_length": {
      "0": 1.4,
      "1": 1.4,
      "2": 1.3,
      "3": 1.5,
      "4": 1.4
    },
    "petal_width": {
      "0": 0.2,
      "1": 0.2,
      "2": 0.2,
      "3": 0.2,
      "4": 0.2
    },
    "species": {
      "0": "setosa",
      "1": "setosa",
      "2": "setosa",
      "3": "setosa",
      "4": "setosa"
    }
  },
  "tableType": "Simple"
}
```


#### Nested Columns
```json
{
  "columns": [
    [
      "sepal_length",
      "min"
    ],
    [
      "sepal_length",
      "max"
    ],
    [
      "sepal_length",
      "mean"
    ],
    [
      "sepal_width",
      "min"
    ],
    [
      "sepal_width",
      "max"
    ],
    [
      "sepal_width",
      "mean"
    ],
    [
      "petal_length",
      "min"
    ],
    [
      "petal_length",
      "max"
    ],
    [
      "petal_length",
      "mean"
    ],
    [
      "petal_width",
      "min"
    ],
    [
      "petal_width",
      "max"
    ],
    [
      "petal_width",
      "mean"
    ]
  ],
  "index": [
    "setosa",
    "versicolor",
    "virginica"
  ],
  "data": [
    [
      4.3,
      5.8,
      5.006,
      2.3,
      4.4,
      3.428,
      1,
      1.9,
      1.462,
      0.1,
      0.6,
      0.246
    ],
    [
      4.9,
      7,
      5.936,
      2,
      3.4,
      2.77,
      3,
      5.1,
      4.26,
      1,
      1.8,
      1.326
    ],
    [
      4.9,
      7.9,
      6.588,
      2.2,
      3.8,
      2.974,
      4.5,
      6.9,
      5.552,
      1.4,
      2.5,
      2.026
    ]
  ],
  "index_field": "species",
  "tableType": "MultiIndex"
}
```


#### Nested Columns and Rows:
```json
{
  "columns": [
    [
      "sepal_length",
      "min"
    ],
    [
      "sepal_length",
      "max"
    ],
    [
      "sepal_width",
      "min"
    ],
    [
      "sepal_width",
      "max"
    ],
    [
      "petal_length",
      "min"
    ],
    [
      "petal_length",
      "max"
    ],
    [
      "petal_width",
      "min"
    ],
    [
      "petal_width",
      "max"
    ]
  ],
  "index": [
    [
      "setosa",
      "north"
    ],
    [
      "setosa",
      "south"
    ]
  ],
  "data": [
    [
      4.6,
      5.1,
      3.1,
      3.5,
      1.4,
      1.5,
      0.2,
      0.2
    ],
    [
      4.7,
      5,
      3,
      3.6,
      1.3,
      1.4,
      0.2,
      0.2
    ]
  ],
  "index_field": null,
  "tableType": "MultiIndex"
}
```








CellOps
-----
Coming in the future

Specification for tabular data:

- Visual operations at cell, column, row, table levels

- Column Operations
  - Binning: 

- Simple Table

- Nested Columns

- Nested Rows

- Cell Symbology
  - 'style':
  - 'breaks':
  - 'palette':
  - 'colorMethod':background, text, fontsize
  - 'binMethod': Equal Interval, Natural Breaks, Quantile, 
  - 'binMethod': Equal Interval, Natural Breaks, Quantile, 
