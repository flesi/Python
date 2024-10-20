- `Un DataFrame es una tabla bidimensional, como una hoja de cálculo o una tabla de base de datos, con columnas etiquetadas. Una Series es una columna individual en un DataFrame.`


## Inicialización
Para usar pandas solo se requiere importar la librería

```python
import pandas as pd
```

pd  :  Aplica a la librería de pandas
df   :  Aplica únicamente a los dataframes
sr    :  Aplica a series (pueden ser series únicas columnas de un DataFrame) 
sd   :  Aplica tanto a series como DataFrames


## Series

```python
sr1 = pd.Series(['a' , 'b' , 'c' ,  'd' ,  'e' , 'f' , 'g' , 'h' , 'i' , 'j'])
```

| **Índice** | **Valor** |
| ------ | ----- |
| 0      | a     |
| 1      | b     |
| 2      | c     |
| 3      | d     |
| 4      | e     |
| 5      | f     |
| 6      | g     |
| 7      | h     |
| 8      | i     |
| 9      | j     |


## DataFrame

```python
df1 = pd.DataFrame( {'A' : range(0, 50, 5),
					 'B' : 10**2,
					 'C' : sr_a.values },
					index=pd.date_range(start='2019-01-01', freq="D", periods=10))
```


| Índice     | A   | B   | C   |
| ---------- | --- | --- | --- |
| 2019-01-01 | 0   | 100 | a   |
| 2019-01-02 | 5   | 100 | b   |
| 2019-01-03 | 10  | 100 | c   |
| 2019-01-04 | 15  | 100 | d   |
| 2019-01-05 | 20  | 100 | e   |
| 2019-01-06 | 25  | 100 | f   |
| 2019-01-07 | 30  | 100 | g   |
| 2019-01-08 | 35  | 100 | h   |
| 2019-01-09 | 40  | 100 | i   |
| 2019-01-10 | 45  | 100 | j   |

## Selección 

```python
df1.iloc[2,2]
```












## Creación

- Métodos comunes para crear DataFrames y atributos habituales

```python
pd.DataFrame(dict)  # Desde un diccionario
pd.read_csv(file)   # Desde un csv
pd.read_excel(file) # Desde un excel
pd.read_json(json)  # Desde un json
pd.read_html(html)  # Desde una web
pd.read_sql(sql)    # Desde una base de datos
pd.read_clipboard() # Desde el portapapeles
pd.read_table(file) # Desde un archivo delimitado tsv
pd.read_parquet()   # Desde un archivo en formato parquet pd.read_gbg
```

### Ejemplos
- **Desde un diccionario**

```python
data = {'col1': [1, 2, 3, 4], 'col2': ['A', 'B', 'C', 'D']} 

df = pd.DataFrame(data) print(df)
```

|     | col1 | col2 |
| --- | ---- | ---- |
| 0   | 1    | A    |
| 1   | 2    | B    |
| 2   | 3    | C    |
| 3   | 4    | D    |


- **Desde un csv**
```python
# Suponiendo que tienes un archivo CSV llamado "data.csv" en el mismo directorio: 

df = pd.read_csv('data.csv') print(df)	
```

Contenido del archivo CSV (`data.csv`):
```
col1,col2
1,A
2,B
3,C
4,D
```

Resultado

|     | col1 | col2 |
| --- | ---- | ---- |
| 0   | 1    | A    |
| 1   | 2    | B    |
| 2   | 3    | C    |
| 3   | 4    | D    |


- **Desde una excel** 
```python
# Suponiendo que tienes un archivo Excel llamado "data.xlsx" con una hoja "Sheet1"
df = pd.read_excel('data.xlsx', sheet_name='Sheet1')
print(df)
```

Resultado

|     | col1 | col2 |
| --- | ---- | ---- |
| 0   | 1    | A    |
| 1   | 2    | B    |
| 2   | 3    | C    |
| 3   | 4    | D    |


- **Desde un json**
```python
# Crear un DataFrame a partir de una cadena JSON
json_data = '{"col1": [1, 2, 3, 4], "col2": ["A", "B", "C", "D"]}'
df = pd.read_json(json_data)
print(df)
```

Resultado

|     | col1 | col2 |
| --- | ---- | ---- |
| 0   | 1    | A    |
| 1   | 2    | B    |
| 2   | 3    | C    |
| 3   | 4    | D    |

- **Desde una tabla HTML**
```python
# Suponiendo que tienes una tabla HTML en una página web
html_data = """
<table>
    <thead>
        <tr>
            <th>col1</th>
            <th>col2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>A</td>
        </tr>
        <tr>
            <td>2</td>
            <td>B</td>
        </tr>
    </tbody>
</table>
"""

# Leer tablas desde HTML
dfs = pd.read_html(html_data)
df = dfs[0]  # pandas devuelve una lista de tablas
print(df)
```

Resultado

