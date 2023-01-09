## Pedro Ruiz
import re 

import requests 

import pandas as pd 

import bs4 import Beautifulsoup as p

url="https://repositorio.unprg.edu.pe/"              # guardo la dirección web del repositorio en url 

html=requests.get(url)                              # pido acceso para poder leer el contenido de la página 

soup=b(content,"lxml")                              # extraemos el contenido de la página 

data=soup.find_all(class_="ds-static-div community-image-container")      # extraemos de una manera más visible el contenido 

for linea in data:

    link=linea.find("a")
    
    enlace="https://repositorio.unprg.edu.pe"+link["href"]
    
# 2dp paso

url=enlace                     # guardamos el enlace extraido anteriormente en url   
 
html=requests.get(url)                              # pido acceso para poder leer el contenido de la página 

content=html.content                                # extraemos el contenido de la página 

soup=b(content,"lxml")                              # extraemos de una manera más visible el contenido 

link = soup.find_all('a', text="Tesis: título profesional")  

tml=requests.get(url)                              # pido acceso para poder leer el contenido de la página 

content=html.content                               # exraemos de una manera más visible el contenido

soup=b(content,"lxml")

link = soup.find_all('a', text="Facultad de Ingeniería Civil, Sistemas y Arquitectura")       

link = link[0]

href = link['href']

enlace2="https://repositorio.unprg.edu.pe"+href                      # gaurdamos el link donde se ubican los tttulos de la facultad de sistemas 


# 3er paso 

url=enlace1                                         # guardamos en enlace donde se encuentran las titulos prifesioanles en url 









