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
<img width="438" height="345" alt="Puurakenne" src="https://github.com/user-attachments/assets/27a5c15b-d4ff-43a8-8192-8a8c0151c20e" />  

