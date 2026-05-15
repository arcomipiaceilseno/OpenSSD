# OpenSSD

**SSD (Security System Device)** è un sistema di segnalazione ideato per permettere agli utenti di segnalare a distanza eventuali situazioni di pericolo all'interno di edifici pubblici. Il progetto nasce dall'analisi delle criticità nelle discoteche, proponendo una soluzione discreta e sicura per richiedere assistenza immediata.

## 📋 Descrizione del Progetto
Il sistema consente di inviare segnalazioni riguardanti problematiche programmabili dal gestore (come molestie, droga, rissa o emergenze sanitarie) attraverso un tastierino fisico posizionato in luoghi appartati della struttura, garantendo la massima discrezione per chi effettua la richiesta.

### Funzionalità principali:
* **Precisione della segnalazione:** Specifica il luogo della richiesta, la zona del pericolo e la tipologia di emergenza.
* **Gestione Gerarchica:** Le notifiche arrivano a figure specifiche (bodyguard o gestore) che possono accettare l'intervento o smistare il messaggio ad altri colleghi.
* **Rete Indipendente:** Opera su una rete chiusa e indipendente, garantendo il funzionamento anche in assenza di copertura cellulare o credito residuo dell'utente.
* **Meccanismo Anti-Errore:** Utilizza uno slider fisico di conferma per evitare invii accidentali.

## 🛠️ Architettura Hardware
Il sistema è basato sul microcontrollore **ESP32-C3** ed è composto da tre moduli principali:

### 1. Trasmettitore (Tastierino)
* **Input:** 6 pulsanti di selezione (luogo/tipo) e 1 slider di conferma.
* **Tecnologia:** Utilizza un latch **74HC373** per mantenere stabile lo stato logico del segnale.
* **Protezione:** Implementa un tempo di *cooldown* configurabile (circa 1 minuto) per evitare l'invio di allarmi multipli accidentali o la saturazione del sistema.

### 2. Smistatore (Hub Centrale)
* Agisce come ponte di comunicazione Wi-Fi.
* Riceve i pacchetti e li pubblica in un deposito dinamico in formato **JSON**, rendendoli accessibili ai dispositivi autorizzati.

### 3. Ricevitore (Dispositivo Mobile)
* **Hardware:** Dotato di schermo LCD per la visualizzazione dei dettagli e batteria al litio ricaricabile per la portabilità.
* **Interazione:** Permette all'operatore di accettare la richiesta (conferma visibile sul trasmettitore tramite LED) o di inoltrarla.

## 🌐 Interfacce di Gestione
Il progetto include tre interfacce web dedicate:
1.  **Pannello di Configurazione:** Per mappare i dispositivi, definire i ruoli e configurare le regole di comunicazione via LAN.
2.  **Interfaccia di Emergenza Smartphone:** Sistema di backup che genera una rete Wi-Fi locale per inviare segnalazioni via browser in caso di danni ai tasti fisici.
3.  **Canale Dati JSON:** Registro dinamico delle comunicazioni e delle configurazioni in tempo reale.

## 🚀 Ambiti di Applicazione
Grazie alla sua versatilità, SSD può essere installato in:
* Case di riposo e ospedali.
* Edifici scolastici e università.
* Stazioni ferroviarie, porti e aeroporti.
* Centri commerciali e uffici della Pubblica Amministrazione.

---

## 👥 Team di Sviluppo
* **Andrea Scarano** (Referente)
* **Andrea Bastoncino**
* **Francesco Grieco**

**Classe:** 5E
**Istituto:** ITI Galileo Ferraris
**A.S.:** 2025/2026
**Docente Tutor:** Pasquale Bucciero
