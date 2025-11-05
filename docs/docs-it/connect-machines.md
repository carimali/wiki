# 1. Connettere le macchine a CARIcare

Per utilizzare **CARIcare** è necessario che le macchine **Carimali** ed **Elektra** siano connesse a Internet.
La procedura di connessione varia in base al modello di macchina.

---

### Linea BlueDot

Per la connessione di una macchina **BlueDot** alla piattaforma **CARIcare**, seguire le istruzioni riportate nel manuale dedicato:

[Wi-Fi Linea BlueDot](https://service.vea.ventures/media/docs/documentitems/IST.%20025.00.23.IT.pdf)

---

### Linea Armonia

Per la connessione di una macchina **Armonia** alla piattaforma **CARIcare**, seguire le istruzioni riportate nel manuale dedicato:

[Wi-Fi Linea Armonia](https://service.vea.ventures/media/docs/documentitems/ist0090319-it.pdf)

---

### Linea SilverAce

Per le macchine della **linea SilverAce**, la procedura di connessione è descritta nel **manuale tecnico – Capitolo 5.8**.

[Wi-Fi Linea SilverAce](https://service.vea.ventures/media/docs/documentitems/SM_SILVERACE_LB.05165.IT.04.pdf)

---

### Linea Evok

TBD


---

## Risoluzione dei problemi di connessione

**Nota:**
**CARIcare** aggiorna lo stato di connessione delle macchine con un intervallo di circa un minuto.
Dopo l’accensione o il riavvio di una macchina, è necessario attendere questo tempo prima di verificare lo stato di connessione.

Per garantire il corretto funzionamento, verificare che:

* Il **firmware installato** sia aggiornato all’ultima versione disponibile.
* **Server MQTT URL**: `mqtt.carimali.com`
* **MQTT Port**: `1883`
* La **password remota** sia corretta.
* Il **numero seriale** della macchina sia inserito correttamente nel software:

  * Per **Armonia**: rimuovere il suffisso alfabetico, mantenere le sei cifre numeriche e aggiungere quattro zero finali.
  ```Esempio
   CA333333 -> 3333330000
````
  * Per **BlueDot**, **Evok** e **SilverAce**: rimuovere solo il suffisso alfabetico, mantenendo le sei cifre finali.
  ```Esempio
   CA333333 -> 333333
````