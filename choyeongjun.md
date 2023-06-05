0501
4-1**HelloWorld**
public class HelloWorldApp {
	public static void main(String[] args) {
		System.out.println("Hello Word!!");
	}
}

4-3**Java 동작원리**
Java Source code.java

        |(compile)

Java Application.class

        |(Run)

Java Virtual Machine

        |(Run)

      computer          

5-1**Hello Java World**
import javax.swing.*;   
import java.awt.Dimension;
import java.awt.Toolkit;
public class HelloWorldGUIApp{
    public static void main(String[] args){
        javax.swing.SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                JFrame frame = new JFrame("HelloWorld GUI");
                frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                frame.setPreferredSize(new Dimension(800, 300)); //800의 수치를 400으로 변경하면 결과 창의 가로길이가 줄어듬
                JLabel label = new JLabel("Hello World!!", SwingConstants.RIGHT); /* RIGHT를 CENTER로 변경하면 결과 창에 나타나는 HelloWorld!! 단어가 가운데에 오는 것을 볼 수 있음*/
                frame.getContentPane().add(label);
                Dimension dim = Toolkit.getDefaultToolkit().getScreenSize();
                frame.setLocation(dim.width/2-400/2, dim.height/2-300/2);

                frame.pack();
                frame.setVisible(true);
            }
        });
    }
}

5-2**사물을 자바로 제어하기**
import com.pi4j.io.gpio.GpioController;
import com.pi4j.io.gpio.GpioFactory;
import com.pi4j.io.gpio.GpioPinDigitalOutput;
import com.pi4j.io.gpio.PinState;
import com.pi4j.io.gpio.RaspiPin;

public class HelloWorldRaspberryPi {

	public static void main(String[] args) throws InterruptedException {

		final GpioController gpio = GpioFactory.getInstance();
		final GpioPinDigitalOutput pin = gpio.provisionDigitalOutputPin(RaspiPin.GPIO_01, "PinLED", PinState.LOW);
		final int SHORT_INTERVAL = 200; //0.2초를 의미함
		final int LONG_INTERVAL = SHORT_INTERVAL * 3;
		final int LETTER_INTERVAL = SHORT_INTERVAL * 7;

		while (true) {
			// H
			pin.high();//high는 불이 켜지는 동작
			Thread.sleep(SHORT_INTERVAL);
			pin.low();//low는 불이 꺼지는 동작
			Thread.sleep(SHORT_INTERVAL);
			pin.high();
			Thread.sleep(SHORT_INTERVAL);
			pin.low();
			Thread.sleep(SHORT_INTERVAL);
			pin.high();
			Thread.sleep(SHORT_INTERVAL);
			pin.low();
			Thread.sleep(SHORT_INTERVAL);
			pin.high();
			Thread.sleep(SHORT_INTERVAL);
			pin.low();
			Thread.sleep(LETTER_INTERVAL);

			// e
			pin.high();
			Thread.sleep(SHORT_INTERVAL);
			pin.low();
			Thread.sleep(LETTER_INTERVAL);

			// l
			pin.high();
			Thread.sleep(SHORT_INTERVAL);
			pin.low();
			Thread.sleep(SHORT_INTERVAL);

			pin.high();
			Thread.sleep(LONG_INTERVAL);
			pin.low();
			Thread.sleep(SHORT_INTERVAL);

			pin.high();
			Thread.sleep(SHORT_INTERVAL);
			pin.low();
			Thread.sleep(SHORT_INTERVAL);
			pin.high();
			Thread.sleep(SHORT_INTERVAL);
			pin.low();
			Thread.sleep(LONG_INTERVAL);

			// l
			pin.high();
			Thread.sleep(SHORT_INTERVAL);
			pin.low();
			Thread.sleep(SHORT_INTERVAL);

			pin.high();
			Thread.sleep(LONG_INTERVAL);
			pin.low();
			Thread.sleep(SHORT_INTERVAL);

			pin.high();
			Thread.sleep(SHORT_INTERVAL);
			pin.low();
			Thread.sleep(SHORT_INTERVAL);
			pin.high();
			Thread.sleep(SHORT_INTERVAL);
			pin.low();
			Thread.sleep(LONG_INTERVAL);
		}
	}
}

