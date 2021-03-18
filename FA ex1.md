```python
import pandas as pd

```


```python
dataset=pd.read_excel("2.Factor Analysis.xlsx",sheet_name=0)
```


```python
dataset.head()
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
      <th>X110</th>
      <th>X111</th>
      <th>X112</th>
      <th>X113</th>
      <th>X114</th>
      <th>X116</th>
      <th>X117</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4</td>
      <td>4</td>
      <td>3</td>
      <td>4</td>
      <td>4</td>
      <td>5</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>4</td>
      <td>3</td>
      <td>4</td>
      <td>3</td>
      <td>5</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5</td>
      <td>5</td>
      <td>3</td>
      <td>5</td>
      <td>3</td>
      <td>4</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>4</td>
      <td>2</td>
      <td>4</td>
      <td>2</td>
      <td>5</td>
      <td>4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>4</td>
      <td>1</td>
      <td>5</td>
      <td>3</td>
      <td>4</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
dataset.columns
```




    Index(['X110', 'X111', 'X112', 'X113', 'X114', 'X116', 'X117'], dtype='object')




```python
from sklearn.decomposition import PCA
```


```python
from sklearn.preprocessing import scale
```


```python
X = dataset.values
X
```




    array([[4, 4, 3, ..., 4, 5, 4],
           [5, 4, 3, ..., 3, 5, 4],
           [5, 5, 3, ..., 3, 4, 3],
           ...,
           [4, 4, 5, ..., 3, 3, 3],
           [4, 3, 4, ..., 4, 4, 3],
           [1, 5, 4, ..., 5, 5, 5]], dtype=int64)




```python
X=scale(X)
X
```




    array([[-0.12512162, -0.40975395, -0.33004819, ...,  0.29179593,
             0.89177093,  0.26090919],
           [-0.11685185, -0.40975395, -0.33004819, ..., -0.89920786,
             0.89177093,  0.26090919],
           [-0.11685185,  1.02797921, -0.33004819, ..., -0.89920786,
            -0.57014863, -0.8734786 ],
           ...,
           [-0.12512162, -0.40975395,  1.40704753, ..., -0.89920786,
            -2.03206819, -0.8734786 ],
           [-0.12512162, -1.84748711,  0.53849967, ...,  0.29179593,
            -0.57014863, -0.8734786 ],
           [-0.14993094,  1.02797921,  0.53849967, ...,  1.48279971,
             0.89177093,  1.39529699]])




```python
pca=PCA(n_components=7)
```


```python
pca.fit(X)
```




    PCA(n_components=7)




```python
print(pca.explained_variance_)
```

    [1.46957610e+04 1.56419739e+00 1.14152668e+00 5.53140602e-01
     4.29613181e-01 3.54425505e-01 2.31737710e-01]
    

#out of the 7 var 
1st 3 var eigen val is > 1
so oly those 3 vars are extracted as factors


```python
pca=PCA(n_components=3)
```


```python
pca.fit(X)
```




    PCA(n_components=3)




```python
print(pd.DataFrame(pca.components_).T) 
#finding the correlation btw factors 1,2,3 with 7 vars this is called factor loading
#representing factor loading in a tabular form is called factor matrix

```

              0         1         2
    0  0.999998  0.000614 -0.000178
    1 -0.001311 -0.129214 -0.232440
    2  0.000615 -0.763794  0.589329
    3 -0.000209 -0.128341 -0.144333
    4 -0.000781 -0.390808 -0.409463
    5  0.000632 -0.080444 -0.475214
    6  0.001255 -0.473548 -0.429352
    


```python

```
