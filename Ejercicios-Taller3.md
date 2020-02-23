1. Cree dos archivos de texto similares (con una o dos líneas diferentes). Compárelos empleando diff. Con el comando diff (get-content texto.txt) (get-content texto2.txt) se obtiene Resultado:

```
PS C:\Users\Desktop> notepad gg1.txt
PS C:\Users\Desktop> notepad gg2.txt
PS C:\Users\Desktop> type gg1.txt
a
PS C:\Users\Desktop> type gg2.txt
n
PS C:\Users\Desktop> diff -ReferenceObject (Get-Content gg1.txt) -DifferenceObject (Get-Content gg2.txt)
InputObject SideIndicator
----------- -------------
a       =>           
n       <=                     
```

2. Qué ocurre si se ejecuta: get-service | export-csv servicios.csv | out-file Por qué?

Porque dice que el path es nulo es decir el lugar donde se va a guardar

```
out-file : Cannot process argument because the value of argument "path" is null. 
Change the value of argument "path" to a non-null value.
```

3. Cómo haría para crear un archivo delimitado por puntos y comas (;)? PISTA: Se emplea export-csv, pero con un parámetro adicional.

`-Delimiter 'Delimitador a usar '`

```
Get-Process | Export-Csv processes.csv -Delimiter ';'
```

4. Export-cliXML y Export-CSV modifican el sistema, porque pueden crear y sobreescribir archivos. Existe algún parámetro que evite la sobreescritura de un archivo existente? Existe algún parámetro que permita que el comando pregunte antes de sobresscribir un archivo? 

`-NoClobber`


5.Windows emplea configuraciones regionales, lo que incluye el separador de listas. En Windows en inglés, el separador de listas es la coma (,). Cómo se le dice a Export-CSV que emplee el separador del sistema en lugar de la coma? 

```
Set-WinUserLanguageList -LanguageList (New-WinUserLanguageList -Language en-GB) -Force
```

6. Identifique un cmdlet que permita generar un número aleatorio.

```
Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>] [<CommonParameters>]
```

7. Identifique un cmdlet que despliegue la fecha y hora actuales.

```
Get-Date
```

8. Qué tipo de objeto produce el cmdlet de la pregunta 7?

Objeto  `Datetime`  casteable a un `String` 

9. Usando el cmdlet de la pregunta 7 y select-object, despliegue solamente el día de la semana

```
Get-Date | Select-Object DayOfWeek
```

Se despleiga solo el día del objeto "get-date".

10. Identifique un cmdlet que muestre información acerca de parches (hotfixes) instalados en el sistema.

```
Get-Hotfix
```

11. Empleando el cmdlet de la pregunta 10, muestre una lista de parches instalados. Luego extienda la expresión para ordenar la lista por fecha de instalación, y muestre en pantalla únicamente la fecha de instalación, el usuario que instaló el parche, y el ID del parche. Recuerde examinar los nombres de las propiedades.

```
Get-HotFix | Sort-Object -Property InstalledOn | Format-Table -Property InstalledOn,installedby , hotfixid
```

12. Complemente la solución a la pregunta 11, para que el sistema ordene los resultados por la descripción del parche, e incluya en el listado la descripción, el ID del parche, y la fecha de instalación. Escriba los resultados a un archivo HTML.

```
Get-HotFix | Export-Clixml |Sort-Object -Property description | Format-Table -Property description,hotfixid , installedon
```

13. Muestre una lista de las 50 entradas más nuevas del log de eventos System. Ordene la lista de modo que las entradas más antiguas aparezcan primero; las entradas producidas al mismo tiempo deben ordenarse por número índice. Muestre el número índice, la hora y la fuente para cada entrada. Escriba esta información en un archivo de texto plano.

```
Get-EventLog -LogName System -newest 50 | Sort-Object -Property id -Descending | Format-Table -Property id, date, source | out-file -filepath .\logs.txt
```
