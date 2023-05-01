JAVA Boostcourse
=============
2023-05-01 1일차 스터디
-------------

<pre>
<code>
public class HelloWorldApp {
	public static void main(String[] args) {
		System.out.println("Hello World!!");
	}
}
</pre>
</code>

- 데스크톱 애플리케이션 만들기

	- 기본 코드

<pre>
<code>
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
</pre>
</code>

- 수정해본 코드

<pre>
<code>
JLabel label = new JLabel("Hello World!!", SwingConstants.CENTER);
</pre>
</code>

