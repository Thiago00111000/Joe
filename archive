import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
from email.mime.application import MIMEApplication

def send_email(subject, body, to_email, attachment_path=None):
    from_email = 'seuemail@gmail.com'
    password = 'sua_senha_de_aplicativo'
    
    # Configuração do servidor
    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.starttls()
    server.login(from_email, password)
    
    # Criação do e-mail
    msg = MIMEMultipart()
    msg['From'] = from_email
    msg['To'] = to_email
    msg['Subject'] = subject
    
    msg.attach(MIMEText(body, 'plain'))
    
    if attachment_path:
        with open(attachment_path, 'rb') as file:
            part = MIMEApplication(file.read(), Name=attachment_path)
        part['Content-Disposition'] = f'attachment; filename="{attachment_path}"'
        msg.attach(part)
    
    # Envio do e-mail
    server.send_message(msg)
    server.quit()

# Exemplo de uso
send_email(
    subject='Relatório Diário',
    body='Olá, em anexo está o relatório diário.',
    to_email='destinatario@example.com',
    attachment_path='relatorio_diario.pdf'
)
