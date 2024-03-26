Consider a dataset that includes the educational qualification of individuals as follows:

| Person | Education Level   |
|--------|-------------------|
| A      | High School       |
| B      | Bachelor's Degree |
| C      | Master's Degree   |
| D      | Ph.D.             |
| E      | Associate Degree  |

## Goal

Our goal is to encode the `Education Level` feature using `OrdinalEncoder` to represent the educational qualifications in a ranked integer format.

## Step 1: Define the Order

First, we need to define the order or rank of the educational qualifications. For this example, we'll use the following order:

1. High School
2. Associate Degree
3. Bachelor's Degree
4. Master's Degree
5. Ph.D.

## Step 2: Apply the OrdinalEncoder

Now, let's apply the `OrdinalEncoder` to transform the `Education Level` into integers based on the defined order:

- **High School**: Encoded as 0
- **Associate Degree**: Encoded as 1
- **Bachelor's Degree**: Encoded as 2
- **Master's Degree**: Encoded as 3
- **Ph.D.**: Encoded as 4

## Encoded Dataset

After applying the `OrdinalEncoder`, our dataset becomes:

| Person | Education Level | Encoded Education Level |
|--------|-----------------|-------------------------|
| A      | High School     | 0                       |
| B      | Bachelor's Degree | 2                   |
| C      | Master's Degree | 3                       |
| D      | Ph.D.           | 4                       |
| E      | Associate Degree| 1                       |