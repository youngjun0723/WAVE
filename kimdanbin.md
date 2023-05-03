public class HelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello World!!");
    }
}


import javax.swing.*;   
import java.awt.Dimension;
import java.awt.Toolkit;
public class HelloWorldGUIApp{
    public static void main(String[] args){
        javax.swing.SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                JFrame frame = new JFrame("HelloWorld GUI");
                frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                frame.setPreferredSize(new Dimension(400, 300));
                JLabel label = new JLabel("Hello World!!", SwingConstants.CENTER);
                frame.getContentPane().add(label);
                Dimension dim = Toolkit.getDefaultToolkit().getScreenSize();
                frame.setLocation(dim.width/2-400/2, dim.height/2-300/2);

                frame.pack();
                frame.setVisible(true);
            }
        });
    }
}


6-2
public class Datatype{
	public static void main(String[]args) {
		System.out.println(6);//Number 숫자
		System.out.println("six");//String 문자열
		
		System.out.println("6");//String 6 문자열 6
		
		System.out.println(6+6);// 12 --> 숫자와 숫자를 결합해 더해주는 더하기 연산자
		System.out.println("6"+"6");// 66 --> 문자열일땐 더하기가 아니라 결합 연산자(문자열을 위한 연산)
		
		System.out.println(6*6);// 36
		//System.out.println("6"*"6");// --> 에러 / 문자열이란 데이터 타입은 곱하기를 할 수 없다
		
		System.out.println("1111".length());// 4  --> 문자열의 길이
		//System.out.println(1111.length());// --> 에러 / 숫자 천백십일 : 숫자는 숫자의 길이를 알려주는 연산은 없다
		
		//프로그래밍에서는 데이터 타입이 있다 , 데이터 타입별로 구분하는 이유는 타입별로 그 타입에 어울리는 연산 방법이 있기 때문에 엄격하게 구분
		
		
	}
}


6-3
public class Number {

	public static void main(String[] args) {
		
		//Operator 연산자 : +,-,*,/
		System.out.println(6 + 2); // 8
		System.out.println(6 - 2); // 4
		System.out.println(6 * 2); // 12
		System.out.println(6 / 2); // 3
		
		System.out.println(Math.PI); //3.141592653589793
		System.out.println(Math.floor(Math.PI)); // 3.0 / floor : 내림(바닥)
		System.out.println(Math.ceil(Math.PI)); // 4.0 / ceil : 올림(천장)

	}

}



6-4
public class StringApp {

	public static void main(String[] args) {
		
		System.out.println("Hello World"); //String 문자열 --> character들이 모여 있는 것
		//System.out.println('Hello World'); // 에러 / 자바에서는 작은 따옴표는 특수한 데이터 타입을 가리킨다 
		System.out.println('H'); // character 문자 / 한 글자를 표현하는 데이터 타입
		System.out.println("H"); // String 문자열
		
		System.out.println("Hello "
				+ "World"); // 줄바꿈이 아니다
		
		// new line 줄바꿈
		System.out.println("Hello \nWorld");
		
		// escape
	    System.out.println("Hello "World""); // Hello "World"를 출력하고싶은데 에러 / 큰 따옴표는 문자의 시작과 끝을 알리는 특수한 문자
		System.out.println("Hello \"World\""); // Hello "World" / 역슬래시를 앞에 붙이면 뒤에 따라오는 따옴표는 일반 문자열이 된다
	}

}


6-5
public class StringOperation {

	public static void main(String[] args) {
		
		System.out.println("Hello World".length()); // 11 / 글자가 11글자
		System.out.println("Hello, leezche ... bye.".replace("leezche","egoing")); // Hello, egoing ... bye.
		System.out.println("Hello, [[[name]]] ... bye.".replace("[[[name]]]","egoing")); // Hello, egoing ... bye.
	
	}

}

8-1
public class Variable {

