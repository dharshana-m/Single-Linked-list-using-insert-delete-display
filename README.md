import java.util.*;
    
    class Linkedlist
    {
        node head;
        Linkedlist()
        {
            head = null;
        }
       
        class node 
        {
            int data;
            node next;
            node(int d)  // 9
            {
                data = d; // data = 9
                next = null;
            }
        }
    
    public void insertAtbegin(int d)
    {
        node n = new node(d);
        n.next = head;
        head = n;
    }
    public void insertAtLast(int d)  // 4
    {
        node n = new node(d);  // 4
        if(head == null)
        {
            head = n;
        }
        else
        {
            node current = head;
            while(current.next!=null)
            {
                current = current.next;
            }
            current.next = n;
        }
    }
    public void insertMiddle(int d, int p)   // p - 3
    {
        if(p<=1)
        {
            insertAtbegin(d);
        }
        node n = new node(d);
        node current = head;
        int c = 1;                          // c - 3
        while(current != null && c < p-1)
        {
            current = current.next;
            c++;
        }
        if(current == null)
        {
            insertAtLast(d);
        }
        else
        {
            n.next = current.next;
            current.next = n;
        }
        
    }
    public void display()
    {
        if(head == null)
        {
            System.out.println("List is empty to display");
        }
        else
        {
            node current = head;
            while(current!=null) // traverse to last node and print the data
            {
                System.out.print(current.data+" ");
                current = current.next;
            }
        }
    }
    public void displayPosition(int p)
    {
        int pos = 1;
        if(head == null)
        {
            System.out.println("List is empty to display");
        }
        else
        {
            node current = head;
            while(current!=null) 
            {
                if(pos==p)
                {
                    System.out.println("\nNode: " + pos + " Data: " + current.data+" ");
                    return;
                }
                else
                {
                    current = current.next;
                    pos++;
                }
            }
            System.out.println(" Invalid position");
        }
    }
    public void deleteBegin()
    {
        if(head == null)
        {
            System.out.println("List is empty to delete");
        }
        else
        {
            node current = head;
            head = current.next;
            current.next = null;
        }
    }
    public void deleteMiddle(int p)   // p - 3
    {
        if(p<=1)
        {
            deleteBegin();
            return;
        }
        node current = head;
        node prev = null;
        int c = 1;                          // c - 3
        while(current != null && c < p)
        {
            prev = current;
            current = current.next;
            c++;
        }
        if(current == null)
        {
            System.out.println("Invalid position to delete");
        }
        else
        {
            prev.next = current.next;
        }
        
    }
    
    public void deleteLast()
    {
        if(head == null)
        {
            System.out.println("List is empty to delete");
        }
        else
        {
            node current = head;
            node prev = head;
            while(current.next!=null)
            {
                prev = current;
                current = current.next;
            }
            prev.next = null;
        }
    }
    public void findElement(int k)
    {
        if(head == null)
        {
            System.out.println("List is empty to find");
        }
        else
        {
            node current = head;
            while(current!=null) // traverse to last node and print the data
            {
                if(current.data==k)
                {
                    System.out.println("Element Found");
                    return;
                }
                else
                {
                    current = current.next;
                }
            }
            System.out.print(k + " Element not found");
        }
    }
    }
    
    public class Main 
    {
        public static void main(String args[])
        {//  class     obj    new  constructor()
            Linkedlist list = new Linkedlist();
            Scanner sc = new Scanner(System.in);
            int n = sc.nextInt();
            int a;
            for(int  i = 0; i< n; i++)
            {
                a = sc.nextInt();
                list.insertAtbegin(a);
            }
            list.deleteMiddle(3);
            list.deleteBegin();
          	list.deleteLast();
          	list.insertAtLast(14);
            list.display();
        }
    }
