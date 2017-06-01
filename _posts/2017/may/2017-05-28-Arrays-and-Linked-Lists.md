---
layout: post
title:  "Singly Linked Lists"
date:   2017-05-28
excerpt: "In this episode of 'Muhammed thinks he knows his shit', we will go over Singly Linked List and how to implement it"
tag:
- java
- EECS 2011
- data structures

comments: false
---
Lets quickly do a refresher on Arrays and Singly Linked Lists. I'll jot down notes as I go.

## Arrays
- An array is a collection of elements of the same type
- Each cell has an index numbered 0, 1, 2 and so forth
- The length of an array can be using syntax array.length()
- Elements in arrays can contain primitive types or reference types

## Singly Linked Lists
- Each node has a **single** link to the next node (stored as auxilliary data)
- Traversing a linked list takes linear time
- Inserting or deleting an elemnt in the beginning can be done in constant time
- appending an element at the end will take linear time
- It does not store a pointer or reference to the previous node
- Head can be pointing to null if array is empty
- Or pointing to something
- There is no index system in singly linked list
- So elements cannot be accessed directly
- To access an element, you must start from head node and traverse down list.


<figure>
<figcaption>Inserting a Node</figcaption>
 <a href="http://www.java2novice.com/images/sll_insert_after.png"><img src="http://www.java2novice.com/images/sll_insert_after.png"></a>
</figure>

## Singly Linked List Implementation
We begin my defining a class called node. In the class Node we have defined the next node and the data the current node stores, which in this case is of type int. We have also defined a constructor that intializes data with a value. {: .notice}
{% highlight java %}

public class Node
{
	Node next;
	int data;
	public Node(int data)
	{
		this.data = data;
	}

}
{% endhighlight %}
Here we have the LinkedLists class with methods append, prepend and deleteWithValue. Read it through and than I'll explain it bit by bit. {: .notice}
{% highlight java %}
public class LinkedList
{
	Node head;
	public void append(int data)
	{
		if(head == null)
		{
			head = new Node(data);
			return;
		}
		Node current = head;
		while(current.next != null)
		{
			current = current.next;
		}
		current.next = new Node(data);
	}
	public void prepend(int data)
	{
		Node newHead = new Node(data);
		newHead.next = head;
		head = newHead;
	}
	public void deleteWithValue(int data)
	{
		if(head == null) return;
		if(head.data == data)
		{
			head = head.next;
			return;
		}
		Node current = head;
		while(current.next != null)
		{
			if(current.next.data == data)
			{
				current.next = current.next.next;
				return;
			}
			current = current.next;
		}
	}
}
{% endhighlight %}
So this method starts off by taking a data value as a parameter. The first thing we check is if the list is empty by checking if the head value is null, and if the head value is null we make a new node and set the head to that and return. If the list isn't empty, we set head node as the starting point to traverse through a list. We iterate through a loop until we get to the end of the list, we know we're at the end of the list when current.next is null. In other words when there are no other element after the element we're currently standing on. Once we're at the end of the list, we simply make a new node and insert it after the last node. FIN. {: .notice}
{% highlight java %}
public void append(int data)
{
  if(head == null)
  {
    head = new Node(data);
    return;
  }
  Node current = head;
  while(current.next != null)
  {
    current = current.next;
  }
  current.next = new Node(data);
}
{% endhighlight %}
In the prepend method we want to add a data value to the beginning. You might have to read this explanation a coupe of times, but the concept is fairly simple. We start by making a new node and "insert" the "old" head node infront of the new node. Once we've done that we set the head pointer to the new node we made.  Actually... that wasn't too bad. {: .notice}
{% highlight java %}
public void prepend(int data)
{
  Node newHead = new Node(data);
  newHead.next = head;
  head = newHead;
}
{% endhighlight %}
This method is a little more interesting. Here we want to delete an element with a particular value. We start by checking if list is empty, if it is, we simply return. Next we check if the element we want to remove is the first element. We do this by checking the data inside the head. If the head is the element, we remove it by pointing the head, to the element after the head. If the element we want to remove isn't the first element, we traverse through the list and stop righ before the element we want to remove. Once we're standing before the element we want to remove, we "jump over it" by setting the pointer to the element we want to remove to the node after the node we want to remove. Reading this over, I feel like i'm the only one whose going to understand this explanation. {: .notice}
{% highlight java %}
public void deleteWithValue(int data)
{
  if(head == null) return;
  if(head.data == data)
  {
    head = head.next;
    return;
  }
  Node current = head;
  while(current.next != null)
  {
    if(current.next.data == data)
    {
      current.next = current.next.next;
      return;
    }
    current = current.next;
  }
}
{% endhighlight %}
