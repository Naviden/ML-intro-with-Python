Suppose we have a dataset with a single feature (e.g., temperatures recorded over a week) as follows:

| Day       | Temperature (°C) |
|-----------|------------------|
| Monday    | 10               |
| Tuesday   | 15               |
| Wednesday | 20               |
| Thursday  | 30               |
| Friday    | 25               |

## Goal

Our goal is to scale the `Temperature` feature to a range between 0 and 1.

## Step 1: Determine the Minimum and Maximum Values

First, we find the minimum and maximum values of the `Temperature` feature.

- **Minimum (Min)**: 10°C
- **Maximum (Max)**: 30°C

## Step 2: Apply the MinMaxScaler Formula

The MinMaxScaler rescales each feature to a given range (in this case, between 0 and 1) using the following formula:

\[ \text{Scaled value} = \frac{\text{value} - \text{Min}}{\text{Max} - \text{Min}} \]

## Step 3: Calculate the Scaled Values

Let's apply the formula to each temperature value:

- **Monday**: \( \frac{10 - 10}{30 - 10} = 0 \)
- **Tuesday**: \( \frac{15 - 10}{30 - 10} = 0.25 \)
- **Wednesday**: \( \frac{20 - 10}{30 - 10} = 0.5 \)
- **Thursday**: \( \frac{30 - 10}{30 - 10} = 1 \)
- **Friday**: \( \frac{25 - 10}{30 - 10} = 0.75 \)

## Scaled Dataset

After applying the `MinMaxScaler`, our dataset becomes:

| Day       | Scaled Temperature |
|-----------|--------------------|
| Monday    | 0                  |
| Tuesday   | 0.25               |
| Wednesday | 0.5                |
| Thursday  | 1                  |
| Friday    | 0.75               |