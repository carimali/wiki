# Machines

The **Machines** section enables viewing, searching, and managing the coffee machines connected to the **CARIcare** platform.
From this area it is possible to filter machines by various parameters, export counters, update firmware, manage recipes, or send remote commands.

<kbd>![machines-page-1](_images/machines-page-1.png)</kbd>

---

## Export counters to CSV

The **Export counters to CSV** button generates a CSV (Comma-Separated Values) file containing up-to-date counter data for the listed machines.
The resulting file can be used for analysis, statistics, or archiving of dispensing data.

<kbd>![machines-page-2](_images/machines-page-2.png)</kbd>

## Search filters

The upper part of the screen contains a set of **filters** that allow quick identification of one or more machines based on specific criteria.

Available fields:

* **Model** – Filters machines by model.
* **Connection** – Allows selection of *connected* or *disconnected* machines only.
* **Serial** – Direct search by unique serial number.

The **Advanced filters** button expands or collapses the search criteria display.

* **Customer** – Shows machines assigned to a specific customer.
* **Address** – Enables search by the machine’s location or site.
* **Firmware** – Filters by the installed firmware version.
* **Tags** – Allows selection of machines by assigned tags
  (e.g., selecting **Firmware update** filters machines for which a software update is available).

<kbd>![machines-page-3](_images/machines-page-3.png)</kbd>

---

## Machine list

The lower part of the page shows the **machine list** with key operational data, available in two display modes:

* **List view**
  Displays machines in a tabular format, one per row.
  Each entry includes:

  * **Image**
  * **Model**
  * **Serial**
  * **Customer**
  * **Installation address**
  * **Installed firmware** version
  * **Connection status**
  * **Tags**
  * **Actions**

  <kbd>![machines-page-4](_images/machines-page-4.png)</kbd>

* **Grid view**
  Displays machines as cards, with the same key information in a more compact layout.
  This mode enables faster visual recognition thanks to the model image.

  <kbd>![machines-page-5](_images/machines-page-5.png)</kbd>

The two modes can be toggled using the **List** or **Grid** buttons at the top right.
On **smartphone** devices, the default display is **list view**, optimized for screen size.

Each row or card represents a single machine.
The **Sel.** column or the checkbox next to each machine allows **multi-selection** to apply bulk actions.
The **CSV** button at the top right allows **exporting the displayed list** in **.csv** format.

---

### Status indicators

Each machine may display **icons or visual indicators** that provide information on operational status:

![Eye icon](_images/icona-occhio.png) <sup style='font-size:15px'>Allows [access to the overview page](docs-it/machine.md) of the selected machine.</sup>

From this page, it is possible to view in real time:

* **MAINTENANCE**

  <kbd>![machines-page-6](_images/machines-page-6.png)</kbd>

  * **Overall machine status**
  * **Recent dispensing**
  * **Operating temperatures (coffee and steam)**
  * **Global and partial counters**
  * **Washing cycles**
  * **Calibration parameters**
  * **Geographical location**
  * **Quarterly / annual maintenance**
  * **Coffee group cycle count**
  * **Dispensing in the last 24 hours**
  * **Product consumption** where available
  * **Connection status**


* **RECIPES**

  <kbd>![machines-page-7](_images/machines-page-7.png)</kbd>

  * **Import a recipe set**
  * **Recipes** list view / grid view

* **SETTINGS**

  <kbd>![machines-page-8](_images/machines-page-8.png)</kbd>

  * **Machine configuration**
  * **Firmware**
  * **Language**
  * **Payment system**
  * **Timezone**
  * **Brewer**
  * **Product consumption**
  * **Scheduled date for extraordinary maintenance**
  * **Counter reset and updates**

* **HISTORY**

  <kbd>![machines-page-9](_images/machines-page-9.png)</kbd>

  * **Errors** history
  * **Washing** history
  * **Firmware updates** history

* **PARAMETERS** (SilverAce models only with latest firmware)

  <kbd>![machines-page-10](_images/machines-page-10.png)</kbd>

  * **Clock management**
  * **Cleaning and maintenance**
  * **Display options**
  * **Machine parameters**

![Error icon](_images/icona-errore.png) <sup style='font-size:15px'>Indicates the presence of one or more **anomalies associated with the machine**.

* **invalid counters**: number of dispenses executed while the machine has been disconnected for more than three days.

  <kbd>![machines-page-14](_images/machines-page-14.png)</kbd>

  Select *Reset* to clear the dispensing count, or select *Fix* to add dispenses performed in offline mode to the sales history.

* **Communication anomaly with server**: the connection to the server is unstable.

  <kbd>![machines-page-143](_images/machines-page-13.png)</kbd>

  Select *Reset* to clear the anomaly.</sup>

---

## Actions on machines

By selecting one or more serial numbers, the **Perform an action on your machines** section appears at the bottom of the screen, grouping all applicable operational functions.

When multiple machines are selected simultaneously, some functions are unavailable and appear disabled: *Restart*, *Start*, *Shutdown*.

<kbd>![machines-page-11](_images/machines-page-11.png)</kbd>

* **Change recipe** – Allows **updating the recipe set** for the selected machines.
  The operation can be performed on **multiple machines simultaneously** (max. 10), provided they belong to **the same model** and have **the same configuration**.

* **Update firmware** – Starts the firmware update process for the selected machines only when the *Firmware update* tag is present.

* **Restart** – Performs a remote restart of the machine.

* **Start** – Reactivates a machine in a stopped state.

* **Shutdown** – Performs a remote shutdown.

* **Assign to** – Associates one or more machines with an existing customer.

* **Tag** – Assigns or modifies associated tags.

* **Export counters** – Generates a **CSV** file containing the updated counter data for the selected machines.

All operations are applied exclusively to the machines selected in the list.
