import time
import board
import busio
import requests
from adafruit_bmp280 import Adafruit_BMP280_I2C
from adafruit_ads1x15.ads1115 import ADS1115
from adafruit_ads1x15.analog_in import AnalogIn

THINGSPEAK_API_KEY = "K3DYONH5QUMKSZ36"
THINGSPEAK_URL = "https://api.thingspeak.com/update"

i2c = busio.I2C(board.SCL, board.SDA)

bmp280 = Adafruit_BMP280_I2C(i2c, address=0x76)

ads = ADS1115(i2c, address=0x48)
ads.gain = 1

mq7 = AnalogIn(ads, 0)
mq135 = AnalogIn(ads, 1)

def calculate_co_level(voltage):
    return round(voltage * 100, 2)

def calculate_hazardous_level(voltage):
    return round(voltage * 200, 2)

try:
    while True:
        try:
            temperature = round(bmp280.temperature, 2)
            pressure = round(bmp280.pressure, 2)

            mq7_voltage = mq7.voltage
            mq135_voltage = mq135.voltage

            co_level = calculate_co_level(mq7_voltage)
            hazardous_level = calculate_hazardous_level(mq135_voltage)

            data = {
                "api_key": THINGSPEAK_API_KEY,
                "field1": temperature,
                "field2": pressure,
                "field3": co_level,
                "field4": hazardous_level
            }

            response = requests.post(THINGSPEAK_URL, data=data)

            if response.status_code == 200:
                print(f"Data sent successfully: {data}")
            else:
                print(f"Failed to send data: HTTP {response.status_code}")

        except Exception as e:
            print(f"Error: {e}")

        time.sleep(15)

except KeyboardInterrupt:
    print("\nExiting...")
