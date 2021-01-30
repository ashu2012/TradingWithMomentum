
# Calculate Returns

![returns_chart.png](returns_chart_720_358.png)

Using the formula $ \frac{p_{t} - p_{t-1}}{p_{t-1}} $, let's apply it to some example prices. For this exercise, we'll calculate the returns for each day using the closing price data in `close`.


```python
import pandas as pd

close = pd.DataFrame(
    {
        'ABC': [1, 5, 3, 6, 2],
        'EFG': [12, 51, 43, 56, 22],
        'XYZ': [35, 36, 36, 36, 37],},
    pd.date_range('10/01/2018', periods=5, freq='D'))
close
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ABC</th>
      <th>EFG</th>
      <th>XYZ</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2018-10-01</th>
      <td>1</td>
      <td>12</td>
      <td>35</td>
    </tr>
    <tr>
      <th>2018-10-02</th>
      <td>5</td>
      <td>51</td>
      <td>36</td>
    </tr>
    <tr>
      <th>2018-10-03</th>
      <td>3</td>
      <td>43</td>
      <td>36</td>
    </tr>
    <tr>
      <th>2018-10-04</th>
      <td>6</td>
      <td>56</td>
      <td>36</td>
    </tr>
    <tr>
      <th>2018-10-05</th>
      <td>2</td>
      <td>22</td>
      <td>37</td>
    </tr>
  </tbody>
</table>
</div>



Using the returns formula on the closing prices for the ticker "ABC" should give us `[(5-1)/1, (3-5)/5, (6-3)/3, (2-6)/6]` or `[4, -0.4, 1, -0.66]`. To calculate this for the whole DataFrame, we'll use the [DataFrame.shift](https://pandas.pydata.org/pandas-docs/version/0.21/generated/pandas.DataFrame.shift.html) function.

This function allows us to shift the rows of data. For example, the following shifts the rows in `close` two days back.


```python
close.shift(2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ABC</th>
      <th>EFG</th>
      <th>XYZ</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2018-10-01</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2018-10-02</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2018-10-03</th>
      <td>1.0</td>
      <td>12.0</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>2018-10-04</th>
      <td>5.0</td>
      <td>51.0</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>2018-10-05</th>
      <td>3.0</td>
      <td>43.0</td>
      <td>36.0</td>
    </tr>
  </tbody>
</table>
</div>



The data for the row "2018-10-03" contains data that is two days in the past. You'll also notice the "NaN" values for "2018-10-01" and "2018-10-02". Since there's not data two days in the past for these dates, it returns a "NaN" value.

Use this function, you can also shift in the future using a negative number. Let's shift one day in the future.


```python
close.shift(-1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ABC</th>
      <th>EFG</th>
      <th>XYZ</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2018-10-01</th>
      <td>5.0</td>
      <td>51.0</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>2018-10-02</th>
      <td>3.0</td>
      <td>43.0</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>2018-10-03</th>
      <td>6.0</td>
      <td>56.0</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>2018-10-04</th>
      <td>2.0</td>
      <td>22.0</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>2018-10-05</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



## Quiz
Using what you know about the [DataFrame.shift](https://pandas.pydata.org/pandas-docs/version/0.21/generated/pandas.DataFrame.shift.html) function, implement the function.

Once you successfully implemented the quiz, you can can continue to the next concept in the classroom.


```python
import quiz_tests


def calculate_returns(close):
    """
    Compute returns for each ticker and date in close.
    
    Parameters
    ----------
    close : DataFrame
        Close prices for each ticker and date
    
    Returns
    -------
    returns : DataFrame
        Returns for each ticker and date
    """
    # TODO: Implement Function
    
    re


quiz_tests.test_calculate_returns(calculate_returns)
```

## Quiz Solution
If you're having trouble, you can check out the quiz solution [here](calculate_returns_solution.ipynb).
