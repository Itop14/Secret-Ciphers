# Secret-Ciphers C#

This programme encrypts and decrypts messages using one of the following ciphers:
• Vernan
The cipher can ignore numbers, symbols and whitespace.

    using System;
    using System.Collections.Generic;
    using System.ComponentModel;
    using System.Data;
    using System.Drawing;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows.Forms;
    
    namespace Secret_Cipher_Volume1
    {
        public partial class Vernam : Form
        {
            public Vernam()
            {
                InitializeComponent();
            }
    
            private void Vernam_Load(object sender, EventArgs e)
            {
    
            }
    
            private void Encrypt_btn_Click(object sender, EventArgs e)
            {
                textBox1.Clear();
                string message = input_text.Text; // Users input is now in a string variable
                string key = KeyGenerator(message.Length); //gives the length of the string to the keygenerator funtion
                textBox1.Text = key;// Shows the generated KEy
    
                string encryptedmessage = Enc_and_Dec(message, key);// Encrypt the message
                Output_text.Text = encryptedmessage;// Display the encrypted message in the RichTextBox
            }
    
            private void Decrypt_btn_Click(object sender, EventArgs e)
            {
                textBox1.Clear();
    
                string encryptedmessage = input_text.Text;
                string key = Keyvalue.Text; // assigns the key to be whatever the user has entered
    
                string decryptedMessage = Enc_and_Dec(encryptedmessage, key);// Decrypt the message
                Output_text.Text = decryptedMessage;// Display the decrypted message in the RichTextBox
            }
    
            static string KeyGenerator(int length)
            {
                Random random = new Random();
                StringBuilder keymaker = new StringBuilder();// special class used to modify strings.
    
                for (int i = 0; i < length; i++)
                {
                    char randomc = (char)random.Next(32, 127);// Generate a random character
                    keymaker.Append(randomc);// add to the StringBuilder
                }
    
                return keymaker.ToString();
            }
    
            private string Enc_and_Dec(string message, string key)
            {
                StringBuilder output = new StringBuilder(); // special class used to modify strings.
    
                for (int i = 0; i < message.Length; i++)// XOR each character in the message with the corresponding character in the key
                {
                    char encryptedletter = (char)(message[i] ^ key[i]); // XOR 
                    output.Append(encryptedletter);// add to the output
                }
    
                return output.ToString();
            }
    
        }
    }
