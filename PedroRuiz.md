## Pedro Ruiz
import re 

import requests 

import pandas as pd 

import bs4 import Beautifulsoup as p

url="https://repositorio.unprg.edu.pe/"              # guardo al dirección ulink rl en url 

html=requests.get(url)                              # pido acceso para poder leer el contenido de la página 

soup=b(content,"lxml")