	public static void main(String[] args) {
		
		int a=1; // Number -> integer(정수) ... -2, -1, 0, 1, 2 ...
		System.out.println(a);
		
	   double b=1.1; // real number(실수) -> double ... -2.0, -1.0, 0, 1.0, 2.0 ...
	   System.out.println(b);
	   
	   String c="Hello World";
	   System.out.println(c);
	   
	   // 변수의 타입을 지정하는 이유 : 변수의 데이터 타입을 바로바로 판단할 수 있기 떄문

	}

}


8-2
public class Letter {

	public static void main(String[] args) {
		
		String name = "leezch";
		System.out.println("Hello, "+name+" ... "+name+" ... egoing ... bye");
		// name이라는 변수를 지정하면, 자주 사용하는 데이터를 여러번 재사용 가능
		//이름을 수정할 경우, 변수의 값만 수정하면 되므로 효율적으로 처리할 수 있다.
		
		double VAT = 10.0;
		System.out.println(VAT);
		
		//변수는 값에 이름을 부여하는 것
		// 변수의 이름을 잘 지으면 코드의 의미를 파악할 떄 도움이 된다.
		// 변수를 사용하면 코드의 의미를 쉽게 파악할 수 있다.

	}

}



8-3
public class Casting {

	public static void main(String[] args) {
		
		double a = 1.1;
		double b = 1; // 자동으로
		double b2 = (double)1; // 수동으로(명시적으로)
		
		System.out.println(b); // 1.0 -> 정수지만 b라고 하는 double이라는 변수에 담길때 1이 실수형인 1.0으로 컴버팅이 될때 잃어버리는 값이 없다.
		
		//int c = 1.1; // 에러 -> 1.1이라는 실수를 정수로 바꿔줄 떄 0.1을 잃어버리는 현상(손실)이 생기기 때문
		double d = 1.1;
		int e = (int) 1.1; // 1 ->  정수 1이 된다
		System.out.println(e);
		
		// 1 to String
		String f = Integer.toString(1);
		System.out.println(f); // 1 -> 1의 데이터 타입이 숫자가 아니라 문자열이다
		System.out.println(f.getClass()); // .getClass()-> 변수가 갖고 있는 값이 어떤 데이터 타입인지 알려주는 코드
		
		
	}

}


9-1
.프로그램은 음악회와 같은 곳에서 연주할 곡들의 순서를 나타내는 것
.컴퓨터 각각의 작업들 하나하나로는 별로 의미가 없지만 내가 하고자 하는 일이 무엇이냐에 따라 그 일을 하기 위해서 필요한 각각의 작업들을 시간의 순서에 따라 실행되게 할 수 있다면 그것을 자동화를 할 수 있게 되는 것이다.
.컴퓨터 언어를 이용해서 프로그램을 만드는 것은 업무의 자동화된 처리를 위해서라고 할 수 있습니다

public class Program {

	public static void main(String[] args) {
		
		System.out.println(1);
		System.out.println(2);
		System.out.println(3);
		
		//이 작업은 그저 화면에 1, 2, 3을 순서대로 출력하는 작업을 수행합니다.
		//만약 3줄이 아니라 1억줄에 이르는 작업을 수행한다면 어떨까요?
		//굉장히 오래 걸리는 작업이라서 끝내기 위해서 하염없이 붙잡고 있어야 하는 작업이라면 어떨까요?
		//이런 경우에 컴퓨터 프로그래밍을 이용하여 사람이 잘 못하는 일을 기계에게 위임해서 자동화할 수 있습니다.
	}

}


9-2,3
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
 

10
이클립스에서 디버거 이용하기
디버거를 실행 : 이클립스 상단의 메뉴 도구 중 벌레 모양으로 생긴 버튼을 클릭
브레이크 포인트가 지정 : 코드 편집 창에서 줄 번호 왼편에서 더블클릭
Step Over : 다음 줄에 브레이크 포인트가 생성되어 그 지점까지만 코드가 실행
Resume : 다음 브레이크 포인트까지 실행되고, 만약 더 이상 브레이크 포인트가 없다면 끝까지 실행
Variable 탭에서 변수들을 확인
Step Into : 코드의 자세한 실행 과정을 들여다볼 수 있다
Step Return : 다시 원래의 코드로 돌아가고자 할 경우
