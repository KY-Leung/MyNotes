## Linked List

​	`LinkedList<Integer> q = new LinkedList<Integer>();`

 `<Integer>` tells Java what type of data will go into the list. Since lists could contain any kind of data, Java needs to know what type of data is in any particular list to help it check types at compile time.

#### Integer versus Int

The type given to a LinkedList must be the name of either a class or an interface. In Java, Integer is a class that holds a number, whereas int is just a number by itself (without a class).



## Getting User's Input

    Scanner sc = new Scanner(System.in);
    System.out.println("Enter Number of Edges");
    numOfEdges = sc.nextInt();



`System.nanoTime()`

This method returns the current value of the most precise available system timer, in nanoseconds.

Nanosecond(ns) / 1,000,000 = Millisecond(ms)