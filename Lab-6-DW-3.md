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
r5 = "pit, spot, spate, slaptwo, respite \npt, Pot, peat, part"
print(r5)
```

    pit, spot, spate, slaptwo, respite 
    pt, Pot, peat, part



```python
regex=re.compile(r"(\bp.t\b|\bs.{3}\b|\bs.{4}\b|\bs.{6}\b|\br.{6})")  
regex.findall(r5)
```




    ['pit', 'spot', 'spate', 'slaptwo', 'respite']



# 6
6.) Cree una expresión regular para obtener los números telefónicos de Guatemala. Estos pueden contener al inicio +502 o 502, pueden estar separados por un espacio en blanco o un guión o juntos. Notar que los números telefónicos pueden empezar únicamente con 4,5,6 o 2.
a. +50254821151,4210-7640,52018150,24346854,11234569, 50211234578


```python
telefonos = ['+50254821151', 
             '4210-7640', 
             '52018150',
             '2434 6854',
             '11234569',
             '50211234578']
print(telefonos)
```

    ['+50254821151', '4210-7640', '52018150', '2434 6854', '11234569', '50211234578']



```python
r6 = re.compile('[502|+502]?'+'[ ]?'+'[2|4|5|6]'+'[\d]{3}'+'[ \-]?'+'[\d]{4}')
telefonos_result = list(filter(r6.match, telefonos))
print(telefonos_result)
```

    ['+50254821151', '4210-7640', '52018150', '2434 6854', '50211234578']


# 7
7.) Genere una expresión regular que sea capaz de obtener correos de la UFM.


```python
correos = ['ejemplo.uno@ufm.edu', 
          'hm_ksh@hotmail.com', 
          'cual_quier@ufm.edu']
print(correos)
```

    ['ejemplo.uno@ufm.edu', 'hm_ksh@hotmail.com', 'cual_quier@ufm.edu']



```python
r7 = re.compile('[\w]+[\w|\.|-][\w]+[\w|\.|-]\w+\@+[ufm.edu]')
correos_result = list(filter(r7.match, correos))
print(correos_result)
```

    ['ejemplo.uno@ufm.edu', 'cual_quier@ufm.edu']


# 8
8.) En el mundo distópico de Eurasia, Big Brother le asigna un identificador único a cada ciudadano. Genere una expresión regular que valide las identificaciones. Composición del id:

    a. El id inicia con 0 a 3 letras minúsculas (puede tener 0 letras minúsculas hasta tres letras minúsculas)
    
    b. Luego es seguido por una cadena de dígitos que puede ser de 2 a 9 dígitos respectivamente.
    
    c. Inmediatamente después de la cadena de dígitos, se encuentra por lo menos tres letras mayúsculas.
    
    d. Ej:abc012333ABCDEEEE


```python
id = ['msh82KDH', 
      'abc012333ABCDEEEE', 
      '749KHDI',
      '9MPS']
print(id)
```

    ['msh82KDH', 'abc012333ABCDEEEE', '749KHDI', '9MPS']



```python
r8 = re.compile('[a-z]{0,3}+[0-9]{2,9}+[A-Z]{3,}')
id_result = list(filter(r8.match, id))
print(id_result)
```

    ['msh82KDH', 'abc012333ABCDEEEE', '749KHDI']

