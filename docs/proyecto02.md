# Proyecto 02: Cálculo del sueldo

El proyecto utiliza un formulario HTML para pedir el sueldo y el puesto de una persona. Después, un programa PHP calcula el complemento según el puesto y muestra el sueldo final.

## 1. Formulario para introducir los datos

El formulario se guarda en una página HTML. `action` indica el archivo que recibirá los datos y `method="post"` hace que se envíen mediante el método POST.

```html
<!DOCTYPE html>
<html lang="es">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Introducir sueldo</title>
</head>
<body>
	<form action="ut02p02.php" method="post">
		<!-- Campo obligatorio para introducir un sueldo de al menos 1001 -->
		<label for="sueldo">SUELDO:</label>
		<input type="number" name="sueldo" id="sueldo" required min="1001">
		<br><br>

		<!-- El valor de cada opción es el que recibirá PHP -->
		<label for="puesto">PUESTO:</label>
		<select name="puesto" id="puesto">
			<option value="base">Base</option>
			<option value="directivo">Directivo</option>
			<option value="alto_cargo">Alto Cargo</option>
		</select>
		<br><br>

		<input type="submit" value="Enviar">
	</form>
</body>
</html>
```

El usuario debe escribir un sueldo y seleccionar un puesto. `required` obliga a completar el campo, mientras que `min="1001"` establece el mínimo permitido por el navegador.

## 2. Recoger los datos en PHP

El archivo `ut02p02.php` recibe los valores enviados por el formulario. El operador `??` utiliza un valor predeterminado si todavía no se ha recibido el dato: sueldo de 1000 y puesto base.

```php
$sueldo = $_POST["sueldo"] ?? 1000;
$puesto = $_POST["puesto"] ?? "base";
```

## 3. Asignar el porcentaje del complemento

Con una estructura condicional se elige el porcentaje según el puesto. Los valores `0.1`, `0.15` y `0.2` representan respectivamente el 10 %, el 15 % y el 20 %.

```php
if ($puesto == "base") {
	$porcentaje = 0.1;
} elseif ($puesto == "directivo") {
	$porcentaje = 0.15;
} elseif ($puesto == "alto_cargo") {
	$porcentaje = 0.2;
} else {
	$porcentaje = 0;
}
```

Si el valor recibido no coincide con ninguno de los puestos previstos, se asigna un complemento del 0 %.

## 4. Calcular el aumento y el sueldo final

El aumento es el sueldo base multiplicado por el porcentaje. El sueldo final se calcula sumando ese aumento al sueldo base.

```php
$aumento = $sueldo * $porcentaje;
$sfinal = $sueldo + $aumento;
```

Por ejemplo, si el sueldo es 1200 € y el puesto es base, el aumento será 120 € y el sueldo final será 1320 €.

## 5. Mostrar los resultados

`echo` escribe los resultados en la página. Multiplicar `$porcentaje` por 100 permite mostrarlo como porcentaje; `<br>` añade un salto de línea.

```php
echo "El sueldo base es de " . $sueldo . "€<br>";
echo "El complemento es del " . ($porcentaje * 100) . "%<br>";
echo "El sueldo final es de " . $sfinal . "€";
```

## 6. Código PHP completo

Este es el código del archivo `ut02p02.php`, reuniendo los fragmentos anteriores dentro de una página HTML:

```php
<!DOCTYPE html>
<html lang="es">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Sueldo</title>
</head>
<body>
	<?php
	$sueldo = $_POST["sueldo"] ?? 1000;
	$puesto = $_POST["puesto"] ?? "base";

	if ($puesto == "base") {
		$porcentaje = 0.1;
	} elseif ($puesto == "directivo") {
		$porcentaje = 0.15;
	} elseif ($puesto == "alto_cargo") {
		$porcentaje = 0.2;
	} else {
		$porcentaje = 0;
	}

	$aumento = $sueldo * $porcentaje;
	$sfinal = $sueldo + $aumento;

	echo "El sueldo base es de " . $sueldo . "€<br>";
	echo "El complemento es del " . ($porcentaje * 100) . "%<br>";
	echo "El sueldo final es de " . $sfinal . "€";
	?>
</body>
</html>
```

En resumen, el formulario envía el sueldo y el puesto a PHP, que selecciona el porcentaje correspondiente, hace los cálculos y presenta el resultado.
