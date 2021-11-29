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
