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

#### *Without* column/cell colouring
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
        ],
        [
            "versicolor",
            "north"
        ],
        [
            "versicolor",
            "south"
        ],
        [
            "virginica",
            "north"
        ],
        [
            "virginica",
            "south"
        ]
    ],
    "data": [
        [
            4.4,
            5.5,
            2.9,
            4.2,
            1.0,
            1.9,
            0.1,
            0.6
        ],
        [
            4.3,
            5.8,
            2.3,
            4.4,
            1.1,
            1.9,
            0.1,
            0.5
        ],
        [
            4.9,
            6.9,
            2.2,
            3.4,
            3.0,
            4.9,
            1.0,
            1.6
        ],
        [
            5.0,
            7.0,
            2.0,
            3.3,
            3.5,
            5.1,
            1.0,
            1.8
        ],
        [
            4.9,
            7.9,
            2.5,
            3.8,
            4.5,
            6.7,
            1.4,
            2.5
        ],
        [
            5.6,
            7.7,
            2.2,
            3.4,
            4.9,
            6.9,
            1.5,
            2.5
        ]
    ],
    "meta": {
        "tableType": "MultiIndex",
        "colors": {
            "bg": "#FFFFFF",
            "fg": "#000000"
        },
        "columns": {
            "type": "MultiIndex",
            "name": [
                null,
                null
            ],
            "bins": {}
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

#### *With* column/cell colouring
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
        ],
        [
            "versicolor",
            "north"
        ],
        [
            "versicolor",
            "south"
        ],
        [
            "virginica",
            "north"
        ],
        [
            "virginica",
            "south"
        ]
    ],
    "data": [
        [
            4.4,
            5.5,
            2.9,
            4.2,
            1.0,
            1.9,
            0.1,
            0.6
        ],
        [
            4.3,
            5.8,
            2.3,
            4.4,
            1.1,
            1.9,
            0.1,
            0.5
        ],
        [
            4.9,
            6.9,
            2.2,
            3.4,
            3.0,
            4.9,
            1.0,
            1.6
        ],
        [
            5.0,
            7.0,
            2.0,
            3.3,
            3.5,
            5.1,
            1.0,
            1.8
        ],
        [
            4.9,
            7.9,
            2.5,
            3.8,
            4.5,
            6.7,
            1.4,
            2.5
        ],
        [
            5.6,
            7.7,
            2.2,
            3.4,
            4.9,
            6.9,
            1.5,
            2.5
        ]
    ],
    "meta": {
        "tableType": "MultiIndex",
        "colors": {
            "bg": "#FFFFFF",
            "fg": "#000000"
        },
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
                        4.298,
                        4.56,
                        4.82,
                        5.08,
                        5.34,
                        5.6
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

### Nested Columns
#### *Without* column/cell colouring
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
        "setosa",
        "versicolor",
        "virginica"
    ],
    "data": [
        [
            4.4,
            5.2,
            2.9,
            4.1,
            1.3,
            1.6,
            0.1,
            0.2
        ],
        [
            5.0,
            7.0,
            2.0,
            3.2,
            3.5,
            4.9,
            1.0,
            1.5
        ],
        [
            6.3,
            7.6,
            2.8,
            3.4,
            5.1,
            6.6,
            1.5,
            2.4
        ]
    ],
    "meta": {
        "tableType": "MultiIndex",
        "colors": {
            "bg": "#FFFFFF",
            "fg": "#000000"
        },
        "columns": {
            "type": "MultiIndex",
            "name": [
                null,
                null
            ],
            "bins": {}
        },
        "index": {
            "type": "Simple",
            "name": "species"
        }
    }
}
```


#### *With* column/cell colouring
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
        "setosa",
        "versicolor",
        "virginica"
    ],
    "data": [
        [
            4.4,
            5.2,
            2.9,
            4.1,
            1.3,
            1.6,
            0.1,
            0.2
        ],
        [
            5.0,
            7.0,
            2.0,
            3.2,
            3.5,
            4.9,
            1.0,
            1.5
        ],
        [
            6.3,
            7.6,
            2.8,
            3.4,
            5.1,
            6.6,
            1.5,
            2.4
        ]
    ],
    "meta": {
        "tableType": "MultiIndex",
        "colors": {
            "bg": "#FFFFFF",
            "fg": "#000000"
        },
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
                        4.396999999999999,
                        4.78,
                        5.16,
                        5.54,
                        5.92,
                        6.3
                    ]
                }
            }
        },
        "index": {
            "type": "Simple",
            "name": "species"
        }
    }
}
```


### Simple Tables
#### *With* column/cell colouring
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
        86,
        2,
        0,
        74,
        88,
        92,
        136,
        105,
        87,
        58,
        60,
        32,
        140,
        29,
        72,
        133,
        50,
        27,
        51,
        8
    ],
    "data": [
        [
            6.7,
            3.1,
            4.7,
            1.5,
            "versicolor"
        ],
        [
            4.7,
            3.2,
            1.3,
            0.2,
            "setosa"
        ],
        [
            5.1,
            3.5,
            1.4,
            0.2,
            "setosa"
        ],
        [
            6.4,
            2.9,
            4.3,
            1.3,
            "versicolor"
        ],
        [
            5.6,
            3.0,
            4.1,
            1.3,
            "versicolor"
        ],
        [
            5.8,
            2.6,
            4.0,
            1.2,
            "versicolor"
        ],
        [
            6.3,
            3.4,
            5.6,
            2.4,
            "virginica"
        ],
        [
            7.6,
            3.0,
            6.6,
            2.1,
            "virginica"
        ],
        [
            6.3,
            2.3,
            4.4,
            1.3,
            "versicolor"
        ],
        [
            6.6,
            2.9,
            4.6,
            1.3,
            "versicolor"
        ],
        [
            5.0,
            2.0,
            3.5,
            1.0,
            "versicolor"
        ],
        [
            5.2,
            4.1,
            1.5,
            0.1,
            "setosa"
        ],
        [
            6.7,
            3.1,
            5.6,
            2.4,
            "virginica"
        ],
        [
            4.7,
            3.2,
            1.6,
            0.2,
            "setosa"
        ],
        [
            6.3,
            2.5,
            4.9,
            1.5,
            "versicolor"
        ],
        [
            6.3,
            2.8,
            5.1,
            1.5,
            "virginica"
        ],
        [
            7.0,
            3.2,
            4.7,
            1.4,
            "versicolor"
        ],
        [
            5.2,
            3.5,
            1.5,
            0.2,
            "setosa"
        ],
        [
            6.4,
            3.2,
            4.5,
            1.5,
            "versicolor"
        ],
        [
            4.4,
            2.9,
            1.4,
            0.2,
            "setosa"
        ]
    ],
    "meta": {
        "tableType": "Simple",
        "colors": {
            "bg": "#FFFFFF",
            "fg": "#000000"
        },
        "columns": {
            "type": "Simple",
            "name": null,
            "bins": {
                "sepal_length": {
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
                        4.396,
                        5.04,
                        5.68,
                        6.32,
                        6.96,
                        7.6
                    ]
                }
            }
        },
        "index": {
            "type": "Simple",
            "name": null
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