|     | col1 | col2 |
| --- | ---- | ---- |
| 0   | 1    | A    |
| 1   | 2    | B    |


- Desde una base de datos
```python
import sqlite3

# Crear una conexión a una base de datos SQLite (o cualquier otra BD compatible)
con = sqlite3.connect('test.db')

# Ejecutar una consulta SQL para leer datos en un DataFrame
query = "SELECT col1, col2 FROM my_table"
df = pd.read_sql(query, con)
print(df)

# Cerrar la conexión
con.close()
```


- Desde el portapapeles
```python
# Copia un texto tabular a tu portapapeles, luego ejecuta este código:
df = pd.read_clipboard()
print(df)
```


- Desde un archivo delimitado por tabulaciones (TSV)
```python
# Suponiendo que tienes un archivo "data.tsv" delimitado por tabulaciones
df = pd.read_table('data.tsv')
print(df)
```


- Desde un archivo en formato Parquet
```python
# Suponiendo que tienes un archivo "data.parquet"
df = pd.read_parquet('data.parquet')
print(df)
```


## Limpieza de datos

Ayudan a identificar datos inválidos 

```python
pd.isna(obj)         # Detecta los valores inválidos en un array
pd.isnull(obj)       # Detecta los nulos en un array
pd.notna(obj)        # Detecta los valores válidos en un array
pd.notnull(obj)      # Detecta todos los valores no nulos en un array
pd.unique(obj)       # Devuelve un array con valores únicos.                                              Tambien existe para series ( serie.unique() ) e índices                            ( index.unique() ), y variaciones (nuinique, is_unique)
sr.hasnas            # Informa si la serie tiene NA
sd.dropna()          # Elimina los valores inválidos 
sd.fillna(val)       # Rellena los valores inválidos 
sd.interpolate()     # Interpola los valores segun distintos metodos
sd.drop_duplicates() # Elimina los duplicados
sd.duplicated()      # Máscara con los duplicados
sr.is_monotic        # Indica si es una progresion creciente/decreciente
sr.nonzero()         # Devuelve los índices de los elementos que no son cero
sd.drop()            # Elimina las filas o columnas del objeto
```




## Operadores lógicos

Operadores lógicos para usar en cualquier expresión booleana

```python
&         # And 
|         # Or
~         # Not
^         # Xor
sd.any()  # Any
sd.all()  # All
```




## Selección 

Selecciona contenido del DataFrame

```python
df.iloc[row_indexer,column_indexer]  # Selecciona por indices de filas y columnas
df.loc[row_indexer,column_indexer]   # Selecciona por etiquetas
df.iat[row,column]                   # Método análogo a iloc para obtener un valor                                        concreto
df.at[row,cloumn]                    # Método análogo a loc para obtener un valor                                         concreto
df[]                                 # Permite mezclar las selecciones y realizar                                         filtrados
```


## Transformaciones avanzadas

Transformaciones de las Series/DataFrames
```python
pd.melt(df)              # Descompone un Dataframe, según las columnas que digamos
pd.pivot(index,col,val)  # Crea una tabla auxiliar a partir de 3 columnas
pd.pivot_table(df)       # Crea una tabla auxiliar con el DataFrame

pd.merge(left, right)    # Fusiona 2 DataFrames como si fuera un join de base de                              datos 
sd.reindex()             # Nos permite utilizar un índice con nuevas etiquetas
sd.join(obj)             # Fusiona las columnas de 2 DataFrames en base a una                                 clave/columna
sd.append(to_append)     # Añade mas columnas al DataFrame
sd.resample(rule)        # Permite realizar un remuestro en función del tiempo
pd.concat(obj)           # Concatena pandas en el eje que se decida
```


## Ordenación
Ordenación de valores e índices
```python
sd.sort_values()  # Ordena los valores
sd.sort_index()   # Ordena el índice 
```



## Consulta de datos
 Obtener información de los datos almacenados
 ```python
 sd.sample()           # Selecciona filas al azar
                         Se puede indicar % o numero de filas/columnas
 sd.isin(list)         # Devuelve un Dataframe que indica si cada celda contiene                            alguno de los elementos que se pasan. 
 df.query(expresion)   # Permite obtener una parte de l DataFrame a partir de una                           expresion. Se puede conseguir algo similar con df[]
 sd.filter(list|expr)  # Filtra las columnas a mostrar
                         Se puede utilizar o una lista o una expresion regular
 sd.head(n=5)          # Obtiene el comienzo del Datraframe
 sd.tail(n=5)          # Obtiene el final del DataFrame
 sd.where(cond)        # Es equivalente a df[cond] pero devolviendo un DataFrame                            con la misma forma que el original
 sd.items()            # Iterador perezoso de elementos. 
                         Equivalente a sd.iteritems()
 sr.items()            # Devuelve el primer elemento de la Serie 
 sd.keys()             # Columnas del objeto
 sd.pop(item)          # Elimina un elemento del conjunto y lo devuelve
```

