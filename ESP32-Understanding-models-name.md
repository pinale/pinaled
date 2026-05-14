# Guida alle Famiglie ESP32, Moduli WROOM/WROVER e Board di Sviluppo

## Introduzione

Nel mondo ESP32 esistono tre livelli distinti che spesso vengono confusi:

```text
CHIP → MODULO → BOARD
```

Esempio reale:

```text
ESP32-S3 → ESP32-S3-WROOM-1 → ESP32-S3-DevKitC-1
```

Dove:

* ESP32-S3 = microcontrollore
* ESP32-S3-WROOM-1 = modulo completo
* ESP32-S3-DevKitC-1 = scheda di sviluppo finale

---

# 1. Il CHIP (microcontrollore)

Il chip è il vero microcontrollore progettato da Espressif.

Le principali famiglie sono:

| Famiglia | Core               | Wi‑Fi    | Bluetooth           | USB nativa | Note principali             |
| -------- | ------------------ | -------- | ------------------- | ---------- | --------------------------- |
| ESP32    | Dual core Xtensa   | Sì       | BT + BLE            | No         | Modello storico più diffuso |
| ESP32-S2 | Single core Xtensa | Sì       | No                  | Sì         | USB e sicurezza             |
| ESP32-S3 | Dual core Xtensa   | Sì       | BLE                 | Sì         | AI, display, USB HID        |
| ESP32-C3 | Single core RISC‑V | Sì       | BLE                 | Sì         | Economico e basso consumo   |
| ESP32-C6 | RISC‑V             | Sì       | BLE                 | Sì         | Wi‑Fi 6 e Thread            |
| ESP32-H2 | RISC‑V             | No Wi‑Fi | BLE + Zigbee/Thread | No         | Domotica e Matter           |

---

## ESP32 classico

Caratteristiche:

* dual core Xtensa fino a 240 MHz
* Wi‑Fi 2.4 GHz
* Bluetooth classico + BLE
* enorme ecosistema
* compatibile con Arduino IDE, ESP-IDF, PlatformIO

Utilizzi tipici:

* automazione
* sensori IoT
* web server
* piccoli display
* relè e controllo dispositivi

---

## ESP32-S2

Caratteristiche:

* single core
* USB nativa
* maggiore attenzione alla sicurezza
* niente Bluetooth

Utilizzi tipici:

* dispositivi USB
* strumenti embedded
* tastiere/macropad
* firmware con USB diretta

---

## ESP32-S3

Evoluzione moderna dell’ESP32.

Caratteristiche:

* dual core
* USB nativa
* BLE
* accelerazioni vettoriali per AI
* migliore gestione display e camera
* molto usato con LVGL

Utilizzi tipici:

* display touch
* GUI avanzate
* videocamere
* audio
* TinyML / AI edge
* HID USB

---

## ESP32-C3

Versione economica e moderna.

Caratteristiche:

* architettura RISC‑V
* single core
* consumi ridotti
* BLE + Wi‑Fi
* costo contenuto

Utilizzi tipici:

* sensori
* dispositivi a batteria
* piccoli nodi IoT
* BLE beacon

---

# 2. Il MODULO

Il chip nudo è difficile da usare direttamente.

Per questo Espressif produce moduli già pronti che includono:

* microcontrollore ESP32
* memoria flash
* antenna RF
* quarzo
* circuiteria radio
* eventuale PSRAM

Il modulo è il piccolo componente metallico schermato saldato sopra la board.

---

# 3. Differenza tra WROOM e WROVER

## WROOM

Modulo standard.

Generalmente include:

* flash integrata
* antenna PCB o IPEX
* nessuna PSRAM aggiuntiva

Ideale per:

* IoT standard
* sensori
* automazione
* piccoli web server
* piccoli display

Esempi:

* ESP32-WROOM-32
* ESP32-S3-WROOM-1

---

## WROVER

Versione potenziata del modulo.

Aggiunge:

* PSRAM esterna

La PSRAM serve per:

* buffer grafici
* gestione immagini
* videocamere
* audio
* AI
* framebuffer grandi

Utilizzi tipici:

* ESP32-CAM
* display avanzati
* LVGL
* elaborazione immagini

Esempio:

* ESP32-WROVER

---

# 4. PSRAM: cosa significa

La PSRAM è memoria RAM aggiuntiva esterna.

Differenze:

| Tipo memoria | Uso                           |
| ------------ | ----------------------------- |
| SRAM interna | velocissima ma limitata       |
| PSRAM        | più lenta ma molto più grande |

La PSRAM è utile quando servono:

* immagini
* grandi array
* buffer audio
* framebuffer display
* AI locale

---

# 5. ESP32-S3 e WROOM/WROVER

ESP32-S3 è il chip.

Poi esistono moduli basati su quel chip.

Esempi:

| Modulo           | Basato su |
| ---------------- | --------- |
| ESP32-S3-WROOM-1 | ESP32-S3  |
| ESP32-S3-WROOM-2 | ESP32-S3  |

Nella generazione S3 la distinzione WROVER viene usata molto meno.

Molti moduli S3 hanno già PSRAM integrata pur chiamandosi ancora WROOM.

---

## Esempio di sigla completa

```text
ESP32-S3-WROOM-1-N16R8
```

Significato:

| Parte    | Significato |
| -------- | ----------- |
| ESP32-S3 | chip        |
| WROOM-1  | tipo modulo |
| N16      | 16 MB flash |
| R8       | 8 MB PSRAM  |

Altro esempio:

