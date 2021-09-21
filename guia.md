# REDES 1 - EJERCICIOS

## Ejercicio 1

- ¿Cuál de los siguientes e suna dirección de host inválida si se usa la máscara de red 255.255.255.192?

A. 10.1.1.1   
B. 10.1.1.66  
**C. 10.1.1.127**  
D. 10.1.1.130  

**Solución**:  

1. **Identificar clase de IP**

Clasificación de IP

|clase  | desde    | hasta         | máscara      |
|-------|----------|---------------|--------------|
|A      |0.0.0.0   |127.255.255.255|255.0.0.0     |
|B      |128.0.0.0 |191.255.255.255|255.255.0.0   |
|C      |192.0.0.0 |223.255.255.255|255.255.255.0 |


Como todas la IP son 10.1.1.x entonces corresponden a clase A

2. **Identificar tipo de máscar de red o subred**

Dado que la máscara de subred para las IP clase A es 255.0.0.0 se pude identificar que se esta haciendo subnetting.

Paso la máscara a binario
`11111111.11111111.11111111.11000000`

como utilizo 2 bits para las subredes, obtendré 2^2=4 subredes.


3. **Calcular rangos validos**

`256/4 = 64`

|subred|desde      |hasta     |
|------|-----------|----------|
|1     |10.1.1.0   |10.1.1.63 |
|2     |10.1.1.64  |10.1.1.127|
|3     |10.1.1.128 |10.1.1.191|
|4     |10.1.1.192 |10.1.1.255|


4. **Identificar IP no permitidas**

Existen 2 IP que se encuentran reservadas
la primera es la que identifica la red/subred propiamente dicha y después se reserva la última IP para broadcast.

Por lo tanto las IP no permitidas son:

- 10.1.1.0 (red) / 10.1.1.63 (broadcast)
- 10.1.1.64 (red) / **10.1.1.127** (broadcast)
- 10.1.1.128 (red) / 10.1.1.191 (broadcast)
- 10.1.1.192 (red) / 10.1.1.255 (broadcast)

___

## Ejercicio 2
- Si se tiene la dirección de IP 172.16.3.57 con máscara de 27 bits,¿cuál es el rango válido de hosts?

A. 172.16.3.32 to 172.16.3.62
B. **172.16.3.33 to 172.16.3.62**
C. 172.16.3.34 to 172.16.3.62
D. 172.16.3.57 to 172.16.3.62


`IP 172.16.3.57` _IP Clase B_ `(255.255.0.0)`

**Mascará aplicada 27 bits**  
`11111111.11111111.11111111.11100000`  
`|----------------------------|----|`  

**En decimal**
`255.255.255.224`

**Subredes**
`256/8 = 32`

| subred | desde           | hasta           |
|--------|-----------------|-----------------|
| 1      | 172.16.3.0      | 172.16.3.31     |
| 2      | **172.16.3.32** | **172.16.3.63** |
| 3      | 172.16.3.64     | 172.16.3.95     |
| 4      | 172.16.3.96     | 172.16.3.127    |
| 5      | 172.16.3.128    | 172.16.3.159    |
| 6      | 172.16.3.160    | 172.16.3.191    |
| 7      | 172.16.3.192    | 172.16.3.223    |
| 8      | 172.16.3.224    | 172.16.3.255    |

Dado que las IP .32 está reservada para la red y la .63 es para broadcast, el rango válido as la opción:  

- **`B. 172.16.3.33 to 172.16.3.62`**

___

## Ejercicio 3

- Determinar si los dispositivos A y B, con direcciones de IP 172.16.17.30/20 y 172.16.28.15/20 respectivamente, 
están en la misma o en diferente subred.


- ip A `172.16.17.30`, `10101100.00010000.00010001.00011110`  
- ip B `172.16.28.15`, `10101100.00010000.00011100.00001111`  
- máscara `11111111.11111111.11110000.00000000`, `255.255.240.0`   

1. Clase: ip Clase B `(255.255.0.0)`  
2. Subnetting: Si  

- Subred IP A  
`11111111.11111111.11110000.00000000`  
`10101100.00010000.00010001.00011110`  
`-----------------------------------`  
`10101100.00010000.00010000.00000000`   
`172.16.16.0`  
  
<br>
    
- Subred IP B  
`11111111.11111111.11110000.00000000`  
`10101100.00010000.00011100.00001111`   
`-----------------------------------`  
`10101100.00010000.00010000.00000000`  
`172.16.16.0`  

**Respuesta:** Al aplicarle la operación lógica AND entre la máscara y la ip se obtuvo que las dos IP están en la misma subred.

___

## Ejercicio 4

- Decir que tipo de direcciones son (clase A, B o C) y cual es la máscara de red correspondiente

| ip            | clase | mascara       |
|---------------|-------|---------------|
| 3.3.3.3       | A     | 255.0.0.0     |
| 230.23.2.1    | ?     | ?             |
| 100.1.1.1     | A     | 255.0.0.0     |
| 190.2.234.210 | B     | 255.255.0.0   |
| 210.0.0.1     | C     | 255.255.255.0 |
| 90.4.3.2      | A     | 255.0.0.0     |
| 131.12.12.5   | B     | 255.255.0.0   |
| 8.1.1.6       | A     | 255.0.0.0     |
| 64.15.2.2     | A     | 255.0.0.0     |


___

## Ejercicio 5

- ¿Si tenemos disponible una dirección de clase B, y necesitamos tener 25 sitios de 2000 hosts cada uno, cual sería una mascara de subred apropiada para implementar?

- 11111111.11111111.11111000.00000000
- 255.255.248.0
- /21

