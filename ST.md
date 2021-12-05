# ATM

```
import java.util.*;
class Check {
  int checkPin(int p, int i) {
    if (p == i)
      return 1;
    System.out.println("Invalid PIN number");
    return 0;
  }
  int checkAccount(int t) {
    if (t == 1) {
      System.out.println("Opened Savings account");
      return 1;
    } else if (t == 1) {
      System.out.println("Opened Current account");
      return 1;
    } else {
      System.out.println("Invalid Account Type");
      return 0;
    }
  }
  void checkBal(int bal) {
    System.out.println("Your available balance is=" + bal);
  }
  int withdraw(int a, int b) {
    if (a > b) {
      System.out.println("Insuffecient funds");
      return 0;
    }
    b = b - a;
    System.out.println("Successful transaction");
    checkBal(b);
    return b;
  }
  int deposit(int a, int b) {
    b = b + a;
    System.out.println("Successful transaction");
    checkBal(b);
    return b;
  }
}
public class ATM {
  public static void main(String[] args) {
    // TODO Auto-generated method stub
    Scanner sc = new Scanner(System.in);
    Check obj = new Check();
    int r, pass = 5555, k = 0, balance = 5000;
    int inp;
    while (k < 3) {
      System.out.println("Enter PIN number");
      inp = sc.nextInt();
      r = obj.checkPin(pass, inp);
      if (r == 1) {
        System.out.println("\nWelcome\n");
        break;
      }
      k++;
    }
    if (k == 3) {
      System.out.println("Ttransaction Terminated");
      System.exit(0);
    }
    r = 0;
    while (r == 0) {
      System.out.println("Enter the account type\n1-Savings\n2-Current\n");
      int type = sc.nextInt();
      r = obj.checkAccount(type);
    }
    int trans = 0;
    while (trans != 4) {
      System.out.println("Select transaction:\n\n1-Check Balance\n2-Withdraw\n3-Deposit\n4-Exit\n");
      trans = sc.nextInt();
      switch (trans) {
      case 1:
        obj.checkBal(balance);
        break;
      case 2:
        System.out.println("Enter the amount you want to withdraw");
        int amt = sc.nextInt();
        if (amt % 500 != 0) {
          System.out.println("Invalid amount");
        } else {
          r = obj.withdraw(amt, balance);
          balance = r;
        };
        break;
      case 3:
        System.out.println("Enter the amount you want to deposit");
        int amt2 = sc.nextInt();
        int b = obj.deposit(amt2, balance);
        balance = b;
        break;
      }
    }
  }

}
```

# Next Date
```
public class NextDate {
	public static String next(int d, int m, int y, int cc) {
		if (d == cc) {
			d = 1;
			if (m==12) {
				y++;
				m = 1;
			} else {
				m++;
			}
		} else if (d < cc) {
			d ++;
		} else {
			return "Invalid Date";
		}
		return String.valueOf(d)+"-"+String.valueOf(m)+"-"+String.valueOf(y);
	}
	
	public String nextDay(int d, int m, int y) {
		if (d >= 1 && d <= 31 && m >= 1 && m <= 12 && y >= 1812 && y <= 2012) {
			switch(m) {
			case 1:
			case 3:
			case 5:
			case 7:
			case 8:
			case 10:
			case 12:
				return (next(d, m, y, 31));
			case 4:
			case 6:
			case 9:
			case 11:
				return next(d, m, y, 30);
			default:
				return next(d, m, y, ((y%4==0 && y%100!=0) || y%400==0)?29:28);
			}
		}
		return "Invalid Date";
	}
	
	public static void main (String [] args) {
		NextDate a = new NextDate();
		System.out.println(""+a.nextDay(38, 2, 2000));
	}
}
```

# Triangle 
```
import java.util.*;
public class Triangle {
	
public String check(int x,int y,int z){
	
	if(x<=200 && x>=1 && y<=200 && y>=1 && z<=200 && z>=1)
	{
		if((x+y)>z && (x+z)>y && (y+z)>x)
		{
			if(x==y && y==z && z==x){
				
				return  "Equilateral";
			}
			else if(x!=y && y!=z && z!=x){
				return "Scalene";
			}
			
			else{
				return "Isosceles";
			}
		}
		else{
			return "Not a triangle";
		}
	}
	else{
		return "Not a triangle";
	}

		
}
public static void main(String[] Args){
	Scanner sc=new Scanner(System.in);
	Triangle t=new Triangle();
	System.out.println("Enter the 3 sides of triangle");
	int x=sc.nextInt();
	int y=sc.nextInt();
	int z=sc.nextInt();
	System.out.println(t.check(x,y,z));
 }

}
```

# Triangle Test
```
import static org.junit.Assert.*;

import org.junit.Test;

public class TriangleTest {
	Triangle T = new Triangle();
	@Test
	public void test1() {
		assertEquals(T.check(100,100,1),"Isosceles");
	}
	
	@Test
	public void test2() {
		assertEquals(T.check(1,100,100),"Isosceles");
	}
	
	@Test
	public void test3() {
		assertEquals(T.check(1,2,1),"Not a triangle");
	}
	
	@Test
	public void test4() {
		assertEquals(T.check(1,2,200),"Not a triangle");
	}
	
	@Test
	public void test5() {
		assertEquals(T.check(2,3,4),"Scalene");
	}
	
	@Test
	public void test6() {
		assertEquals(T.check(98,99,100),"Scalene");
	}
	
	@Test
	public void test7() {
		assertEquals(T.check(2,2,2),"Equilateral");
	}
	
	@Test
	public void test8() {
		assertEquals(T.check(100,100,100),"Equilateral");
	}
	
}
```
