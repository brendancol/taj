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

```json
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
        "style" : {
            "colors": {
                "bg": < #RGB value > ,
                "fg": < #RGB value >
            }
        },
        "index": {
            "type": < "Simple" or "MultiIndex" > ,
            "name": < String, List of strings or 'null' >
            "levels": < Number of levels for a "MultiIndex", value is greater-or-equal to 1 ("Simple") >
        },
        "columns": {
            "type": < "Simple" or "MultiIndex" > ,
            "name": < String, List of strings or 'null' >,
            "levels": < Number of levels for a "MultiIndex", value is greater-or-equal to 1 ("Simple") >
            "bins": {
                # for each column with 'bins' defined, the following mapping:
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

#### Simple Tables
```json
{
    "columns": [
        "sepal_length",
        "sepal_width",
        "petal_length",
        "petal_width",
        "species"
    ],
    "index": [
        0,
        1,
        2,
        3,
        4,
        5,
        6,
        7,
        8,
        9
    ],
    "data": [
        [
            5.1,
            3.5,
            1.4,
            0.2,
            "setosa"
        ],
        [
            4.9,
            3.0,
            1.4,
            0.2,
            "setosa"
        ],
        [
            4.7,
            3.2,
            1.3,
            0.2,
            "setosa"
        ],
        [
            4.6,
            3.1,
            1.5,
            0.2,
            "setosa"
        ],
        [
            5.0,
            3.6,
            1.4,
            0.2,
            "setosa"
        ],
        [
            5.4,
            3.9,
            1.7,
            0.4,
            "setosa"
        ],
        [
            4.6,
            3.4,
            1.4,
            0.3,
            "setosa"
        ],
        [
            5.0,
            3.4,
            1.5,
            0.2,
            "setosa"
        ],
        [
            4.4,
            2.9,
            1.4,
            0.2,
            "setosa"
        ],
        [
            4.9,
            3.1,
            1.5,
            0.1,
            "setosa"
        ]
    ],
    "meta": {
        "tableType": "Simple",
        "index": {
            "type": "Simple",
            "name": null
        },
        "columns": {
            "sepal_width": {
                "colors": [
                    "#005a32",
                    "#238b45",
                    "#41ab5d",
                    "#74c476",
                    "#a1d99b",
                    "#c7e9c0",
                    "#edf8e9"
                ],
                "bins": [
                    2.898,
                    3.043,
                    3.186,
                    3.329,
                    3.471,
                    3.614,
                    3.757,
                    3.9
                ]
            }
        }
    }
}
```


#### Nested Rows
```json
{
    "columns": [
        "sepal_length",
        "sepal_width",
        "petal_length",
        "petal_width"
    ],
    "index": [
        [
            "setosa",
            "south"
        ],
        [
            "setosa",
            "south"
        ],
        [
            "setosa",
            "north"
        ],
        [
            "setosa",
            "north"
        ],
        [
            "setosa",
            "north"
        ],
        [
            "setosa",
            "north"
        ],
        [
            "setosa",
            "south"
        ],
        [
            "setosa",
            "south"
        ],
        [
            "setosa",
            "north"
        ],
        [
            "setosa",
            "north"
        ],
        [
            "setosa",
            "south"
        ],
        [
            "setosa",
            "north"
        ],
        [
            "setosa",
            "north"
        ],
        [
            "setosa",
            "south"
        ],
        [
            "setosa",
            "north"
        ],
        [
            "setosa",
            "south"
        ],
        [
            "setosa",
            "south"
        ],
        [
            "setosa",
            "north"
        ],
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
            5.1,
            3.5,
            1.4,
            0.2
        ],
        [
            4.9,
            3.0,
            1.4,
            0.2
        ],
        [
            4.7,
            3.2,
            1.3,
            0.2
        ],
        [
            4.6,
            3.1,
            1.5,
            0.2
        ],
        [
            5.0,
            3.6,
            1.4,
            0.2
        ],
        [
            5.4,
            3.9,
            1.7,
            0.4
        ],
        [
            4.6,
            3.4,
            1.4,
            0.3
        ],
        [
            5.0,
            3.4,
            1.5,
            0.2
        ],
        [
            4.4,
            2.9,
            1.4,
            0.2
        ],
        [
            4.9,
            3.1,
            1.5,
            0.1
        ],
        [
            5.4,
            3.7,
            1.5,
            0.2
        ],
        [
            4.8,
            3.4,
            1.6,
            0.2
        ],
        [
            4.8,
            3.0,
            1.4,
            0.1
        ],
        [
            4.3,
            3.0,
            1.1,
            0.1
        ],
        [
            5.8,
            4.0,
            1.2,
            0.2
        ],
        [
            5.7,
            4.4,
            1.5,
            0.4
        ],
        [
            5.4,
            3.9,
            1.3,
            0.4
        ],
        [
            5.1,
            3.5,
            1.4,
            0.3
        ],
        [
            5.7,
            3.8,
            1.7,
            0.3
        ],
        [
            5.1,
            3.8,
            1.5,
            0.3
        ]
    ],
    "meta": {
        "tableType": "MultiIndex",
        "index": {
            "type": "MultiIndex",
            "name": [
                "species",
                "location"
            ]
        },
        "columns": {
            "sepal_length": {
                "colors": [
                    "#000003",
                    "#711F81",
                    "#F0605D",
                    "#FBFCBF"
                ],
                "bins": [
                    4.2989999999999995,
                    4.775,
                    5.0,
                    5.4,
                    5.8
                ]
            }
        }
    }
}
```


#### Nested Columns

**TO BE UPDATED**

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

- Cell Symbology: cells may be [draw](https://github.com/brendancol/react-taj) with different colors, for instance, based on their values, corresponding column or index.
  - 'style':
  - 'breaks':
  - 'palette': colors to use for drawing
  - 'colorMethod': background, text, fontsize
  - 'binMethod': Equal Interval, Natural Breaks, Quantile,
