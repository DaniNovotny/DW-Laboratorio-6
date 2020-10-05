```python
import regex as re
```

# Regex

# 1
1.) Genere una expresión regular que sea capaz de detectar las placas de un vehículo particular guatemalteco.

Para este ejercicio me base en la informacion de "Matriculas del Mundo" en la seccion de 'Matricuals de Guatemala (GCA)'.
La pagina la pueden encontrar ingresando al siguiente link:
    https://www.matriculasdelmundo.com/guatemala.html 


```python
placas = ['P001BCD', 
          'M657CJK', 
          'MI203FNY',
          'CD502VQK']
print(placas)
```

    ['P001BCD', 'M657CJK', 'MI203FNY', 'CD502VQK']



```python
r1 = re.compile('(A|C|CC|CD|M|MI|O|P|TC|U)' + '\d{3}' + '\D{3}')
placas_result = list(filter(r1.match, placas))
print(placas_result)
```

    ['P001BCD', 'M657CJK', 'MI203FNY', 'CD502VQK']


## 2

2.) Genere una expresión regular que valide si un archivo es de tipo .pdf o jpg. a. Ejemplo1.pdf,prueba2.PDF,respuestas_del_examen.jpg,amor.JPG


```python
archivos = ['Ejemplo1.pdf', 
          'prueba2.PDF', 
          'respuestas_del_examen.jpg',
          'amor.JPG']
print(archivos)
```

    ['Ejemplo1.pdf', 'prueba2.PDF', 'respuestas_del_examen.jpg', 'amor.JPG']



```python
r21 = re.compile('[\w]+\.(pdf|PDF)')
archivos_PDF = list(filter(r21.match, archivos))
print("Los archivos en PDF son:")
print(archivos_PDF)
r22 = re.compile('[\w]+\.(jpg|JPG)')
archivos_JPG = list(filter(r22.match, archivos))
print("\nLos archivos en JPG son:")
print(archivos_JPG)
```

    Los archivos en PDF son:
    ['Ejemplo1.pdf', 'prueba2.PDF']
    
    Los archivos en JPG son:
    ['respuestas_del_examen.jpg', 'amor.JPG']


## 3
3.) Genere una expresión regular para validar contraseñas de correo. Una contraseña de correo debe contener por lo menos 8 caracteres, una letra mayúscula y un carácter especial.


```python
contrasenia = ['Tkdh8kdhg', 
          '98haiKMi', 
          'mdh35kdh8',
          'SIllon']
print(contrasenia)
```

    ['Tkdh8kdhg', '98haiKMi', 'mdh35kdh8', 'SIllon']



```python
r3 = re.compile('^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?!.*[&%$]).{8,}$')
contrasenia_result = list(filter(r3.match, contrasenia))
print(contrasenia_result)
```

    ['Tkdh8kdhg', '98haiKMi']


## 4
4.) Cree una expresión regular para validar un numero de carnet de la Universidad Galileo, por ejemplo 19002324 donde los primeros dos dígitos representan el año en el que el alumno se inscribió los cuales pueden variar desde el 01 (año 2001) hasta el 30 (año 2030). Los siguientes dos dígitos son cero (00) los cuales van por default y los últimos cuatro dígitos son un número que va desde el 1110 hasta el 8970. Para dar su respuesta utilice la notación de expresiones regulares.


```python
carnet = ['14008524', 
          '17007301', 
          '17005292',
          '31009063',
          '42012584',
          '16034765',
          '24001354']
print(carnet)
```

    ['14008524', '17007301', '17005292', '31009063', '42012584', '16034765', '24001354']



```python
r4 = re.compile('^([0-2][1-9]|30)+0{2}+[1110-8970]')
carnet_result = list(filter(r4.match, carnet))
print(carnet_result)
```

    ['14008524', '17007301', '17005292', '24001354']


# 5
5.) Cree una expresión regular que encuentre todas las palabras de la primera línea, pero ninguna de la segunda.

a. pit,spot,spate,slaptwo,respite 

b. pt,Pot,peat,part


```python
filas = "pit,spot,spate,slaptwo,respite \npt,Pot,peat,part"
print(filas)
```

    pit,spot,spate,slaptwo,respite 
    pt,Pot,peat,part



```python
r5 = re.compile('\A')
filas_result = list(filter(r5.match, filas))
print(filas_result)
```

    ['p', 'i', 't', ',', 's', 'p', 'o', 't', ',', 's', 'p', 'a', 't', 'e', ',', 's', 'l', 'a', 'p', 't', 'w', 'o', ',', 'r', 'e', 's', 'p', 'i', 't', 'e', ' ', '\n', 'p', 't', ',', 'P', 'o', 't', ',', 'p', 'e', 'a', 't', ',', 'p', 'a', 'r', 't']



```python
 \A.*
```


```python
'/^(.*)$/m'
```


```python
'(?<!\s+)^(.+)$'
```


```python
r'^.*?[\.!\?](?:\s|$)'
```


```python

```


```python

```
