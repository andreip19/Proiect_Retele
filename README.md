# Proiect Rețele de Calculatoare II

Acest repository conține proiectul final pentru disciplina **Rețele de Calculatoare II** (Universitatea „Dunărea de Jos” din Galați, Facultatea de Automatică, Calculatoare, Inginerie Electrică și Electronică).

**Autor:** Petrea Andrei (Calculatoare, Anul III)  
**Profesor coordonator:** C. Niculiță  

---

## 📌 Descrierea Proiectului
Proiectul reprezintă designul și implementarea unei rețele de tip LAN extins (Campus Network), bazată pe modelul ierarhic Cisco. Aceasta include configurarea echipamentelor de rețea (routere, switch-uri), implementarea de VLAN-uri, rutare Inter-VLAN, NAT (Overload și Static) și aplicarea de politici de securitate prin Access Control Lists (ACL).

Fișierul principal al simulării este `PROIECT.pkt`, realizat în **Cisco Packet Tracer**.

## 🏗️ Topologia și Arhitectura Rețelei
Rețeaua este organizată ierarhic:
* **Core / Edge:** Un Router central (Cisco 2911) care gestionează traficul Inter-VLAN, securitatea (ACL) și ieșirea la Internet (NAT).
* **Distribuție:** 4 Switch-uri (Catalyst 2960) care agregă traficul din clădiri (A, B, C, D) și îl transmit către router prin conexiuni Trunk (Gigabit Ethernet).
* **Acces:** Switch-uri de nivel 2 (Catalyst 2960) instalate la etaje pentru conectarea stațiilor de lucru (FastEthernet).
* **NOC (Network Operations Center):** Un switch dedicat (VLAN 10) unde sunt localizate toate serverele și echipamentele partajate.

## ⚙️ Servicii și Servere (Zona NOC)
Toate serverele se află în subrețeaua `10.43.40.0/24` și sunt mapate static (NAT) pentru acces extern:
* **DHCP** (`10.43.40.12`): Oferă configurare IP automată stațiilor de lucru prin funcția DHCP Relay de pe router.
* **DNS** (`10.43.40.10`)
* **HTTP** (`10.43.40.13`)
* **EMAIL / SMTP** (`10.43.40.14`)
* **FTP** (`10.43.40.15`)

## 🔒 Securitate și Reguli de Acces (ACL)
Securitatea informațiilor este asigurată prin liste de acces (ACL) configurate pe router:
1.  **Baza de Date 1 (`10.43.40.20`):** Accesibilă exclusiv utilizatorilor din Rețeaua 1 (Clădirile A și B).
2.  **Baza de Date 2 (`10.43.40.21`):** Accesibilă exclusiv utilizatorilor din Rețeaua 2 (Clădirile C și D).
3.  **Imprimante de Rețea (`10.43.40.30`, `10.43.40.31`):** Accesibile pentru toți utilizatorii din rețelele interne mari, indiferent de clădire. Accesul din exterior (Internet) este strict blocat.

## 📂 Conținutul Repository-ului
* `PROIECT.pkt` - Simularea rețelei în Cisco Packet Tracer.
* `documentatie.docx` - Documentația completă a proiectului.
* `harta_logica.jpg` / `harta_fizica.jpg` - Diagramele topologiei logice și fizice (Visio).
* `Cerinte proiect.pdf` - Specificațiile și cerințele inițiale ale proiectului.

## 🚀 Cum să rulezi proiectul
1. Descarcă și instalează **Cisco Packet Tracer**.
2. Clonează acest repository:
   ```bash
   git clone [https://github.com/andreip19/Proiect_Retele.git](https://github.com/andreip19/Proiect_Retele.git)
