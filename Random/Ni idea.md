```py
palabras = []
palabras.append("Ni")
palabras.append("idea")

texto_output = ""
for palabra in palabras:
	texto_output += palabra + " "

# Borra el último caracter del string, el cual es un espacio
texto_output = texto_output[:-1]

print(texto_output)

------------------------------------------

Output:
Ni idea
```