= Send a mail on gmail via python
:hp-tags: python, mail
:hp-image: /images/cat.jpg

Code to send a mail via gmail with an attachment 

[source,python]
----
import smtplib
from email.MIMEMultipart import MIMEMultipart
from email.MIMEText import MIMEText
from email.MIMEBase import MIMEBase
from email import encoders


fromaddr = ""
toaddr = ""
PASSWORD = ""

msg = MIMEMultipart()

msg['From'] = fromaddr
msg['To'] = toaddr
msg['Subject'] = "python test"

body = """Hey bro, that's a test ! \o/"""

msg.attach(MIMEText(body, 'plain'))

filename = "test.zip"
attachment = open(r'D://test.zip', "rb")

part = MIMEBase('application', 'octet-stream')
part.set_payload((attachment).read())
encoders.encode_base64(part)
part.add_header('Content-Disposition', "attachment; filename= %s" % filename)

msg.attach(part)

server = smtplib.SMTP('smtp.gmail.com', 587)
server.starttls()
server.login(fromaddr, PASSWORD)
text = msg.as_string()
server.sendmail(fromaddr, toaddr, text)
server.quit()
----