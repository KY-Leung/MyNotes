# Common

```python
import ...

def compareTriplets(a, b):
    totalA = 0
    totalB = 0

    for x in range(0, len(a)):	# range not inclusive the last number
        if a[x] > b[x]:
            totalA += 1
        elif a[x] < b[x]:
            totalB += 1

    return (totalA, totalB)

# Sum of array
sum(ar)

[0][0] [0][1] [0][2]
[1][0] [1][1] [1][2]
[2][0] [2][1] [2][2]

0 - 2

```



### `diagonalDifference(arr)`

```python
def diagonalDifference(arr):
    primaryDiagonal = 0
    secondaryDiagonal = 0

    for i in range(0, len(arr)):
        primaryDiagonal += arr[i][i]
        secondaryDiagonal += arr[i][abs(i-(len(arr)-1))]
    
    return abs(primaryDiagonal - secondaryDiagonal)
```



```
def plusMinus(arr):
    positive = 0
    negative = 0
    zero = 0

    for x in range(0, len(arr)):
        if arr[x] > 0:
            positive += 1
        elif arr[x] < 0:
            negative += 1
        else:
            zero += 1
    print(formatTo(positive))
    print(formatTo(negative))
    print(formatTo(zero))

def formatTo(x):
    return "{:.6f}".format(x/len(arr))
```



## Staircase

**Sample Input**

```
6 
```

**Sample Output**

```
     #
    ##
   ###
  ####
 #####
######
```

**Solution**

```python
def staircase(n):
    for x in range(1, n+1):
        numOfHash = '#' * x
        numOfSpace = ' ' * (n-x)
        print ("%s%s" % (numOfSpace, numOfHash))
```









## User Input

### `raw_input`

```python
url = raw_input("Enter a website to extract the URL's from: ")
```



### `requests.get`

```python
r = requests.get("URL")
data = r.text
```



## Standard Functions

### Run infinite

```python
from time import sleep

try:
	while True:
	sleep(60)

except KeyboardInterrupt:
	exit()
```



## Beautifulsoup Functions

### `findAll`

`.findAll()` returns list of all found elements:

```python
inputTag = soup.findAll(attrs={"name" : "stainfo"})
OR
inputTag = soup.findAll("div", {"data-relatedlink": True})
```

`inputTag` is a list. Depending on what you want exactly, you either should do:

```python
output = inputTag[0]['value']
OR
output = inputTag[0]['data-relatedlink']
```



### `find`

`.find()` method returns only the 1st found element:

```python
 inputTag = soup.find(attrs={"name": "stainfo"})
 output = inputTag['value']
```

