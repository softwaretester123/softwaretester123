# NEXT DATE
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
		if (d >= 1 && d <= 31 && m >= 1 && m <= 12 && y >= 1819 && y <= 2019) {
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
