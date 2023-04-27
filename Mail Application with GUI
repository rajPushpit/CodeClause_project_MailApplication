import tkinter as tk
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart
from PIL import ImageTk, Image
from tkinter import Label

class MailApplication:
    def __init__(mail, master):
        mail.master = master
        mail.master.title("Mail Application")

# Set background image
        mail.bg_image = tk.PhotoImage(file='mail_images.png')
        bg_label = tk.Label(mail.master, image=mail.bg_image)
        bg_label.place(x=0, y=0, relwidth=1, relheight=1)

        # Create labels and input fields
        mail.to_label = tk.Label(master, text="To:",bg='red')
        mail.to_label.grid(row=0, column=0, padx=5, pady=5)
        mail.to_entry = tk.Entry(master,width=65)
        mail.to_entry.grid(row=0, column=1, padx=5, pady=5)

        mail.subject_label = tk.Label(master, text="Subject:",bg='red')
        mail.subject_label.grid(row=1, column=0, padx=5, pady=5)
        mail.subject_entry = tk.Entry(master,width=65)
        mail.subject_entry.grid(row=1, column=1, padx=5, pady=5)

        mail.message_label = tk.Label(master, text="Message:",bg='red')
        mail.message_label.grid(row=2, column=0, padx=5, pady=5)
        mail.message_text = tk.Text(master, height=10, width=50)
        mail.message_text.grid(row=2, column=1, padx=5, pady=5)

        # Create send button
        mail.send_button = tk.Button(master, text="Send", command=mail.send_email,bg='red')
        mail.send_button.grid(row=3, column=1, padx=5, pady=5)

    def send_email(self):
        # Get values from input fields
        to_address = self.to_entry.get()
        subject = self.subject_entry.get()
        message = self.message_text.get("1.0", "end")

        # Set up email message
        msg = MIMEMultipart()
        msg['To'] = to_address
        msg['Subject'] = subject
        msg.attach(MIMEText(message, 'plain'))

        # Send email
        smtp_server = 'smtp.gmail.com' # Replace with your SMTP server
        smtp_port = 587 # Replace with your SMTP port
        smtp_username = 'your_username@gmail.com' # Replace with your SMTP username
        smtp_password = 'your_password' # Replace with your SMTP password
        smtp_connection = smtplib.SMTP(smtp_server, smtp_port)
        smtp_connection.starttls()
        smtp_connection.login(smtp_username, smtp_password)
        smtp_connection.sendmail(smtp_username, to_address, msg.as_string())
        smtp_connection.quit()

        # Clear input fields
        self.to_entry.delete(0, "end")
        self.subject_entry.delete(0, "end")
        self.message_text.delete("1.0", "end")

# Create main window and run application
mail_win = tk.Tk()
app = MailApplication(mail_win)
mail_win.geometry('500x300+200+150')
mail_win.iconbitmap('emails-concept.ico')
mail_win.resizable(False, False)

mail_win.mainloop()
