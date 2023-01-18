import java.util.*;

public class DLL {

    node temp, head, prev;

    Scanner sc = new Scanner(System.in);

    class node {

        int data;

        node prev;

        node next;

        node() {

            System.out.println("Enter Data :");

            data = sc.nextInt();

        }

    }

    void insert() {

        node nn = new node();

        if (head == null) {

            head = nn;

        } else {

            temp = head;

            while (temp.next != null) {

                temp = temp.next;

            }

            temp.next = nn;

            nn.prev = temp;

        }

        display();

    }

    void insertAtF() {

        node nn = new node();

        if (head == null) {

            head = nn;

        } else {

            nn.next = head;

            head.prev = nn;

            head = nn;

        }

        display();

    }

    void insertAtP() {

        node nn = new node();

        if (head == null) {

            head = nn;

        } else {

            int val;

            System.out.println("Enter Position :");

            val = sc.nextInt();

            int count = 1;

            if (val == 1) {

                nn.next = head;

                head.prev = nn;

                head = nn;

            } else {

                temp = head;

                prev = head;

                while (temp.next != null) {

                    if (val == count) {

                        prev.next = nn;

                        nn.prev = prev;

                        nn.next = temp;

                        temp.prev = nn;

                    }

                    count++;

                    prev = temp;

                    temp = temp.next;

                }

            }

        }

    }

    void delete() {

        if (head == null) {

            System.out.println("List is Empty...");

        } else {

            if (head.next == null) {

                head = null;

            } else {

                temp = head;

                while (temp.next != null) {

                    temp = temp.next;

                }

                temp.prev.next = null;

            }

        }

        display();

    }

    void deleteAtF() {

        if (head == null) {

            System.out.println("List is Empty...");

        } else {

            head.next.prev = null;

            head = head.next;

        }

        display();

    }

    void deleteAtP() {

        if (head == null) {

            System.out.println("List is Empty...");

        } else {

            int val;

            System.out.println("Enter Position from u want to delete");

            val = sc.nextInt();

            int count = 1;

            if (val == 1) {

                head.next.prev = null;

                head = head.next;

            } else {

                temp = head;

                prev = head;

                while (temp.next != null) {

                    if (val == count) {

                        prev.next = temp.next;

                        temp.next.prev = prev;

                    }

                    count++;

                    prev = temp;

                    temp = temp.next;

                }

            }

        }

        display();

    }

    void display() {

        if (head == null) {

            System.out.println("List is Empty...");

        } else {

            temp = head;

            while (temp != null) {

                System.out.println(" " + temp.data);

                temp = temp.next;

            }

        }

    }

    public static void main(String[] args) {

        DLL d = new DLL();

        Scanner sc = new Scanner(System.in);

        int ch;

        do {

            System.out.println("1.Insert");

            System.out.println("2.Insert At First");

            System.out.println("3.Insert At Position");

            System.out.println("4.Delete");

            System.out.println("5.Delete At First");

            System.out.println("6.Delete At position");

            System.out.println("7.Display");

            System.out.println("8.Exit");

            System.out.println("Enter Your Choice :");

            ch = sc.nextInt();

            switch (ch) {

                case 1:

                    d.insert();

                    break;

                case 2:

                    d.insertAtF();

                    break;

                case 3:

                    d.insertAtP();

                    break;

                case 4:

                    d.delete();

                    break;

                case 5:

                    d.deleteAtF();

                    break;

                case 6:

                    d.deleteAtP();

                    break;

                case 7:

                    d.display();

                    break;

                case 8:

                    System.out.println("Tata...");

                    break;

                default:

                    System.out.println("Invalid Choice...");

                    break;

            }

        } while (ch != 7);

    }

}