===============================================

0502
6-1
데이터의 여러가지 종류가 있고 그 종류에 따라 수행할 수 있는 연산이 달라진다.

6-2**데이터타입**
public class Datatype{
    public static void main(String[] args) {
        System.out.println(6); // Number
        System.out.println("six"); // String
         
        System.out.println("6"); // String 6
         
        System.out.println(6+6); // 12  단순 더하기 연산처리
        System.out.println("6"+"6"); // 66  각각 문자열로 묶여있으면 결합연산자로 사용됨
         
        System.out.println(6*6); // 36
//      System.out.println("6"*"6"); //문자열은 곱하기 연산을 할 수가 없다
         
        System.out.println("1111".length()); // 4
//      System.out.println(1111.length()); // error
    }
}

6-3**데이터연산**
public class Number {
 
    public static void main(String[] args) {
        // Operator
        System.out.println(6 + 2); // 8
        System.out.println(6 - 2); // 4
        System.out.println(6 * 2); // 12
        System.out.println(6 / 2); // 3
 
        System.out.println(Math.PI); // 3.141592653589793
        System.out.println(Math.floor(Math.PI)); // 3.0  floor은 내림표현으로 소수점을 잘라버림
        System.out.println(Math.ceil(Math.PI)); // 4.0  ceil은 올림표현으로 실수 +1을 하면 됨  ex) Math.ceil(5.1);
                                                                                                // 6
         
    }
 
}

6-4**문자열의 표현**
public class StringApp {
 
    public static void main(String[] args) {
         
        // Character VS String 
        System.out.println("Hello World"); // String 문자열(Character들의 집합체)
        System.out.println('H'); // Character 한 글자를 표현하는 데이터 타입
        System.out.println("H"); // String
     
        System.out.println("Hello "
                + "World"); // 문자열과 문자열이 더해진 것(줄바꿈 안됨)
         
        // new line
        System.out.println("Hello \nWorld"); // 줄바꿈
         
        // escape
        System.out.println("Hello \"World\"");// Hello "World"      " 앞에 \를 넣어 줌으로써 "World"를 표현할 수 있게 됨
    }
 
}

6-5**문자열 다루기**
public class StringOperation {
 
    public static void main(String[] args) {
         
        System.out.println("Hello World".length()); // 11   length를 사용하면 문자열 내부의 글자 수를 파악할 수 있음
        System.out.println("Hello, [[[name]]] ... bye. ".replace("[[[name]]]", "duru")); /* replace - 특정 문자열을 다른 문자열로 교체하는 명령 내릴 수 있음*/
 
    }
 
}

===============================================

0503
8-1**변수의 정의(Variable)**
public class Variable {
 
    public static void main(String[] args) {
         
        int a = 1; // Number -> integer(정수) 
        System.out.println(a);
         
        double b = 1.1; // real number(실수) -> double 
        System.out.println(b);
         
        String c = "Hello World"; // 문자열
        System.out.println(c);
    }
 
}

8-2**변수의 효용**
public class Letter {
 
    public static void main(String[] args) {
        String name = "leezche";
        System.out.println("Hello, "+name+" ... "+name+" ... egoing ... bye");  // 개인적으로 C언어에서 scanf와 비슷한 원리라 생각함
         
        double VAT = 10.0;
        System.out.println(VAT); 

        //남들이봐도 쉽게 알아볼 수 있게 코딩을 이쁘게 해야함

    }
 
}

8-3**Casting**
public class Casting {
 
