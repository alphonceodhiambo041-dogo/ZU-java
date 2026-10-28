


import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class RadioButtonDemo extends JFrame implements ActionListener {
    
    private JRadioButton birdButton, catButton, dogButton, rabbitButton, pigButton;
    private ButtonGroup petGroup;
    private JLabel imageLabel;

    public RadioButtonDemo() {
        setTitle("RadioButtonDemo");
        setSize(500, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout(10, 10));
        setLocationRelativeTo(null);

        // Left Panel - Radio Buttons
        JPanel radioPanel = new JPanel();
        radioPanel.setLayout(new BoxLayout(radioPanel, BoxLayout.Y_AXIS));
        radioPanel.setBorder(BorderFactory.createEmptyBorder(20, 20, 20, 20));

        birdButton = new JRadioButton("Bird");
        catButton = new JRadioButton("Cat");
        dogButton = new JRadioButton("Dog");
        rabbitButton = new JRadioButton("Rabbit");
        pigButton = new JRadioButton("Pig");

        // Only one can be selected at a time
        petGroup = new ButtonGroup();
        petGroup.add(birdButton);
        petGroup.add(catButton);
        petGroup.add(dogButton);
        petGroup.add(rabbitButton);
        petGroup.add(pigButton);

        // Listen for clicks
        birdButton.addActionListener(this);
        catButton.addActionListener(this);
        dogButton.addActionListener(this);
        rabbitButton.addActionListener(this);
        pigButton.addActionListener(this);

        radioPanel.add(birdButton);
        radioPanel.add(catButton);
        radioPanel.add(dogButton);
        radioPanel.add(rabbitButton);
        radioPanel.add(pigButton);

        // Center Panel - Where pet image/text appears
        imageLabel = new JLabel("Select a pet", SwingConstants.CENTER);
        imageLabel.setFont(new Font("Arial", Font.BOLD, 18));
        imageLabel.setBorder(BorderFactory.createLineBorder(Color.GRAY));

        add(radioPanel, BorderLayout.WEST);
        add(imageLabel, BorderLayout.CENTER);

        // Default - Pig selected like in assignment picture
        pigButton.setSelected(true);
        imageLabel.setText("Pig Selected");
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        String pet = e.getActionCommand();
        
        // 1. Show Message Box - REQUIRED BY ASSIGNMENT
        JOptionPane.showMessageDialog(this,
                "You selected: " + pet,
                "Pet Selection",
                JOptionPane.INFORMATION_MESSAGE);

        // 2. Update center display
        // If you have images: imageLabel.setIcon(new ImageIcon(pet + ".png"));
        imageLabel.setText(pet + " Selected");
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            new RadioButtonDemo().setVisible(true);
        });
    }
}