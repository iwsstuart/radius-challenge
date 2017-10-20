# radius-challenge

## Data quality report

This report offers a brief description of the quality of the provided dataset, which contains records for 1 million businesses in the United States and its territories. Quality is measured in terms of the number of missing or erroneous values contained in each field, or alternatively, the number of good or relevant values for each field out of the total of 1 million. In addition, several other aspects of the data are explored, namely the cardinality of each field, as well as the relative composition of businesses by age category, for different zip codes.

### 1. Fill rate

The dataset has some values that are automatically inferred to be of type `None` upon reading into Python. By identifying these values and subtracting each column's number from the total, we get our initial "fill rate" figures, which can be seen in the included notebook.

### 2. True-valued fill rate

There are other values in the dataset that are clearly not representive of any true data. By looking at the unique values for some of the categorical fields, we are able to identify a set of values that should also be given the type `None`. These are the strings `'null', 'none', '0', ' '`, and `''`, as well as the integer value `0`. After identifying and converting all of these values to `None`, we can check again for null values and obtain our adjusted fill rate figures.

| Field            | "Good" values |
|------------------|--------|
| address          | 999898 |
| category_code    | 999910 |
| city             | 999895 |
| headcount        | 962273 |
| name             | 999910 |
| phone            | 590798 |
| revenue          | 943001 |
| state            | 999896 |
| time_in_business | 916048 |
| zip              | 999890 |

### 3. Cardinality

One interesting aspect of the data is its cardinality, or the number of unique values contained in each field. From the table below, we can see that `address` and `name` have the most unique values, but even that even those fields have some duplicates. It appears that some businesses in the dataset share and address, and that some different businesses probably have the same name.

| Field            | Unique values |
|------------------|--------|
| address          | 892115 |
| category_code    | 1179   |
| city             | 13715  |
| headcount        | 10     |
| name             | 890718 |
| phone            | 575149 |
| revenue          | 12     |
| state            | 54     |
| time_in_business | 6      |
| zip              | 26392  |

### 4. Exploring further

There are many interesting questions that can be explored with this dataset. The potential for tailored marketing strategies for different localities is one possible use case. Since the dataset contains business information by zip code, it could be useful to look at how different categories of businesses are distributed in different zip codes. Here, we identify the top 100 zip codes in terms of total business count, and within those 100, identify the zip codes with the highest percentages of their total for each business age category. The results are below (the top 3 zip codes for each category are shown - the top 10 can be seen in the notebook output).

#### 1-2 Years

| Zip code            | Percentage of total |
|------------------|--------|
| 85016    | 0.028061  |
| 30305    | 0.025189  |
| 10012    | 0.024938  |

#### 3-5 Years

| Zip code            | Percentage of total |
|------------------|--------|
| 29607 |   0.070905 |
| 30339 |   0.058952 |
| 60007 |   0.054435 |

#### 6-10 Years

| Zip code            | Percentage of total |
|------------------|--------|
| 98052 |   0.155131 |
| 94107 |   0.126168 |
| 10010 |   0.124777 |

#### 10+ Years

| Zip code            | Percentage of total |
|------------------|--------|
| 90025 |   0.808858 |
| 92612 |   0.793814 |
| 20850 |   0.790826 |

