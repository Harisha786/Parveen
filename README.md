import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class TrafficLightSimulation extends JFrame implements ActionListener {

    JRadioButton redButton, yellowButton, greenButton;
    ButtonGroup group;
    JPanel panel;
    String currentColor = "";

    public TrafficLightSimulation() {
        setTitle("Traffic Light Simulation");
        setSize(300, 400);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLayout(new FlowLayout());

        // Create radio buttons
        redButton = new JRadioButton("Red");
        yellowButton = new JRadioButton("Yellow");
        greenButton = new JRadioButton("Green");

        // Group the buttons
        group = new ButtonGroup();
        group.add(redButton);
        group.add(yellowButton);
        group.add(greenButton);

        // Add action listeners
        redButton.addActionListener(this);
        yellowButton.addActionListener(this);
        greenButton.addActionListener(this);

        // Panel to draw light
        panel = new JPanel() {
            protected void paintComponent(Graphics g) {
                super.paintComponent(g);
                g.setColor(Color.BLACK);
                g.fillRect(100, 50, 80, 200);

                g.setColor(currentColor.equals("Red") ? Color.RED : Color.GRAY);
                g.fillOval(110, 60, 60, 60);

                g.setColor(currentColor.equals("Yellow") ? Color.YELLOW : Color.GRAY);
                g.fillOval(110, 120, 60, 60);

                g.setColor(currentColor.equals("Green") ? Color.GREEN : Color.GRAY);
                g.fillOval(110, 180, 60, 60);
            }
        };

        panel.setPreferredSize(new Dimension(300, 300));
        add(redButton);
        add(yellowButton);
        add(greenButton);
        add(panel);
        setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        if (e.get
