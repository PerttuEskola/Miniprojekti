# Projektin aloitus
Projektisssa toteutetaan automatisoitu Debian-peliympäristö käyttämällä Ansiblea.  
Tavoitteena on siis luoda puhdas Debian kone valmiiksi peliympäristöksi yhdellä komennolla.  

# Ansible konfiguraatio
Luodaan tarvittavat tiedostot ansiblea varten:  
````
micro hosts.ini
micro ansible.cfg
micro site.yml
````
Lisätään hosts.ini:iin  
````
localhost

[all:vars]
ansible_python_interpreter=/usr/bin/python3
````
Tämä tehdään sitä varten että ansible ei valittaisi python versiosta.  
Lisätään ansible.cfg:
````
[defaults]
inventory = hosts.ini
````
Tämän takia ei tarvitse kirjoittaa "-i hosts.ini" joka kerta kun ajaa ansible-playbookin.  
Lisätään site.yml:
````
- hosts: all
  roles:
````


# Luodaan roolit
Luotiin yksi rooli, "**LGE**", jonka sisällä on muut tarvittavat konfiguraatiotiedostos.  
````
mkdir -p roles/lge/files  
mkdir -p roles/lge/handlers
mkdir -p roles/lge/tasks
mkdir -p roles/lge/vars
````
<img width="438" height="345" alt="Puurakenne" src="https://github.com/user-attachments/assets/27a5c15b-d4ff-43a8-8192-8a8c0151c20e" />  

Varsin sisällä on määriteltynä käyttäjä ja proton muuttujat.  
<img width="1698" height="69" alt="Näyttökuva 2026-05-04 183415" src="https://github.com/user-attachments/assets/05e690e4-fc3c-454d-ad8d-b3adb9a51772" />  

Taskin sisällä on määriteltynä tehtävät, ladattavat paketit, ajurit ja tiedostopolut.  
Koodia rakennetaan osa kerrallaan, pikkuhiljaa kokeillen toimiiko se vai ei.  
Steamia varten pitää lisätä contrib ja non-free repositoriot, jotta se toimisi:    
````
- apt_repository:
    repo: "deb http://deb.debian.org/debian/ trixie main contrib non-free non-free-firmware"
````
Myös discordia varten pitää ladata .deb paketti:  
````
get_url:
  url: "https://discord.com/api/download?platform=linux&format=deb"
  dest: "/tmp/discord.deb"
````
<img width="800" height="1200" alt="task_koodi" src="https://github.com/user-attachments/assets/a32ec8cf-08bb-4e9c-aee3-9d20522229e7" />  

Handlerin sisällä on viesti joka ilmoittaa että Proton on latautunut.  
<img width="1572" height="90" alt="Näyttökuva 2026-05-04 183114" src="https://github.com/user-attachments/assets/2fdc471f-72bc-4f01-b267-cb73b1fba779" />  

Filesin sisällä on MangoHud:in konfiguraatiotiedosto.  
<img width="457" height="486" alt="Näyttökuva 2026-05-04 183245" src="https://github.com/user-attachments/assets/546c2840-9977-4933-a0df-15a018615848" />  


  

