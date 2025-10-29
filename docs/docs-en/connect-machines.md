# 1. Connecting Machines to CARIcare

To use **CARIcare**, **Carimali** and **Elektra** machines must be connected to the Internet.
The connection procedure varies depending on the machine model.

---

### BlueDot Line

To connect a **BlueDot** machine to the **CARIcare** platform, follow the instructions provided in the dedicated manual:

[Wi-Fi BlueDot Line](https://service.vea.ventures/media/docs/documentitems/IST.%20025.00.23.IT.pdf)

---

### Armonia Line

To connect an **Armonia** machine to the **CARIcare** platform, follow the instructions provided in the dedicated manual:

[Wi-Fi Armonia Line](https://service.vea.ventures/media/docs/documentitems/ist0090319-it.pdf)

---

### SilverAce Line

For **SilverAce** line machines, the connection procedure is described in the **technical manual – Chapter 5.8**.

[Wi-Fi SilverAce Line](https://service.vea.ventures/media/docs/documentitems/SM_SILVERACE_LB.05165.IT.04.pdf)

---

### Evok Line

TBD

---

## Troubleshooting Connection Issues

**Note:**
**CARIcare** updates the machine connection status approximately every minute.
After powering on or restarting a machine, wait for this interval before checking the connection status.

To ensure proper operation, verify that:

* The **installed firmware** is updated to the latest available version.
* **Server MQTT URL**: `mqtt.carimali.com`
* **MQTT Port**: `1883`
* The **remote password** is correct.
* The machine’s **serial number** is correctly entered in the software:

  * For **Armonia**: remove the alphabetic suffix, keep the six numeric digits, and add four zeros at the end.

  ```Example
   CA333333 -> 3333330000
  ```

  * For **BlueDot**, **Evok**, and **SilverAce**: remove only the alphabetic suffix, keeping the last six digits.

  ```Example
   CA333333 -> 333333
  ```