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

url=enlace

html=requests.get(url)                              # pido acceso para poder leer el contenido de la página 

content=html.content

soup=b(content,"lxml")

link = soup.find_all('a', text="Tesis: título profesional")

link = link[0]

href = link['href']

enlace1="https://repositorio.unprg.edu.pe"+href    


# 3er paso 

url=enlace1

html=requests.get(url)                              # pido acceso para poder leer el contenido de la página 

content=html.content

soup=b(content,"lxml")

link = soup.find_all('a', text="Facultad de Ingeniería Civil, Sistemas y Arquitectura")

link = link[0]

href = link['href']

enlace2="https://repositorio.unprg.edu.pe"+href                       # guardamos el nuevo enlace en enlace 2 


# 4ta paso 

url=enlace2

html=requests.get(url)                              # pido acceso para poder leer el contenido de la página 

content=html.content

soup=b(content,"lxml")

link = soup.find_all('a', text="Ingeniería de Sistemas")

link = link[0]

href = link['href']

enlace3="https://repositorio.unprg.edu.pe"+href   


# 5to paso:guardamos los link en una lista

lista=[]

url=enlace3                                         # guardo al dirección ulink rl en url 

html=requests.get(url)                              # pido acceso para poder leer el contenido de la página 

content=html.content                                # accedo al contenido de la página 

soup=b(content,"lxml")                      # con este comando puedo obtener una mejor visualizaciónn del contenido de la página                               

data=soup.find_all(class_="thumbnail artifact-preview")

for linea in data:

    link=linea.find("a")
    
    links="https://repositorio.unprg.edu.pe"+link.get("href")
    
    lista.append(links)

###################################################################

url=lista[0]

html=requests.get(url)

content=html.content

soup=b(content,"lxml")

data=soup.find("div",class_="simple-item-view-show-full item-page-field-wrapper table")

link=data.find("a")

link1="https://repositorio.unprg.edu.pe"+ link["href"]

url=link1

html=requests.get(url)

content=html.content

soup=b(content,"lxml")

data=soup.find(class_="ds-static-div primary")

t1universidad=data.find_all(class_="word-break")[9].text

t1titulo=data.find_all(class_="word-break")[16].text

t1nombre_tesista1=data.find_all(class_="word-break")[1].text

t1nombre_tesista2=data.find_all(class_="word-break")[1].text

t1grado=data.find_all(class_="word-break")[20].text

t1asesor=data.find_all(class_="word-break")[0].text

t1resumen=data.find_all(class_="word-break")[6].text

t1fecha_emitida=data.find_all(class_="word-break")[4].text

#########################

url=lista[1]

html=requests.get(url)

content=html.content

soup=b(content,"lxml")

data=soup.find("div",class_="simple-item-view-show-full item-page-field-wrapper table")

link=data.find("a")

link2="https://repositorio.unprg.edu.pe"+ link["href"]

url=link2

html=requests.get(url)

content=html.content

soup=b(content,"lxml")

data=soup.find(class_="ds-static-div primary")

t2universidad=data.find_all(class_="word-break")[10].text

t2titulo=data.find_all(class_="word-break")[17].text

t2nombre_tesista1=data.find_all(class_="word-break")[1].text

t2nombre_tesista2=data.find_all(class_="word-break")[2].text

t2grado=data.find_all(class_="word-break")[21].text

t2asesor=data.find_all(class_="word-break")[0].text

t2resumen=data.find_all(class_="word-break")[7].text

t2fecha_emitida=data.find_all(class_="word-break")[5].text


#########################

url=lista[2]

html=requests.get(url)

content=html.content

soup=b(content,"lxml")

data=soup.find("div",class_="simple-item-view-show-full item-page-field-wrapper table")

link=data.find("a")

link3="https://repositorio.unprg.edu.pe"+ link["href"]



url=link3

html=requests.get(url)

content=html.content

soup=b(content,"lxml")

data=soup.find(class_="ds-static-div primary")

t3universidad=data.find_all(class_="word-break")[10].text

t3titulo=data.find_all(class_="word-break")[17].text

t3nombre_tesista1=data.find_all(class_="word-break")[1].text

t3nombre_tesista2=data.find_all(class_="word-break")[2].text

t3grado=data.find_all(class_="word-break")[21].text

t3asesor=data.find_all(class_="word-break")[0].text

t3resumen=data.find_all(class_="word-break")[7].text

t3fecha_emitida=data.find_all(class_="word-break")[5].text


#creamos un dataframe 

df=pd.DataFrame()

#insertamos:

#insertamos estructura del informe

df['Estructura']= ["Universidad","Título","Nombre del tesista 1","Nombre del tesista 2","Grado","Asesor","Resumen","Fecha emitida"]

#insertamos los datos extraidos de la tesis 1

df['Primera tesis']=[t1universidad,t1titulo,t1nombre_tesista1,t1nombre_tesista2,t1grado,t1asesor,t1resumen,t1fecha_emitida]

#insertamos los datos extraidos de la tesis 2

df['Segunda tesis']=[t2universidad,t2titulo,t2nombre_tesista1,t2nombre_tesista2,t2grado,t2asesor,t2resumen,t2fecha_emitida]

#insertamos los datos extraidos de la tesis 3

df['Tercera tesis']=[t3universidad,t3titulo,t3nombre_tesista1,t3nombre_tesista2,t3grado,t3asesor,t3resumen,t3fecha_emitida]

df
    


