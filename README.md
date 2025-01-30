# 📊 Proyecto Integrador - Análisis y Manejo de Datos con Scala

## 📌 Descripción del Proyecto y Objetivos
Este proyecto tiene como objetivo realizar un análisis exploratorio de datos utilizando Scala, implementar funciones de orden superior y manipular datos en una base de datos SQL. Se incluyen procesos de limpieza, transformación y explotación de datos, con un enfoque en la eficiencia y escalabilidad.

---

## 📂 Explicación de los Datos
El dataset utilizado contiene múltiples columnas, incluyendo datos numéricos y categóricos. Uno de los principales desafíos es el manejo de la columna **Crew**, que requiere una transformación específica.

- **Columnas Numéricas**: Contienen valores como ingresos, costos, cantidad de pasajeros, etc.
- **Columnas No Numéricas**: Representan información categórica como nombres, ubicaciones, estados.
- **Columna Crew**: Necesita un tratamiento especial para normalizar su contenido y hacerla compatible con los análisis posteriores.

---

## 📥 Lectura del CSV y Limpieza de Datos
Los datos se cargan desde un archivo CSV utilizando Scala y se procesan con funciones de limpieza que incluyen:
- Eliminación de valores nulos o duplicados.
- Transformaciones en la columna Crew.
- Conversión de tipos de datos según sea necesario.

```scala
import org.apache.spark.sql.SparkSession

val spark = SparkSession.builder()
  .appName("Data Analysis")
  .master("local[*]")
  .getOrCreate()

val data = spark.read.option("header", "true").csv("data/dataset.csv")
val cleanedData = data.na.drop()
```

---

## 🛠 Implementación de Funciones en Scala
Se implementan diversas funciones de orden superior para procesar los datos:
- **`map`**: Transformación de cada elemento.
- **`filter`**: Filtrado de registros.
- **`flatMap`**: Expansión de listas anidadas.
- **`count`**: Conteo de registros.
- **`foldLeft`**: Acumulación de valores.

```scala
val valores = List(1, 2, 3, 4, 5)
val cuadrados = valores.map(x => x * x)
val pares = valores.filter(_ % 2 == 0)
val suma = valores.foldLeft(0)(_ + _)
```

---

## 🗄️ Consultas SQL desde Scala
Se integran consultas SQL en Scala para manipular y extraer información relevante de la base de datos:

```scala
import java.sql.DriverManager

val conexion = DriverManager.getConnection("jdbc:mysql://localhost:3306/proyecto", "usuario", "password")
val statement = conexion.createStatement()
val resultado = statement.executeQuery("SELECT * FROM datos WHERE Crew > 5")
```

---

## 🚀 Ejecución del Código
Para ejecutar el proyecto, sigue estos pasos:

1. Clona el repositorio:
   ```bash
   git clone https://github.com/tu_usuario/proyecto-integrador.git
   cd proyecto-integrador
   ```
2. Configura el entorno y ejecuta el script principal:
   ```bash
   sbt run
   ```
3. Verifica los resultados y genera reportes.

---

📌 **Notas:** Asegúrate de tener instalado **Scala, Spark y MySQL** antes de ejecutar el código.

📌 **Contacto:** Para dudas o sugerencias, abre un issue en el repositorio. 🚀