    public static void main(String[] args) {
         
        double a = 1.1;
        double b = 1;  // double을 사용했기 때문에 1.0 으로 출력            자동화
        double b2 = (double) 1; //                                        수동화 
         
        System.out.println(b);
         
        // int c = 1.1; 
        double d = 1.1; 
        int e = (int) 1.1; // (int)를 사용해 줌으로써 1.1 -> 1로 변경한 후 int e 에 적용. 즉, int e = 1; 과 동일한 의미
        System.out.println(e);
         
        // 1 to String 
        String f = Integer.toString(1);
        System.out.println(f.getClass());
 
 
    }
 
}

9-3**IoT 프로그램 만들기**
import org.opentutorials.iot.Elevator;
import org.opentutorials.iot.Lighting;
import org.opentutorials.iot.Security;
 
public class OkJavaGoInHome {
 
    public static void main(String[] args) {
         
        String id = "JAVA APT 507";
         
        // Elevator call 
        Elevator myElevator = new Elevator(id);
        myElevator.callForUp(1);
         
        // Security off 
        Security mySecurity = new Security(id);
        mySecurity.off();
         
        // Light on
        Lighting hallLamp = new Lighting(id+" / Hall Lamp");
        hallLamp.on();
         
        Lighting floorLamp = new Lighting(id+" / floorLamp");
        floorLamp.on();
 
    }
 
}

===============================================

0504
11-1**입력과 출력**
import javax.swing.JOptionPane;
 
import org.opentutorials.iot.DimmingLights;
import org.opentutorials.iot.Elevator;
import org.opentutorials.iot.Lighting;
import org.opentutorials.iot.Security;
 
public class OkJavaGoInHomeInput {
 
    public static void main(String[] args) {
         
        String id = JOptionPane.showInputDialog("Enter a ID"); // JOptionPane의 showInputDialog를 이용하여 정보를 String 데이터로 받음
        String bright = JOptionPane.showInputDialog("Enter a Bright level"); // 밝기또한 마찬가지
         
        // Elevator call 
        Elevator myElevator = new Elevator(id);
        myElevator.callForUp(1);
         
        // Security off 
        Security mySecurity = new Security(id);
        mySecurity.off();
         
        // Light on
        Lighting hallLamp = new Lighting(id+" / Hall Lamp");
        hallLamp.on();
         
        Lighting floorLamp = new Lighting(id+" / floorLamp");
        floorLamp.on();
         
        DimmingLights moodLamp = new DimmingLights(id+" moodLamp");
        moodLamp.setBright(Double.parseDouble(bright));
        moodLamp.on();
 
    }
 
}

11-2**arguments&parameter**
main 메소드의 args 파라미터를 이용하여 코드내의 값을 편하게 설정할 수 있음
public static void main(String[] args){
        String id = args[0];
        String bright = args[1];
}
argument 값을 다양하게 사용하여 결과값을 알아볼 수 있음
args는 문자열 배열로 여러개의 String 데이터가 들어있을 수 있음
인덱스는 0부터 시작함

===============================================

2023-05-08
-------------

* API(Application Programming Interface)

  자바 프로그램을 만들고 사용할 때의 단계 -> Computer - OS - Java - (API)Java Program...

  Application - 도구(System, Date, Math..)의 응용에 주목

  Program - 작업들의 시간적 순서에 주목

  자바 프로그램은 또 다른 자바 프로그램에서 사용될 수도 있고, 다른 프로그램에서 사용할 수 있도록 만들어둔 장치 역시 API이다.

* UI(User Interface)
  사용자가 우리가 만든 프로그램을 사용할 수 있도록 만들어둔 장치

* 자바 - 문서
  메소드(Method), 변수(Variable) < 클래스(Class) < 패키지(Package)
  메소드(Method) : floor, ceil...

* 인스턴스(Instance)

<pre><code>
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.PrintWriter; // 이게 없으면 작동x
public class InstanceApp {
 
