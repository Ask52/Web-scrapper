# Web-scrapper
API testing with Python and Selenium

Import requests
from bs4 import BeautifulSoup
import smtplib

URL = 'https://www.amazon.com/Wireless-Bluetooth-Headphones-Compatible-Paperwhite/dp/B07CPG3H22/ref=sr_1_4?crid=360UOQR3H9799&keywords=bluetooth+headphones&qid=1574903744&s=amazon-devices&sprefix=bluetooth+Head%2Camazon-devices%2C267&sr=1-4'

headers = {"User-Agent": 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36'}

def check_price():
    page = requests.get(URL, headers=headers)

    soup = BeautifulSoup(page.content, 'html.parser')

    title = soup.find(id="productTitle").get_text()
    price = soup.find(id="priceblock_ourprice").get_text()
    converted_price = float(price[0:5])

    if(converted_price < 1.800):
        send_mail()

    print(converted_price)
    print(title.strip())

    if(converted_price > 1.700):
        send_mail()

def send_mail():
    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.elho
    server.startls()
    server.elho()

    server.login('archita.kenis.ak@gmail.com', '123456')

    subject = 'Hey the price fell down'
    body = 'Check out the amazon link https://www.amazon.com/Wireless-Bluetooth-Headphones-Compatible-Paperwhite/dp/B07CPG3H22/ref=sr_1_4?crid=360UOQR3H9799&keywords=bluetooth+headphones&qid=1574903744&s=amazon-devices&sprefix=bluetooth+Head%2Camazon-devices%2C267&sr=1-4'
    msg = f"Subject: {subject}\n\n{body}"

    server.sendmail(
        'user1@gmail.com',
        'user1@gmail.com',
msg
    )

    print('EMAIL SENT')

    server.quit()
    check_price()
