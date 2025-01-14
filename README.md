In that file there is the simple BMI code is present # Garbage

import javax.swing.*;
import java.awt.event.*;

public class BMICalculatorGUI {

    public static void main(String[] args) {
        
        JFrame frame = new JFrame("BMI Calculator");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(300, 200);

        
        JPanel panel = new JPanel();
        frame.add(panel);
        placeComponents(panel);

        
        frame.setVisible(true);
    }

    private static void placeComponents(JPanel panel) {
        panel.setLayout(null);

       
        JLabel weightLabel = new JLabel("Weight (kg):");
        weightLabel.setBounds(10, 20, 80, 25);
        panel.add(weightLabel);

        
        JTextField weightText = new JTextField(20);
        weightText.setBounds(100, 20, 165, 25);
        panel.add(weightText);

        
        JLabel heightLabel = new JLabel("Height (m):");
        heightLabel.setBounds(10, 50, 80, 25);
        panel.add(heightLabel);

        
        JTextField heightText = new JTextField(20);
        heightText.setBounds(100, 50, 165, 25);
        panel.add(heightText);

        
        JButton calculateButton = new JButton("Calculate BMI");
        calculateButton.setBounds(10, 80, 150, 25);
        panel.add(calculateButton);

        
        
        JLabel resultLabel = new JLabel("Your BMI is: ");
        resultLabel.setBounds(10, 110, 300, 25);
        panel.add(resultLabel);

       
        calculateButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                try {
                    double weight = Double.parseDouble(weightText.getText());
                    double height = Double.parseDouble(heightText.getText());
                    double bmi = weight / (height * height);
                    String category;

                    if (bmi < 18.5) {
                        category = "You are underweight.";
                    } else if (bmi >= 18.5 && bmi < 24.9) {
                        category = "You have a normal weight.";
                    } else if (bmi >= 25 && bmi < 29.9) {
                        category = "You are overweight.";
                    } else {
                        category = "You are obese.";
                    }

                    resultLabel.setText("Your BMI is: " + bmi + " - " + category);
                } catch (NumberFormatException ex) {
                    resultLabel.setText("Please enter valid numbers.");
                }
            }
        });
    }
}
