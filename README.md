# javacollectionsmethods
interviewpoints
///////program Collections in list
package manipulation;
import java.time.LocalDate;
import java.util.*;

public class MainClass {
	List<LibDetails> list=new ArrayList<>();
	
	Scanner sc = new Scanner(System.in);
	public static void main(String args[])
	{
		System.out.println("Welcome to Manipulation Application \n");
		MainClass mc = new MainClass();
		mc.addDefaultRecords();
		mc.menu();
	}
	

	private void menu() {
		System.out.println("\nChoose Options :  1.Retreive 2.Add 3.Del\n");
		
		int a = sc.nextInt();
		if(a==1)
			ret();
		else if(a==2)
			 add();
		else if(a==3)
			del();		
	}
	
	private void ret() {
		System.out.println("Books are : ");
		if(list.size() > 0) {
		for(LibDetails b:list)  
      	  System.out.println("Student Name: " + b.studentName +"  Student Id : " + b.studentId + "  Book Received Date : "+ b.bookReceivedDate + "  Book Name "+ b.bookName); 
		}else
			System.out.println("OOPS ...! There are No Books...");
		menu();
	}
	private void add() {
		LibDetails lib = new LibDetails();
		Scanner sc = new Scanner(System.in);
		
		System.out.println("Enter the Student Name to add: \n");
		String studentName = sc.nextLine();
		System.out.println("Enter the Student Id to add: \n");
		
		while(!sc.hasNextInt())
		{
			System.out.println("Enter only Int");
			sc.nextLine();
		}
		int studentId = sc.nextInt();
		
		//String s=Integer.toString(studentId);
		Scanner scc = new Scanner(System.in);
		System.out.println("Enter the name of Bookd Received Date to add: \n");
		String bookReceivedDate = scc.nextLine();
		System.out.println("Enter the name of the book to add: \n");
		String bookName = scc.nextLine();
		
		lib.setStudentName(studentName);
		lib.setStudentId(studentId);
		lib.setBookReceivedDate(bookReceivedDate);
		lib.setBookName(bookName);
        
		list.add(lib);
		
		System.out.println("List of Books are");
		ret();
        //for(LibDetails b:list)  
        	 // System.out.println("Student Name: " + b.studentName +" Student Id : " + b.studentId + " Book Received Date : "+ b.bookReceivedDate + " Book Name "+ b.bookName); 
        menu(); 
        
    }
	
	private void del() {
		System.out.println("Enter the name of the book to delete:");
		Scanner scc = new Scanner(System.in);
        String bookName = scc.nextLine();
        
        ListIterator<LibDetails> itr = list.listIterator();
        while(itr.hasNext())
        {
        	LibDetails ld = itr.next();
        	 if (ld.getBookName().equals(bookName)) {
        		 itr.remove();
                 System.out.println("\"" + bookName + "\" has been removed from the library.");
             } 
        	 else {
                 System.out.println("Book not found in the library.");
             }
        }
        
       ret();
        menu();
	}
	  private void addDefaultRecords() {
        for (int i = 1; i <= 5; i++) {
            LibDetails lib = new LibDetails();
            lib.setStudentName("Student" + i);
            lib.setStudentId(i);
            LocalDate currentDate = LocalDate.now();
            lib.setBookReceivedDate(currentDate.toString());
            
            lib.setBookName("Book" + i);
            list.add(lib);
        }
    }
	
}