## Operadores Binarios
Son operaciones entre 2 Series o DataFrames
```python
sd.add(sd)           # Suma al nivel de elemento
sd.sub(sd)           # Resta a nivel de elemento
sd.mul(sd)           # Multiplicación a nivel de elemento
sd.div(sd)           # División a nivel de elemento
sd.mod(sd)           # Módulo a nivel de elemento 
sd.pow(sd)           # Potencia a nivel de elemento
sd.combine(sd,func)  # Combina 2 objetos aplicando la función a sus elementos
sd.round()           # Redondea con el número de decimales que indiquemos
sd.lt()              # Operador lógico <
sd.gt()              # Operador lógico >
sd.le()              # Operador lógico <=
sd.ge()              # Operador lógico >=
sd.ne()              # Operador lógico !=
sd.eq()              # Operador lógico ==
sd.product()         # Devuelve el producto de sus valores según el eje que                               indiquemos
sd.dot(sd)           # Devuelve el producto matricial
```

## Exportación
Permite exportar los datos a un fichero
```python
sd.to_excel()        # En formato excel
sd.to_csv()          # En formato csv
sd.to_dict()         # En formato diccionario python
sd.to_json()         # En formato json
sd.to_sql(tab, con)  # A una base de datos indicanto tabla y cadena de conexión 
sd.to_string()       # En formato cadena de texto
sd.to_clipboard()    # Al portapapeles
Series.to_latex()    # En formato latex
```


## Gráficas 
Permite obtener gráficos de los datos del DataFrame
```python
df.plot()   # Grafico
df.hist()   # Histograma de los datos
```


## Agrupaciones
Permite agrupar los datos y aplicar funciones
También se pueden utilizar cualquiera de las funciones de estadística 

```python
sd.groupby()               # Agrupa datos por un criterio
sd.apply(func)             # Aplica una función a los datos sobre el eje que                                    indiquemos
df.applymap(lambda x: x*2) # Aplica una operacion a todos los elementos del DataFrame
sd.rolling()               # Crea ventanas que se desplazan para el procesamiento                               de los datos
sd.agg(func)               # Agrega los datos aplicando la función del parámetro 
sd.transform(func)         # Devuelve una serie/Dataframe después de aplicarle la                               función 
sd.pipe(func)              # Permite encadenar llamadas a funciones  
sd.expanding(periods)      # Crea una ventana creciente con los periodos que                                    indiquemos
```



## Funciones estadísticas 
Funciones que nos permiten calcular la estadística sobre columnas o DataFrames completos
```python
sd.sum()             # Calcula la suma total
sd.count()           # Calcula el número de elementos
sd.max()             # Calcula el valor máximo 
sd.min()             # Calcula el valor mínimo 
sd.std()             # Calcula la desviación típica 
sd.mean()            # Calcula la media
sd.median()          # Calcula la mediana
sr.value_counts()    # Calcula los valores que hay de cada tipo
sd.abs()             # Devuelve una serie con el valor absoluto de cada elemento
sd.cov(sr)           # Calcula la covaranzia con otro objeto
                       El parametro es obligatorio en la Series  
sd.corr(sr)          # Calcula la correlacióncon otro objeto
                       El parametro es obligatorio en la Series  
sd.mad()             # Devuelve la media de la desviación absoluta de los valores
sd.nlargest(n, col)  # Devuelve los N elementos mas altos
                       En el DataFrame hay que indicar la coma  
sd.nsmallest(n, col) # Devuelve los N elementos mas pequeños
                       En el DataFrame hay que indicar la coma
sd.pct_change()      # Devuelve la serie con los cambios porcentuales
sd.rank()            # Rango de elementos
sd.cumsum()          # Suma acumulada
sd.cummax()          # Máximo acumulado  
sd.cummin()          # Mínimo acumulado
sd.cumprod()         # Producto acumulado 
sd.quantile()        # Devuelve un elemento en el percentil indicado
```

## Modificación
Permite modificar nuestros elementos
```python
sd.rename()             # Permite cambiar el nombre o las etiquetas del índice 
sd.replace(to_replace)  # Reemplaza los valores de panad según el parámetro 
sd.update(sd)           # Actualiza los valores según el objeto del parámetro 
sd.shift()              # Desplazamos los valores tantas posiciones como                                     indiquemos (por defecto 1)
```




## Metainformación

Nos da información sobre el modelo que estamos manejando
```python
sd.index               # Etiquetas del índice 
sd.values              # ndarray con valores
sr.dtype               # Informa del tipo de datos
sd.shape               # Informa del número de filas de la Serie. 
                         También se pueda usar con DataFrame y devuelve filas y                             columnas
sd.size                # Número de elementos
sr.data                # Puntero a los datos
sr.name                # Nombre da la Serie
sr.put(indices,values) # Efectúa un put sobre los índices con valores suministrados
```
