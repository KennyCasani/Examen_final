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