    public static void main(String[] args) throws IOException{
         
        PrintWriter p1 = new PrintWriter("result1.txt");
        // PrintWriter 클래스의 이름을 p1으로 설정함.
        // new 키워드를 통한 인스턴스를 생성
        p1.write("Hello 1");
        p1.close();
         
        PrintWriter p2 = new PrintWriter("result2.txt");
        p2.write("Hello 2");
        p2.close();

    }
        // 생성자(Constructors)가 없으면 1회용 이다. (math)
		// 생성자가 있으면 생성자를 이용해 인스턴스를 만드는 것이 허용 되어있다.
}
</code></pre>

* 상속(Inheritance)

<pre><code>
java.lang.Object			 // 전체
	java.io.Writer  		 // Object 에게 상속받음
		jave.io.PrintWriter  // Writer 에게 상속받음
</code></pre>

* AccountingApp

<pre><code>
public class AccountingApp {

	public static void main(String[] args) {
		
		System.out.println("Value of supply : " +10000.0);
        System.out.println("VAT : " +(10000.0*0.1));
        System.out.println("Total : " +(10000.0+(10000.0*0.1)));
        System.out.println("Expense : " +(10000.0*0.3));
        System.out.println("Income : " +(10000.0-(10000.0*0.3)));
        System.out.println("Dividend 1 : " +(10000.0-(10000.0*0.3))*0.5);
        System.out.println("Dividend 2 : " +(10000.0-(10000.0*0.3))*0.3);
        System.out.println("Dividend 3 : " +(10000.0-(10000.0*0.3))*0.2);

        // Edit -> Find/Replace -> 숫자 10000.0을 12345.0으로 바꿀 수 있다
	}

}
</code></pre>

* 이전 프로그램에 변수 도입

<pre><code>
public class AccountingApp {
 
    public static void main(String[] args) {
 
        double valueOfSupply = 10000.0;
        double vatRate = 0.1;
        double expenseRate = 0.3;
        double vat = valueOfSupply * vatRate;
        double total = valueOfSupply + vat;
        double expense = valueOfSupply * expenseRate;
        double income = valueOfSupply - expense;
        double dividend1 = income * 0.5;
        double dividend2 = income * 0.3;
        double dividend3 = income * 0.2;
 
        System.out.println("Value of supply : " + valueOfSupply);
        System.out.println("VAT : " + vat);
        System.out.println("Total : " + total);
        System.out.println("Expense : " + expense);
        System.out.println("Income : " + income);
        System.out.println("Dividend 1 : " + dividend1);
        System.out.println("Dividend 2 : " + dividend2);
        System.out.println("Dividend 3 : " + dividend3);
 
    }
 
}
</code></pre>

***

2023-05-09
-------------

* 조건문

<pre><code>
if(income > 10000.0) {
    dividend1 = income * 0.5;
    dividend2 = income * 0.3;
    dividend3 = income * 0.2;
} else {
    dividend1 = income * 0.4;
    dividend2 = income * 0.2;
    dividend3 = income * 0.1;
}
</code></pre>

* 배열

<pre><code>
double rate1 = 0.5;
double rate2 = 0.3;
double rate3 = 0.2;
        
double dividend1 = income * rate1;
double dividend2 = income * rate2;
double dividend3 = income * rate3;
//변수가 많으면 변수가 더럽혀질 가능성이 커진다는 문제점이 있다. 세 개의 변수가 서로 같은 성격의 데이터라는 것이 분명하지 않다.

double[] dividendRates = new double[3];
// double형 데이터로 이루어진 배열이다.
// double형의 데이터를 3개를 담을 수 있는 수납상자
dividendRates[0] = 0.5;
dividendRates[1] = 0.3;
dividendRates[2] = 0.2;
        
double dividend1 = income * dividendRates[0];
double dividend2 = income * dividendRates[1];
double dividend3 = income * dividendRates[2];
</code></pre>

* 반복문

<pre><code>
int i = 0;
while(i < dividendRates.length) {
    System.out.println("Dividend : " + (income*dividendRates[i]) );
    i = i + 1;
}
</code></pre>

* 메소드
  
  메소드는 서로 연관된 코드를 그룹핑 해서 이름을 붙인 정리정돈의 상자이다.