```text
ESP32-WROOM-32
```

Significa:

* chip ESP32 classico
* modulo WROOM
* generalmente senza PSRAM

---

# 6. La BOARD di sviluppo finale

La board è la scheda completa utilizzata dallo sviluppatore.

Include:

* modulo ESP32
* connettore USB
* convertitore USB-seriale
* regolatore 3.3V
* pulsanti RESET/BOOT
* pin GPIO esposti

Le board sono progettate per:

* breadboard
* prototipazione
* sviluppo firmware
* debugging

---

# 7. DevKit

"DevKit" significa semplicemente:

> Development Kit

cioè una scheda pensata per sviluppo e prototipazione.

Esempi:

* ESP32-DevKitC
* ESP32-S3-DevKitC-1
* DevKit V1

Caratteristiche tipiche:

* layout standard
* pin facilmente accessibili
* USB integrata
* documentazione ufficiale

---

# 8. NodeMCU

Originariamente NodeMCU era:

* un firmware Lua
* una board ESP8266

Nel tempo il nome è stato riutilizzato per molte board ESP32 compatibili.

Oggi “NodeMCU ESP32” generalmente significa:

* board compatta
* compatibile breadboard
* USB integrata
* economica

Non è uno standard tecnico preciso.

---

# 9. DOIT

DOIT è un produttore.

La famosa:

```text
DOIT ESP32 DEVKIT V1
```

è una delle board ESP32 più diffuse.

Tipicamente monta:

* ESP32-WROOM-32

Caratteristiche:

* economica
* compatibile Arduino IDE
* molto diffusa nei tutorial

---

# 10. Altri produttori importanti

| Produttore   | Caratteristiche               |
| ------------ | ----------------------------- |
| Espressif    | board ufficiali               |
| LilyGO       | display, LoRa, GPS            |
| M5Stack      | moduli industriali e modulari |
| Wemos/LOLIN  | board compatte                |
| Seeed Studio | serie XIAO                    |
| Adafruit     | documentazione eccellente     |
| Waveshare    | display e accessori           |

---

# 11. Form factor delle board

Il form factor descrive:

* dimensioni
* disposizione pin
* connettori
* compatibilità meccanica

---

## DevKit standard

Caratteristiche:

* abbastanza largo
* molti GPIO disponibili
* USB laterale
* ottimo per prototipi

Contro:

* può occupare entrambe le metà della breadboard

---

## NodeMCU style

Caratteristiche:

* stretto
* compatibile breadboard
* più compatto

Molto usato per:

* piccoli prototipi
* progetti maker

---

## Mini / Nano

Board molto piccole.

Esempi:

* XIAO ESP32
* ESP32-C3 Mini

Ideali per:

* wearable
* batteria
* dispositivi embedded

---

## M5Stack

Form factor modulare.

Include spesso:

* display
* case
* batteria
* speaker
* sensori

Molto usato in:

* industriale
* prototipi rapidi
* IoT avanzato

---

# 12. Antenne

I moduli ESP32 possono avere:

| Tipo        | Caratteristiche             |
| ----------- | --------------------------- |
| PCB antenna | integrata sulla board       |
| IPEX/U.FL   | antenna esterna collegabile |

Antenna esterna utile per:

* maggiore portata
* contenitori metallici
* segnali difficili

---

# 13. Flash e memoria

Le sigle spesso includono quantità di memoria.

Esempi:

| Sigla | Significato |
| ----- | ----------- |
| N4    | 4 MB flash  |
| N8    | 8 MB flash  |
| N16   | 16 MB flash |
| R2    | 2 MB PSRAM  |
| R8    | 8 MB PSRAM  |

Esempio:

```text
N16R8
```

significa:

* 16 MB flash
* 8 MB PSRAM

---

# 14. Come leggere una board completa

Esempio:

```text
ESP32-S3-DevKitC-1
```

con modulo:

```text
ESP32-S3-WROOM-1-N8R2
```

Interpretazione completa:

| Livello | Valore    |
| ------- | --------- |
| Chip    | ESP32-S3  |
| Modulo  | WROOM-1   |
| Flash   | 8 MB      |
| PSRAM   | 2 MB      |
| Board   | DevKitC-1 |

---

# 15. Quando scegliere cosa

## Progetti semplici

Consigliato:

* ESP32 classico
* ESP32-WROOM
* DevKit economica

---

## Display e GUI

Consigliato:

* ESP32-S3
* PSRAM abbondante
* board con USB nativa

---

## Camera

Consigliato:

* ESP32-S3
* oppure ESP32-WROVER
* PSRAM obbligatoria o quasi

---

## Basso consumo

Consigliato:

* ESP32-C3
* board mini

---

## Audio e AI

Consigliato:

* ESP32-S3
* PSRAM elevata

---

# 16. Schema mentale finale

```text
CHIP
 ├── ESP32
 ├── ESP32-S2
 ├── ESP32-S3
 └── ESP32-C3
        ↓
MODULO
 ├── WROOM
 └── WROVER
        ↓
BOARD
 ├── DevKit
 ├── NodeMCU
 ├── DOIT
 ├── LOLIN
 ├── M5Stack
 └── XIAO
```

---

# 17. Regola pratica veloce

Se leggi:

```text
ESP32-S3-WROOM-1-N16R8
```

ricorda:

* ESP32-S3 = chip
* WROOM-1 = modulo
* N16 = flash
* R8 = PSRAM

Se invece leggi:

```text
ESP32-S3-DevKitC-1
```

stai guardando la board completa di sviluppo.
