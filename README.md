# Miniprojekti
## Linux gaming essentials

Automatisoi valmiin Linux-peliympäristön asennus Debian käyttöjärjestelmälle yhdellä komennolla.

## Yleiskuvaus
Käytetään ansiblea konfiguroimaan puhdas Debian kone valmiiksi peliympäristöksi. 
Ansiblella asennetaan ja konfiguroidaan pelityökalut automaattisesti, säästäen aikaa ja varmistaen toistettavan, sekä toimivan lopputuloksen.

## Ominaisuudet 
Asentaa:
- **Steam** (Pelikirjasto ja kauppa)
- **Lutris** (Pelialusta: GOG, Epic Games, Humble Bundle, Steam, jne)
- **Discord** (Pelaajien suosima viestintä sovellus)
- **Proton GE** (Yhteensopivuustyökalu Steam Playlle, joka perustuu Wineen ja lisäkomponentteihin)
- **Ajurit ja arkkitehtuuri** (Vulkan ja i386-arkkitehtuuri)
- **GameMode** (Optimoi Linux-järjestelmän suorituskykyä tarvittaessa)
- **MangoHud** (Monitoroi esim. FPS:ää, lämpötiloja ja suorittimen/näytönohjaimen kuormitusta)

## Vaatimukset
- Debian pohjainen järjestelmä.
- Ansiblen ja ssh asennus.
- Sudo-oikeudet.

## Käyttöönotto
Asenna Ansible
````bash
sudo apt-get update
````
````bash
sudo apt-get install ansible
````
Asenna SSH
````bash
sudo apt-get -y install ssh
````
Käynnistä ja enabloi ssh
````bash
sudo systemctl enable --now ssh
````
Testaa SSH
````bash
ssh localhost
````
````bash
exit
````
Automatisoi SSH login
````bash
ssh-keygen
````
````bash
ssh-copy-id localhost
````

### Lataa ja pura .zip tiedosto kotihakemistoon.

Suorita ansible-kansion sisällä playbook.
````bash
ansible-playbook site.yml -K
````
Idempotentti saadaan komennon uudelleen suorittamisen jälkeen.

## Protonin konfigurointi.

Idempotentin jälkeen käynnistä Steam.
````bash
steam
````

### Steamiin kirjauduttua "**Settings**" --> "**Compatibility**" ja valitaan Proton versio.
<img width="1890" height="1496" alt="image" src="https://github.com/user-attachments/assets/8167b2d4-413c-4def-9d44-4e494a09ed9f" />

### Proton asentuu.
<img width="2756" height="190" alt="image" src="https://github.com/user-attachments/assets/5d3a6a43-2cde-4c92-a20b-1b3eb4a6c165" />

## MangoHud ja GameMode

Lisää pelin "**Properties**" --> "**General**" --> "**Lauch Options**".
````
gamemoderun mangohud %command%
````
<img width="1392" height="280" alt="image" src="https://github.com/user-attachments/assets/ec37d043-cc5e-43c2-b578-01326e275004" />


## Lopputulos
Valmis peliympäristö.
Steam, lutris ja discord käyttövalmiina.
Suorituskykytyökalut konfiguroituna.

### Asennetut sovellukset käynnistettynä.
<img width="2047" height="1181" alt="image" src="https://github.com/user-attachments/assets/6e48ef33-d432-412e-b324-90b81fefd10f" />

### Lutris avattuna.
<img width="626" height="362" alt="image" src="https://github.com/user-attachments/assets/d797c6d6-5791-4adf-a9a7-24032584d605" />

### MangoHud pelin sisällä.
<img width="2879" height="1648" alt="image" src="https://github.com/user-attachments/assets/a2f63a09-ce27-44e6-8b20-9220f72f9181" />


## Tekijät
Perttu Eskola & Toni Hepola

## Lisenssi
Tämä projekti on lisenssoitu GNU General Public Licence v3.0 -lisenssillä
