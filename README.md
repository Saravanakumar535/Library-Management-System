# Library-Management-System
// package library_management_sytem;
import java.util.*;
class Book {
	String title;
	Boolean isAvailable;
	Book(String title){
		this.title=title;
		this.isAvailable=true;
		
	}
	public void BookBorrowed()
	{
		this.isAvailable=false;
	}
	public void BookReturned()
	{
		this.isAvailable=true;
	}
	
}
// package library_management_sytem;
// import java.util.ArrayList;
class Library {
	ArrayList<Book> books=new ArrayList<Book>();
	public void addbook(String name)
	{
		books.add(new Book(name));
		System.out.println(name+" added to library");
	}
	public void ShowBooks()
	{
		System.out.println("Library Books are");
		boolean hasAvailable=false;
		for(Book book : books)
		{
			if(book.isAvailable)
			{
			System.out.println(book.title);
			hasAvailable=true;
			}
		}
		if(!hasAvailable){
		System.out.println("No books are available");
		}
	}
	public void borrowbook(String title)
	{
		for(Book book:books)
		{
			if(book.title.equalsIgnoreCase(title) && book.isAvailable)
			{
				book.BookBorrowed();
				System.out.println(title+" is Borrowed");
				return;
			}
		}
		
			System.out.println(title+ " not available in the library ");
	}
	public void returnbook(String title)
	{
		for(Book book : books)
		{
			if(book.title.equalsIgnoreCase(title)&& !book.isAvailable)
			{
				book.BookReturned();
				System.out.println(title+" is returned ");
				return;
			}
		}
		System.out.println(title+" is not Borrowed");
	}
	
}
// package library_management_sytem;
// import java.util.*;
public class Main {

	public static void main(String[] args) {
		Library library=new Library();
		Scanner sc=new Scanner(System.in);
		while (true){
			System.out.println("Library :");
			System.out.println("1. Add book");
			System.out.println("2. Show books");
			System.out.println("3. Borrowbbook");
			System.out.println("4. Returnbook");
			System.out.println("5. Exit");
			int choice=sc.nextInt();
			sc.nextLine();
			switch(choice)
			{
			case 1:
				System.out.println("Enter book title: ");
				String title=sc.nextLine();
				library.addbook(title);
				break;
			case 2:
				library.ShowBooks();
				break;
			case 3:
				System.out.println("Enter the book title to borrow: ");
				String title1=sc.nextLine();
				library.borrowbook(title1);
				break;
			case 4:
				System.out.println("Enter the book title to return: ");
				String title2=sc.nextLine();
				library.returnbook(title2);
				break;
			case 5:
				System.out.println("Exiting.....");
				return;
			default:
				System.out.print("Invalid choice");
				
			}
			
		}
		

	}

}
