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

# Next Date BVA
```
import static org.junit.Assert.*;
import org.junit.Test;
public class Normalbva {
	@Test
	public void test1() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,1812),"13/3/1812");
	}
	@Test
	public void test2() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(30,3,1813),"31/3/1813");
	}
	
@Test
	public void test3() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,1912),"1/1/1913");
	}
	
	@Test
	public void test4() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,2019),"13/3/2019");
	}
	@Test
	public void test5() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,2020),"13/3/2020");
	}
	@Test
	public void test6() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(15,1,2020),"16/1/2020");
	}
	@Test
	public void test7() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(15,2,2020),"16/2/2020");
	}
	@Test
	public void test8() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(15,11,2020),"16/11/2020");
	}
	@Test
	public void test9() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(15,12,2020),"16/12/2020");
	}
	@Test
	public void test10() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(15,6,2020),"16/6/2020");
	}
	@Test
	public void test11() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(1,6,2020),"2/6/2020");
	}
	@Test
	public void test12() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(2,6,2020),"3/6/2020");
	}
	@Test
	public void test13() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(15,6,2020),"16/6/2020");
	}
	
	@Test
	public void test14() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(30,6,2020),"1/7/2020");
	}
	@Test
	public void test15() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,3,2020),"1/4/2020");
	}

}

*Robust BVA


import static org.junit.Assert.*;
import org.junit.Test;
public class robustbva {

	@Test
	public void test() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(25,3,2019),"26/3/2019");
	}

	@Test
	public void test1() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,1950),"13/3/1950");
	}
	@Test
	public void test3() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,1915),"1/1/1916");
	}
	
	@Test
	public void test6() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,1915),"13/3/1915");
	}
	
	@Test
	public void test4() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(32,3,1914),"Enter valid dates");
	}
	@Test
	public void test5() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,13,2021),"Enter valid dates");
	}
	

	@Test
	public void test7() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,2020),"13/3/2020");
	}

}

*Worst-case BVA

import static org.junit.Assert.*;
import org.junit.Test;
public class worstcase {

	@Test
	public void test() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(25,3,2012),"26/3/2012");
	}

	@Test
	public void test1() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,1925),"13/3/1925");
	}
	@Test
	public void test2() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(30,3,1950),"31/3/1950");
	}
	@Test
	public void test3() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,2010),"1/1/2011");
	}
	public void test4() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,2010),"1/1/2010");
	}
	public void test5() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,2010),"1/1/2010");
	}
	
	@Test
	public void test6() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,1915),"13/3/1915");
	}
	@Test
	public void test7() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,1920),"13/3/1920");
	}
	@Test
	public void test8() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,2009),"1/1/2010");
	}
	@Test
	public void test9() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,2000),"1/1/2001");
	}


}







*Robust worst-case BVA

import static org.junit.Assert.*;

import org.junit.Test;

public class robustworstcase {

	@Test
	public void test() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(25,3,2012),"26/3/2012");
	}

	@Test
	public void test1() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,1925),"13/3/1925");
	}
	@Test
	public void test2() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(30,3,1950),"31/3/1950");
	}
	@Test
	public void test3() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,2010),"1/1/2011");
	}
	public void test4() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,2010),"1/1/2010");
	}
	public void test5() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,2010),"1/1/2010");
	}
	
	@Test
	public void test6() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,1915),"13/3/1915");
	}
	@Test
	public void test7() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,3,1920),"13/3/1920");
	}
	@Test
	public void test8() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,2009),"1/1/2010");
	}
	@Test
	public void test9() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,2000),"1/1/2001");
	}
	public void test12() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,2019),"1/1/2020");
	}
	@Test
	public void test13() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(31,12,1999),"1/1/2000");
	}
	@Test
	public void test10() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(32,3,1914),"Enter valid dates");
	}
	@Test
	public void test11() 
	{
		Next d1 = new Next();
		assertEquals(d1.nextd(12,13,2021),"Enter valid dates");
	}


}

```
# Next Date Equivalence
```
public class equind2pgm {

	//weak and strong normal test case
	@Test
	
	public void test_1() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(15,6,1912),"16/6/1912");
	}
	
	@Test
	public void test_2() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(10,6,1912),"11/6/1912");
	}
	@Test
	public void test_3() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(10,6,1900),"11/6/1900");
	}
	
	@Test
	public void test_4() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(10,5,1912),"11/5/1912");
	}
	
	@Test
	public void test_5() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(20,10,2010),"21/10/2010");
	} 
	
	//weak robust test cases
 
	@Test
	public void test3() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(-1,10,1912),"Invalid Values");
	}

	@Test
	public void test31() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(12,7,1912),"13/7/1912");
	}
	@Test
	public void test32() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(12,8,1912),"13/8/1912");
	}
	@Test
	public void test33() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(12,4,1912),"13/4/1912");
	}
	@Test
	public void test34() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(12,9,1912),"13/9/1912");
	}
	@Test
	public void test35() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(12,1,1912),"13/1/1912");
	}
	@Test
	public void test36() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(12,2,1912),"13/2/1912");
	}
	@Test
	public void test37() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(12,3,1912),"13/3/1912");
	}
	@Test
	public void test30() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(10,3,1912),"11/3/1912");
	}
	@Test
	public void test4() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(15,13,1912),"Invalid Values");
	}
	@Test
	public void test5() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(1,6,2200),"Invalid Values");
	}
	@Test
	public void test6() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(32,6,1912),"Invalid Values");
	}
	@Test
	public void test7() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(15,6,1811),"Invalid Values");
	}
	@Test
	public void test8() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(15,6,2013),"Invalid Values");
	}
	
	//strong robust test cases
	@Test
	public void test9() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(2,1,1912),"3/1/1912");
	}
	@Test
	public void test10() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(-1,3,1900),"Invalid Values");
	}
	@Test
	public void test11() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(15,0,1811),"Invalid Values");
	}
	@Test
	public void test12() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(33,12,1912),"Invalid Values");
	}
	@Test
	public void test13() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(15,-1,-1),"Invalid Values");
	}
	@Test
	public void test14() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(-1,6,-1),"Invalid Values");
	}
	@Test
	public void test15() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(-1,-1,-1),"Invalid Values");
	}
	@Test
	public void test16() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(31,12,2010),"1/1/2011");
	}
	@Test
	public void test17() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(30,11,2010),"1/12/2010");
	}
	
	//////leap
	@Test
	public void test18() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(3,2,2010),"4/2/2010");
	}

	@Test
	public void test19() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(28,2,2010),"1/3/2010");
	}
	@Test
	public void test20() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(20,2,2008),"21/2/2008");
	}
	@Test
	public void test21() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(29,2,2000),"1/3/2000");
	}
	@Test
	
	public void test22() 
	{
		nextdate ob1=new nextdate();
		assertEquals(ob1.nextday(28,2,1900),"1/3/1900");
	}

}

```

