# pythondevelopmentdatasetcsv
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

def send_email(subject, body, to_email):
    # Your Gmail credentials
    gmail_user = 'your_email@gmail.com'
    gmail_password = 'your_password'
    # Email details
    from_email = gmail_user
    to_email = to_email
    # Create the MIME object
    msg = MIMEMultipart()
    msg['From'] = from_email
    msg['To'] = to_email
    msg['Subject'] = subject
    # Attach the body of the email
    msg.attach(MIMEText(body, 'plain'))
    # Connect to the SMTP server (in this case, Gmail's SMTP server)
    with smtplib.SMTP('smtp.gmail.com', 587) as server:
        server.starttls()  # Use TLS encryption
        server.login(gmail_user, gmail_password)  # Login to your Gmail account
        server.sendmail(from_email, to_email, msg.as_string())  # Send the email

# Example usage
subject = 'Test Email'
body = 'This is a test email sent using Python.'
to_email = 'recipient@example.com'
send_email(subject, body, to_email)
