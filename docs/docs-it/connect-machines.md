# Connettere le macchine a CARIcare

Per ultilizzare il CARIcare sulla vostre macchine le stesse dovranno essere connesse ad internet, Carimali 

## BlueDot / BlueDot Plus
Per connettere una BlueDot / Plus al CARIcare per prima cosa impostare la macchina in modalità MiniAP, se hai appena installato la scheda questo passaggio non sarà necessario quindi passa direttamente al punto successivo

1 **Impostare la modalità MiniAP**

   - Accendi la macchina, nella pagina iniziale premi il tasto settaggi macchina
   - Seleziona **System Manager**
   - Dal menù seleziona **Wifi**, se non dovesse essere presente tra le scelte segui le istruzioni che trovi nella sezione    troubleshooting
   - Inserisci la password (la stessa di amministrazione macchina)
   - Seleziona **Wifi: Parametri** 
   - Scorri fino all'ultima voce **Ripristina config originale** e conferma.
   - Riavvia la macchina, attendi la schermata di stato Wi-Fi, **Connection status** risulterà <p style="color:orange">Mini-AP</p>

2 **Configurare il Wi-Fi**
      Per questo passaggio sarà necessario un (verificare che device supporta) con la possibilità di connetterti tramite Wi-Fi

   - Connetti il device alla rete "Carimali_HotSpot"
   - Se entro pochi secondi il browser non si apre automaticamente sulla pagina 192.168.1.1, aprilo, digita manualmente 192.168.1.1 e conferma
   - Apri il tab Wi-Fi Services e completa in questo modo i seguenti campi
            **MQTT Broker Url** : mqtt.carimali.com
            **MQTT Port** : 1883
        Premi **Submit**   
   -   


### 1.1 

![BlueDot-img-connect](_images/logi-1.png)

## Armonia: Plus / Ultra

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam sed sapien a erat lacinia tempor. Phasellus nec vulputate metus. Morbi rhoncus odio suscipit est tristique volutpat. Pellentesque in mauris ut erat ornare tempus vel quis neque. Vestibulum massa nisl, molestie gravida imperdiet vitae, eleifend non nunc.

![Armonia-img-connect](_images/policy_pricy_1.png)



##  Troubleshoot connection problems

 n.b. CARIcare è in grado di mostrare se la macchina è connessa o disconnessa, tuttavia questo controllo viene fatto con un intervallo   di circa un minuto, quindi se la macchina è appena stata accessa o riavviata lasciare al sistema il tempo di aggiornarsi prima di verificare lo stato della connessione.
 
  - Il firmware installato in macchina deve essere una versione recente (elencare versioni firmware)
  - L'indirizzo del Broker MQTT deve essere: mqtt.carimali.com porta 1883
  - La passowrd remota deve essere 12345
  - Il seriale dev'essere inserito correttamente nel software della macchina
  - Service Dose Info, Service Status, Service Vending devono essere abilitati nell'area WiFi (solo per famiglia BlueDot)
  
  












