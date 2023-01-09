## UPC
#primero llamo a todos los paquetes a utilizar para hacer el web scraping  
import re  
import requests   
import pandas as pd  
from bs4 import BeautifulSoup as b  

#1er paso 
url="https://repositorioacademico.upc.edu.pe/"   # guardo al dirección ulink rl en url  
html=requests.get(url)                              # pido acceso para poder leer el contenido de la página  
content=html.content 
soup=b(content,"lxml")       
link = soup.find_all('a', text='Tesis') 
link = link[0] 
href = link['href'] 


#2do paso 
url="https://repositorioacademico.upc.edu.pe/handle/10757/621261"   # guardo al dirección ulink rl en url   
html=requests.get(url)                              # pido acceso para poder leer el contenido de la página  
content=html.content 
soup=b(content,"lxml")       
link = soup.find_all('a', text='Pregrado') 
link = link[0] 
href = link['href'] 



#3er paso 
url="https://repositorioacademico.upc.edu.pe/handle/10757/621410"   # guardo al dirección ulink rl en url   
html=requests.get(url)                              # pido acceso para poder leer el contenido de la página  
content=html.content 
soup=b(content,"lxml")       
link = soup.find_all('a', text='Facultad de Ingeniería') 
link = link[0]  
href = link['href'] 


