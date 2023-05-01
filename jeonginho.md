-<pre><code>
public class MyClass {
    public static void main(String args[]) {
        System.out.println("Hello World!");
    }
}

>>결과: Hello World!

import javax.swing.*;   
import java.awt.Dimension;
import java.awt.Toolkit;
public class HelloWorldGUIApp{
    public static void main(String[] args){
        javax.swing.SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                JFrame frame = new JFrame("HelloWorld GUI");
                frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                frame.setPreferredSize(new Dimension(800, 300));
                JLabel label = new JLabel("Hello World!!", SwingConstants.CENTER); //작은 창에 Hello World!! 라는 문구를 출력 시킴.
                frame.getContentPane().add(label);
                Dimension dim = Toolkit.getDefaultToolkit().getScreenSize();
                frame.setLocation(dim.width/2-400/2, dim.height/2-300/2);
                
                frame.pack();
                frame.setVisible(true);
            }
        });
    }
}

>> 자바에서 기본적인 출력법과 자바의 응용 분야에 대해서 학습했다.