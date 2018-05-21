Tables As JSON
-------

TAJ is a specification for *Pandas DataFrames* as a JSON structure including
not only the data and table's metadata but also visual parameters to visualize
it in a uniform way.

The JSON structure is composed by four sections:
* columns : name of the columns
* index : table index values
* data : list of values disposed rowwise
* meta : metadata section for general visual aspects

```
{
    "columns": [
        < If 'columns:type' is "Simple", this is a list of column names >
        < If 'columns:type' is "MultiIndex", this a list of tuples with column names >
    ],
    "index": [
    ],
    "data": [
    ],
    "meta": {
        "tableType": < "Simple" or "MultiIndex" > ,
        "colors": {
            "bg": < #RGB value > ,
            "fg": < #RGB value >
        },
        "filterFields": <List of strings>,
        "index": {
            "type": < "Simple" or "MultiIndex" > ,
            "name": < String, List of strings or 'null' >
        },
        "columns": {
            "type": < "Simple" or "MultiIndex" > ,
            "name": < String, List of strings or 'null' >,
            "bins": {
                < Column name >: {
                    "edges": < List of values >,
                    "colors": {
                        "bg": < List of #RGB values >,
                        "fg": < List of #RGB values >
                    }
                }
            }
        },
    }
}
```


## Example of tables

### Nested Rows & Columns
#### *With* columns/cell colouring *and* "filter-fields"
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
      "versicolor",
      "north"
    ],
    [
      "virginica",
      "north"
    ]
  ],
  "data": [
    [
      4.4,
      5.7,
      2.9,
      4.4,
      1.3,
      1.6,
      0.2,
      0.6
    ],
    [
      5.5,
      5.7,
      2.4,
      2.8,
      3.8,
      4.5,
      1.1,
      1.3
    ],
    [
      5.8,
      7.7,
      2.8,
      3.2,
      4.8,
      6.7,
      1.6,
      2.4
    ]
  ],
  "meta": {
    "tableType": "MultiIndex",
    "colors": {
      "bg": "#FFFFFF",
      "fg": "#000000"
    },
    "filterFields": [
      "sepal_length|min"
    ],
    "columns": {
      "type": "MultiIndex",
      "name": [
        null,
        null
      ],
      "bins": {
        "sepal_length|min": {
          "colors": {
            "bg": [
              "#006d2c",
              "#31a354",
              "#74c476",
              "#bae4b3",
              "#edf8e9"
            ],
            "fg": [
              "#6d0041",
              "#a33180",
              "#c474c2",
              "#ddb3e4",
              "#f4e9f8"
            ]
          },
          "edges": [
            4.398,
            4.68,
            4.96,
            5.24,
            5.52,
            5.8
          ]
        }
      }
    },
    "index": {
      "type": "MultiIndex",
      "name": [
        "species",
        "location"
      ]
    }
  }
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

- Cell Symbology: cells may be [draw](https://github.com/brendancol/react-taj) with different colors, for instance, based on their values, corresponding column or index.
  - 'style':
  - 'breaks':
  - 'palette': colors to use for drawing
  - 'colorMethod': background, text, fontsize
  - 'binMethod': Equal Interval, Natural Breaks, Quantile,