<pre><code>
  public class AccountingMethodApp {
    public static double valueOfSupply;
    public static double vatRate;
    public static double expenseRate;
    public static void main(String[] args) { 
    // void main 밖으로 꺼내 전역변수로 설정한다.
        valueOfSupply = 10000.0;
        vatRate = 0.1;
        expenseRate = 0.3;
        print();
    }
 
    public static void print() {
        System.out.println("Value of supply : " + valueOfSupply);
        System.out.println("VAT : " + getVAT());
        System.out.println("Total : " + getTotal());
        System.out.println("Expense : " + getExpense());
        System.out.println("Income : " + getIncome());
        System.out.println("Dividend 1 : " + getDiviend1());
        System.out.println("Dividend 2 : " + getDiviend2());
        System.out.println("Dividend 3 : " + getDiviend3());
    }
 
    public static double getDiviend1() {
        return getIncome() * 0.5;
    }
    public static double getDiviend2() {
        return getIncome() * 0.3;
    }
    public static double getDiviend3() {
        return getIncome() * 0.2;
    }
 
    public static double getIncome() {
        return valueOfSupply - getExpense();
    }
 
    public static double getExpense() {
        return valueOfSupply * expenseRate;
    }
 
    public static double getTotal() {
        return valueOfSupply + getVAT();
    } 
 
    public static double getVAT() {
        return valueOfSupply * vatRate;
    }
 
}
</code></pre>

* 클래스

<pre><code>
class Accounting{
    public static double valueOfSupply;
    public static double vatRate;
    public static double expenseRate;
    public static void print() {
        System.out.println("Value of supply : " + valueOfSupply);
        System.out.println("VAT : " + getVAT());
        System.out.println("Total : " + getTotal());
        System.out.println("Expense : " + getExpense());
        System.out.println("Income : " + getIncome());
        System.out.println("Dividend 1 : " + getDiviend1());
        System.out.println("Dividend 2 : " + getDiviend2());
        System.out.println("Dividend 3 : " + getDiviend3());
    }
 
    public static double getDiviend1() {
        return getIncome() * 0.5;
    }
    public static double getDiviend2() {
        return getIncome() * 0.3;
    }
    public static double getDiviend3() {
        return getIncome() * 0.2;
    }
 
    public static double getIncome() {
        return valueOfSupply - getExpense();
    }
 
    public static double getExpense() {
        return valueOfSupply * expenseRate;
    }
 
    public static double getTotal() {
        return valueOfSupply + getVAT();
    } 
 
    public static double getVAT() {
        return valueOfSupply * vatRate;
    }
}
public class AccountingClassApp {
     
    public static void main(String[] args) {
        Accounting.valueOfSupply = 10000.0;
        Accounting.vatRate = 0.1;
        Accounting.expenseRate = 0.3;
        Accounting.print();
        // anotherVariable = ...;
        // anotherMethod = ...;
    }
}
</code></pre>

* 인스턴스

  하나의 클래스를 복제해서 서로 다른 데이터의 값과 서로 같은 메소드를 가진 복제본을 만드는 것이다.

<pre><code>
public class AccountingClassApp {
	
	public static void main(String[] args) {
		Accounting.valueOfSupply = 10000.0;
		Accounting.vatRate = 0.1;
		Accounting.expenseRate = 0.3;	
		Accounting.print();
		//...
		Accounting.valueOfSupply = 20000.0;
		Accounting.vatRate = 0.05;
		Accounting.expenseRate = 0.2;	
		Accounting.print();
		//...
		
		Accounting.valueOfSupply = 20000.0;
		Accounting.vatRate = 0.05;
		Accounting.expenseRate = 0.2;	
		Accounting.print();
		
	}
}
// 이 과정이 빈번하게 발샐한다고 한다면 이렇게 클래스의 내부적인 상태를 바꾸는 행위가 버그를 우발할 가능성이 매우 높다. 
</code></pre>

***

2023-05-10
-------------
