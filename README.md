# Cloud-based-energy-monitor-.python
import requests
import time
import random

CLOUD_URL = "https://your-server.com/api/energy"

while True:
    voltage = 230
    current = random.uniform(1, 5)
    power = voltage * current

    data = {
        "voltage": voltage,
        "current": round(current, 2),
        "power_w": round(power, 2)
    }

    try:
        response = requests.post(CLOUD_URL, json=data, timeout=10)
        print("Uploaded:", data, response.status_code)
    except requests.RequestException as e:
        print("Upload failed:", e)

    time.sleep(10)
