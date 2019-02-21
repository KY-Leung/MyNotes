* Big 0 = Worst Case

* Omega = Best Case

* Theta = Average Case

  > Only focus Worst Case
  >
  > Work for the worst, with the best

### **Find Complexity:**

1. Constant; +, -, *, / & if takes 1 step toexecute
2. Loops, Subroutine (function calls) takes n stepto execute
3. Memory access; assign variable update value take1 step




## Data Structures

### Array

```java
int[] myList = new int[list.length];
double[] myList = {1.9, 2.9, 3.4, 3.5};

// 2-dimensional array
int[][] num = new int[3][3];
```



### Arraylist

* Best for access and searching
* Bad of insert and delete

```java
ArrayList<String> ar = new ArrayList<String>();
ar.add("Developer");
ar.remove(1);

ArrayList<employee> emp = new ArrayList<String>();
emp.add(new employee("Join", 20));

class employee{
  String name;
  int age;
  public employee(String name, int age){
    this.name = name;
    this.age = age;
  }
}
```



### [Linked List](https://www.tutorialspoint.com/java/java_linkedlist_class.htm)

```java
import java.util.*;
LinkedList ll = new LinkedList();
LinkedList<String> ll = new LinkedList<String>();

ll.add("OMG");
Iterator<String> itr = ll.iterator();

// Print each
while(itr.hasNext())
  System.out.printIn(itr.next());
```



### HashSet (No duplicate elements)

```java
HashSet<String> ll = new HashSet<String>();
ll.add("OMG");
ll.add("OMG");

// OMG
```



### TreeSet (No duplicate elements & ASC)

```java
HashSet<String> ll = new HashSet<String>();
ll.add("OMG");
ll.add("AMG");

// AMG
// OMG
```



### Hashed Map / Hashed Table (Like library)

```java
HashMap<Integer, String> map = new HashMap<Integer, String>();
map.put(1, "OMG"); //add & edit
map.remove(1);
System.err.println(map.get(1));

// Print each
for(Map.Entry m:map.entrySet()){
  System.err.println(m.getKey() + m.getValue());
}
```

#### Worst case

* Search O(n) *Found at the end of linked list / not found*
* Insert O(n) *Insert at the end of linked list*
* Delete O(n) *Delete at the end of linked list*

#### Benefit

* Search at specify place
* Take O(1) if insert at start of linked list




### Stack (FILO)

```java
import java.util.*;

Stack sk = new Stack();
Stack<String> sk = new Stack<String>();
sk.push(36);
System.out.println(sk.pop());
sk.search(12) //if found, return # of pop to get the num. Else return -1
```

> Represented using:
>
> * Array
> * Dynamic array (Java)
> * Linked list

#### Worst case

- Search O(n) *Pop until the end of stack / not found*
- Access O(n) *Pop until the end of stack*
- Insert O(1) *Insert at the head*
- Delete O(1)




### Queue (FIFO)

```java
import java.util.*;

Queue queueA = new LinkedList();
queueA.add("element 1");
System.out.println(queueA.element()); //return head without dequeue
System.out.println(queueA.remove()); // or queueA.poll()
```

> Represented using:
>
> - Array
> - Dynamic array
> - Linked list

#### Worst case

- Search O(n) *Dequeue until the end of stack / not found*
- Access O(n) *Dequeue until the end of stack*
- Insert O(1) *Queue at the head*
- Delete O(1) 



#### Priority Queue

``` java
PriorityQueue queueA = new LinkedList(); //Arrange in asc at all time
```

> [39. Queue and Priority Queue](https://www.udemy.com/data-structure-and-algorithms-analysis/learn/v4/t/lecture/6293294?start=0)
>
> 06.00 - PriorityQueue of student
>
>     - implements Comparable <student>
> - override compareTo



### n-Factorial

```java
public static int fact(int n) {
    if (n == 0)
        return 1;
    else
        return n*fact(n-1);
}
```



## Search

### Linear Search

```java
public static int ls(int[] arr, int searching) {
    for(int i=0; i<arr.length; i++){
        if (arr[i] == searching)
            return i;
    }
    return 88;
}
```



### Binary Search

```java
int[] arr = {5, 10, 11, 12, 16, 25, 30, 32};
int searching = 30;
int low = 0;
int mid = 0;
int high = arr.length - 1;
int numOfTry = 0;
Boolean isFound = false;
        
while (!isFound){
    if (low > high){
        System.out.println("Not Found");
        break;
    }
    mid = (high + low) / 2;
    numOfTry++;
    if (arr[mid] == searching){
        System.out.println("Found after " + numOfTry + " tries.");
        break;
    }
    if (searching < arr[mid])
        high = mid - 1;
    if (searching > arr[mid])
        low = mid + 1;
}
```



### Interpolation Search (Best if array is continuous) Dictionary, only look for 11..

```java
mid = low+((high - low) / A[hight] - A[low]) * (Search - A[low]);
```