# Triangle Eclemma
```
public class triangleTest {

	@Test
	public void test() {
		triangle t1=new triangle();
		assertEquals(t1.op(1, 2, 3),"Not a Triangle");
	}
	@Test
	public void test12() {
		triangle t1=new triangle();
		assertEquals(t1.op(2, 1, 1),"Not a Triangle");
	}
	@Test
	public void test13() {
		triangle t1=new triangle();
		assertEquals(t1.op(2, 4, 2),"Not a Triangle");
	}


	@Test
	public void test1() {
		triangle t1=new triangle();
		assertEquals(t1.op(100, 100, 100),"Equilateral Triangle");
	}
	@Test
	public void test2() {
		triangle t1=new triangle();
		assertEquals(t1.op(4, 5, 6),"Scalen Triangle");
	}
	@Test
	public void test3() {
		triangle t1=new triangle();
		assertEquals(t1.op(4, 6, 6),"Isosceles Triangle");
	}
	@Test
	public void test4() {
		triangle t1=new triangle();
		assertEquals(t1.op(201, 201, 201),"Invalid");
	}
	@Test
	public void test5() {
		triangle t1=new triangle();
		assertEquals(t1.op(6, 6, 4),"Isosceles Triangle");
	}
	@Test
	public void test6() {
		triangle t1=new triangle();
		assertEquals(t1.op(4, 201, 7),"Invalid");
	}
	@Test
	public void test7() {
		triangle t1=new triangle();
		assertEquals(t1.op(4, 7, 201),"Invalid");
	}
	@Test
	public void test8() {
		triangle t1=new triangle();
		assertEquals(t1.op(0, 7, 201),"Invalid");
	}
	@Test
	public void test9() {
		triangle t1=new triangle();
		assertEquals(t1.op(7, 0, 201),"Invalid");
	}

	@Test
	public void test11() {
		triangle t1=new triangle();
		assertEquals(t1.op(7, 9, 0),"Invalid");
	}

}

```
