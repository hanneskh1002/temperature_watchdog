# 🌡️ Home Assistant Temperature Watchdog Blueprint

A reusable Home Assistant automation blueprint to monitor temperature sensors and detect sensor failures.

This blueprint is designed for scenarios like:

* ❄️ Freezers (e.g. alarm if above -10 °C)
* 🧊 Refrigerators
* 🖥️ Server racks
* 🌿 Grow setups
* Any environment where **temperature stability matters**

---

## 🚀 Features

* ✅ Immediate alert when temperature exceeds a defined threshold
* 🔁 Repeating alerts every X minutes until the issue is resolved
* ⏱️ Detection of sensor failure (no updates for X hours)
* 🔧 Fully configurable per device
* ♻️ Reusable via Home Assistant Blueprint system
* 🧼 No helpers required

---

## ⚙️ Requirements

* Home Assistant (Blueprint support enabled)
* A temperature sensor entity (e.g. `sensor.xyz_temperature`)
* A working notify service (e.g. `notify.notify` or `notify.mobile_app_*`)

---

## 📦 Installation

### Option 1: Manual

1. Copy the YAML file into:

```
config/blueprints/automation/hannes/
```

2. Restart Home Assistant **or** reload automations

3. Go to:

```
Settings → Automations & Scenes → Blueprints
```

4. Import the blueprint

---

### Option 2: GitHub Import

Use the "Import Blueprint" feature in Home Assistant and paste the GitHub URL of this file.

---

## 🧠 How it works

The blueprint uses two trigger types:

* 🔄 **State trigger** → reacts immediately to temperature changes
* ⏱️ **Time pattern trigger** → ensures:

  * repeated alerts
  * detection of missing sensor updates

---

## 🔧 Configuration

When creating an automation from this blueprint, you can configure:

| Parameter                      | Description                               |
| ------------------------------ | ----------------------------------------- |
| **Temperature Sensor**         | The sensor to monitor                     |
| **Device Name**                | Name used in notifications                |
| **High Temperature Threshold** | Alarm if value exceeds this               |
| **Clear Threshold**            | Value where alarm is considered resolved  |
| **Repeat Interval**            | Minutes between repeated alerts           |
| **Sensor Timeout**             | Hours without update before failure alert |
| **Notify Service**             | Notification target                       |

---

## 📢 Example Use Case

**Freezer monitoring:**

* Threshold: `-10`
* Clear threshold: `-12`
* Repeat: `20 minutes`
* Timeout: `12 hours`

➡️ Result:

* Immediate alert if freezer warms up
* Repeated warning every 20 minutes
* Alert if sensor stops reporting

---

## ⚠️ Known Limitations

* The blueprint does not track alarm state persistently
  → This means alerts may repeat even after acknowledgment

* "Clear" notifications are not included by default
  → Can be added separately if required

---

## 💡 Recommended Enhancements

* Use with **Telegram / Mobile App notifications**
* Combine with:

  * sirens
  * lights
  * critical alerts (iOS/Android)

---

## 🧪 Tested With

* Zigbee temperature sensors
* ESPHome sensors
* MQTT-based sensors

---

## 🤝 Contributing

Feel free to:

* Open issues
* Suggest improvements
* Submit pull requests

---

## 📄 License

MIT License

---

## 👨‍🔧 Author

Created for practical real-world monitoring use cases.
Built with a focus on reliability and simplicity.
