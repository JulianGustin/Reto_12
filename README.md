# Reto_12
Reto #12 de la clase de Programación de Computadores  

T.I: 1091275973  

Julian Jacobo Gustin Moreno  
***
## 1. Consulte que hacen los siguientes métodos de strings en python:
- *endswith, startswith* : Verifican si una cadena termina o empieza con un parametro especifiado
- *isalpha* : Verifica si los caracteres de la cadena son letras
- *isalnum* : Verifica si los caracteres de la cadena son alfanuméricos (letras o digitos) 
- *isdigit* : Verifica si los caracteres de la cadena son digitos 
- *isspace* : Verifica si todos los caracteres de la cadena son espacios en blanco
- *istitle* : Vefifica si la cadena sigue el formato de titulo (Cada palabra empieza con mayuscula y el resto en minusculas)
- *islower, issupper* : Verifican si los caracteres alfabeticos estan en mayusculas o minusculas
***
## 2. Procesar el archivo y extraer
### Cantidad de vocales y consonantes
```python
def contar_vocales_consonantes(file):
    #Define las vocales y consonantes
    #Se definen sin letras con tilde ni ñ porque el texto está en ingles
    vocales : str = "aeiou"
    consonantes : str = "bcdfghjklmnpqrstvwxyz"
    #Inicialzia los contadores
    num_vocales = 0
    num_consonantes = 0
    #Iterar sobre cada caracter en el texto, añadir 1 al contador si cumple con el requisito
    for caracter in file:
        if caracter in vocales:
            num_vocales += 1
        elif caracter in consonantes:
            num_consonantes += 1
    return num_consonantes, num_vocales
```
### 50 palabras mas frecuentes
```python
def palabras_frecuentes(file):
    palabras = file.split()
    freq = {}
    
    for palabra in palabras:
        #Nueva variable para almacenar la palabra "limpia"
        palabra_limpia = ""
        #Recorrer cada caracter
        for caracter in palabra:
            if caracter .isalpha():
                 #Si es una letra, la agrega a la nueva palabra limpia
                palabra_limpia += caracter
        #Remplaza la palabra por la nueva palabra limpia
        palabra = palabra_limpia
        #Procesa palabras no vacias
        if palabra:
            #Si la palabra está en el diccionario, incrementa su contador
            if palabra in freq:
                freq[palabra] +=1
            #Si no, la agrega con un contador de 1
            else:
                freq[palabra] = 1
                
    #Ordena las palabras de mayor a menor
    palabras_ordenadas = sorted(freq, key=freq.get, reverse=True)
    return palabras_ordenadas[:50]
    # [:50] es una tecnica de slicing que obtiene una sublista o subsecuencia
    # Se inicia el corte desde el inicio [:] y toma los primeros 50 elementos
```
### Main
```python
if __name__ == "__main__":
    #Lee el archivo
    with open("mbox.txt", "r") as archivo:
        file = archivo.read()
    num_vocales, num_consonantes = contar_vocales_consonantes(file)
    palabras_mas_frecuentes = palabras_frecuentes(file)
    print(f"Cantidad de vocales: {num_vocales}")
    print(f"Cantidad de consonantes: {num_consonantes}")
    print(f"50 palabras más frecuentes: {palabras_mas_frecuentes}")
```


