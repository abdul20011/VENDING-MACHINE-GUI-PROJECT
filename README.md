# VENDING-MACHINE-GUI-PROJECT
import java.awt.EventQueue;

import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.border.EmptyBorder;
import javax.swing.JTextField;
import javax.swing.JLabel;
import java.awt.Font;
import javax.swing.border.TitledBorder;
import javax.swing.JCheckBox;
import javax.swing.JButton;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

public class Vendingmachine extends JFrame {

	private JPanel contentPane;
	private JTextField txtInsert;
	private JTextField txtChange;

	/**
	 * Launch the application.
	 */
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					Vendingmachine frame = new Vendingmachine();
					frame.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the frame.
	 */
	public Vendingmachine() {
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100, 100, 450, 300);
		contentPane = new JPanel();
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));

		setContentPane(contentPane);
		contentPane.setLayout(null);
		
		JLabel lblNewLabel = new JLabel("Vending Machine");
		lblNewLabel.setBounds(161, 6, 134, 19);
		lblNewLabel.setFont(new Font("Lucida Grande", Font.BOLD, 15));
		contentPane.add(lblNewLabel);
		
		JLabel lblNewLabel_1 = new JLabel("Insert Money");
		lblNewLabel_1.setBounds(93, 42, 81, 16);
		contentPane.add(lblNewLabel_1);
		
		txtInsert = new JTextField();
		txtInsert.setBounds(186, 37, 130, 26);
		contentPane.add(txtInsert);
		txtInsert.setColumns(10);
		
		JLabel lblNewLabel_2 = new JLabel("Change:");
		lblNewLabel_2.setBounds(113, 74, 61, 16);
		contentPane.add(lblNewLabel_2);
		
		txtChange = new JTextField();
		txtChange.setBounds(186, 69, 130, 26);
		contentPane.add(txtChange);
		txtChange.setColumns(10);
		
		JPanel panel = new JPanel();
		panel.setBorder(new TitledBorder(null, "Select an item", TitledBorder.LEADING, TitledBorder.TOP, null, null));
		panel.setBounds(6, 121, 438, 92);
		contentPane.add(panel);
		panel.setLayout(null);
		
		JCheckBox cbSprite = new JCheckBox("Sprite ($1.50)");
		cbSprite.setBounds(6, 22, 128, 23);
		panel.add(cbSprite);
		
		JCheckBox cbcoke = new JCheckBox("coke ($1.75)");
		cbcoke.setBounds(6, 57, 128, 23);
		panel.add(cbcoke);
		
		JCheckBox cbwater = new JCheckBox("water ($1.00)");
		cbwater.setBounds(146, 22, 128, 23);
		panel.add(cbwater);
		
		JCheckBox cbPepsi = new JCheckBox("Pepsi ($1.50)");
		cbPepsi.setBounds(146, 57, 128, 23);
		panel.add(cbPepsi);
		
		JCheckBox cblemon = new JCheckBox("lemon ($2.00)");
		cblemon.setBounds(263, 22, 128, 23);
		panel.add(cblemon);
		
		JCheckBox cbpower = new JCheckBox("power($1.75)");
		cbpower.setBounds(263, 57, 128, 23);
		panel.add(cbpower);
		
		JButton btnNewButton = new JButton("Purchase");
		btnNewButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				double cost =0;
				if (cbSprite.isSelected())
					cost+=1.50;
				if (cbwater.isSelected())
					cost+=1.00;
				if (cbcoke.isSelected())
					cost+=1.75;
				if (cblemon.isSelected())
					cost+=2.00;
				if (cbpower.isSelected())
					cost+=1.75;
				if (cbPepsi.isSelected())
					cost+=1.50;
              double insertedMoney=Double.parseDouble(txtInsert.getText());
              double change=insertedMoney - cost;
              txtChange.setText(""+change);
          
			}
		});
		btnNewButton.setBounds(6, 237, 117, 29);
		contentPane.add(btnNewButton);
		
		JButton btnReset = new JButton("Reset");
		btnReset.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				txtInsert.setText("");
				cbSprite.setSelected(false);
				cbcoke.setSelected(false);
				cbwater.setSelected(false);
				cblemon.setSelected(false);
				cbpower.setSelected(false);
				cbPepsi.setSelected(false);


			}
		});
		btnReset.setBounds(157, 237, 117, 29);
		contentPane.add(btnReset);
		
		JButton btnQuit = new JButton("Quit");
		btnQuit.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				System.exit(0);
			}
		});
		btnQuit.setBounds(299, 237, 117, 29);
		contentPane.add(btnQuit);
	}
}
