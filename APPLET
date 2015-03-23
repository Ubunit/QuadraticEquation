# QuadraticEquation
/** THIS IS APPLET FOR QUADRATIC EQUATION */

package mainApplet;
import java.applet.Applet;
import java.awt.event.*;
import java.awt.*;
public class QuadraticEquation extends Applet implements ActionListener {
Button show_roots,show_discriminant;
Label discriminant,roots, function, a_,b_,c_;
TextField tf_a,tf_b,tf_c;
double a,b,c,D;
long a_long,b_long,c_long,D_long;
	public void init(){
		Font font = new Font("Monospased",Font.BOLD, 20);
		this.setLayout(new GridLayout(7,3));
		show_roots = new Button("Show roots");
		show_discriminant = new Button("Show discriminant");
		discriminant = new Label();
		discriminant.setFont(font);
		roots = new Label();
		roots.setFont(font);
		a_ = new Label(" a: ");
		a_.setFont(font);
		b_ = new Label(" b: ");
		b_.setFont(font);
		c_ = new Label(" c: ");
		c_.setFont(font);
		tf_a = new TextField();
		tf_b = new TextField();
		tf_c = new TextField();
		function = new Label(" ax^2 + bx + c = 0; (a != 0)");
		function.setFont(font);
		function.setForeground(Color.GRAY);
		this.add(function);
		this.add(new Label(""));
		this.add(a_);
		this.add(tf_a);
		this.add(b_);
		this.add(tf_b);
		this.add(c_);
		this.add(tf_c);
		this.add(show_discriminant);
		this.add(show_roots);
		this.add(discriminant);
		this.add(roots);
		show_roots.addActionListener(this);
		show_discriminant.addActionListener(this);
		this.setSize(700,300);
	}
private int radical(int num){
	int radical = 0;
	while(true){
		radical++;
		if(num == radical*radical){
			break;
		}
		if(num/2.5 < radical){
			radical = -1;
			break;
		}
	}
	return radical;
}
private String operation(double a,double b,double c){
	String answer = "Null";
	String number2 = "", number = "";
	int D_int = 2;
	double D,x1,x2;
    D = b*b - 4*a*c;
	String D_string = String.valueOf(D); 
	if(D_string.substring(D_string.indexOf(".")+1).equals("0")){
		 D_int = (int) D; 
	}
    if(D < 0){
    	answer = "Корней нет.";
    }else if(D == 0){
    	x1 = -b / (2*a);
    	String x1_string = String.valueOf(x1); 
    	if(x1_string.substring(x1_string.indexOf(".")+1).equals("0")){
    		int x1_int = (int) x1;
    		answer = "x = " + x1_int;
    	}else{
    	answer = "x = " + x1;
    	}
    }else{
    	if(D_string.indexOf(".")  != -1){
    		if(radical(D_int) == -1 ){
    			D *= 100000;
    			D_int = (int) D;
    			D = (double) D_int;
    			D /= 100000;
    			answer = "(" + -b + " +- sqrt(" + D + ")) / " + 2 * a;
    			//exit
    		}else{
    	x1 = -b + radical(D_int);
    	x1 = x1 / (2*a);
    	x2 = -b - radical(D_int);
    	x2 = x2 / (2*a);
    	number = number.valueOf(x1);
    	number2 = number2.valueOf(x2);
    	if(number.substring(number.indexOf(".") + 1).equals("0") && number2.substring(number2.indexOf(".") + 1).equals("0")){
    		int x1_int = (int) x1;
    		int x2_int = (int) x2;
    		answer = "x1 = " + x1_int + "; x2 = " + x2_int;
    	}else if(number.substring(number.indexOf(".") + 1).equals("0") || number2.substring(number2.indexOf(".") + 1).equals("0")){
    			if(number.substring(number.indexOf(".") + 1).equals("0")){
    				int x1_int = (int) x1;
    				answer = "x1 = " + x1_int + "; x2 = " + x2;
    			}else if(number2.substring(number2.indexOf(".") + 1).equals("0")){
    				int x2_int = (int) x2;
    				answer = "x1 = " + x1 + ";   x2 = " + x2_int + ";";
    			}
    	}else{
    	answer = "x1 = " + x1 + "; x2 = " + x2;
    	     }
    	
    		    }
    	   }
    	}
	return answer;
}
public void actionPerformed(ActionEvent ev) {
	if(tf_a.getText().equals("") || tf_b.getText().equals("") || tf_c.getText().equals("")){
		roots.setText("");
		discriminant.setForeground(Color.RED);
		discriminant.setText(" Введите все значения");
		return;
	}
	discriminant.setForeground(Color.BLACK);
	try{
	a = Double.parseDouble(tf_a.getText());
	if(a == 0){
		roots.setText("");
		discriminant.setForeground(Color.RED);
		discriminant.setText(" (a != 0)");
		return;
	}
	b = Double.parseDouble(tf_b.getText());
	c = Double.parseDouble(tf_c.getText());
	}catch(NumberFormatException ex){
		roots.setText("");
		discriminant.setForeground(Color.RED);
		discriminant.setText(" Введите правильные значения");
		tf_a.setText("");
		tf_b.setText("");
		tf_c.setText("");
		return;		
    }
	Button button = (Button) ev.getSource();
	if(button == show_discriminant){
    D = b*b - 4*a*c;
    String D_string = Double.toString(D);
    if(D_string.substring(D_string.indexOf(".") + 1).equals("0")){
    	D_long = (long) D;
    	discriminant.setText("" + D_long);
    }else discriminant.setText("" + D);
    }
	if(button == show_roots){
		if(discriminant.getText().equals(" Введите правильные значения") || 
		   discriminant.getText().equals(" Введите все значения") ||
		   discriminant.getText().equals(" (a != 0)")) discriminant.setText("");
	     String answer = operation(a,b,c);
	     roots.setText(answer);
  	}
  }
}
