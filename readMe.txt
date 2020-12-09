github: https://github.com/franciscojgsalguero1/examen_1eva_20201209_gordo_francisco.git

el usuario y la contraseña para el adminer es alumne

4)

He añadido el símbolo \$ en la línea 40 del archivo read_template.php y la línea 47 
del archivo read_one.php.

5)

La imagen se guarda en la columna image de la base de datos con formato varchar(512).

La primera comprobación que hacemos es si en el formulario el input de imagen está vacío,
en la línea 41 del archivo create_product.php y si es así obtenemos el hash con sha1_file
y lo concatenamos con el nombre de la imagen y un guión en la línea 41 del mismo archivo.

$image=!empty($_FILES["image"]["name"]) ? sha1_file($_FILES['image']['tmp_name']) . "-" . basename($_FILES["image"]["name"]) : "";

A continuación en el método uploadPhoto del objeto product en el archivo product.php,
(dejo comentarios de lo que se va haciendo en español dentro del propio código).
Lineas comentadas: 160, 173, 183, 189, 195, 202, 208. Todos los comentarios que
he hecho empiezan con: comprobamos que (por si quieres usar CTRL+F).

En resumen: comprobamos que la imagen ha sido enviada, es real, la extensión de la
imagen está entre las permitidas, que no exista ya la imagen, que el tamaño no supere
1 MB y que el directorio donde se almacena la imagen real exista.

En la base de datos guardamos un varchar de longitud máxima de 512 carácteres que es la concatenación de un hash de la imagen
(con la función sha1_file) un "-" y el nombre de la imagen. Mientras la imagen de verdad la guardamos en la carpeta uploads.

La recuperamos con el método readOne del objeto product en el archivo product.php y mostramos la imagen
mediante la línea 68 del archivo read_one.php que pone 

echo $product->image ? "<img src='uploads/{$product->image}' style='width:300px;' />" : "No image found.";

6)

Simplemente añadí (creo) la parte del formulario de create_product.php de subir la imagen
en la línea 111 a 114 de update_product.php, le añadí las líneas 52 y 53 en update_product.php
que también estaban en create_product.php y en el archivo product.php en el método update
llamé al método uploadPhoto() en la línea 128.

