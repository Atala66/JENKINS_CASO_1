# Repo para EU - DevOps&Cloud - UNIR

Este repositorio incluye un proyecto sencillo para demostrar los conceptos de pruebas unitarias, pruebas de servicio, uso de Wiremock y pruebas de rendimiento
El objetivo es que el alumno entienda estos conceptos, por lo que el código y la estructura del proyecto son especialmente sencillos.
Este proyecto sirve también como fuente de código para el pipeline de Jenkins.


 # ------------------------------ COMANDOS DESDE EL DIRECTORIO RAIZ -------------------------------- #


# Error: ModuleNotFoundError: No module named 'app'
# set PYTHONPATH=.

# Correr el fichero mas basico ( calculadora )
python app\calc.py

# Correr el servidor Flask
pip install flask
SET FLASK_APP=app\<ruta api.py>
flask run 


# Correr los  Tests
pip install pytest
pytest test\<ruta test>

# cmd %ERRORLEVEL%  if (!0) error [1]


# Wireframe como STANDALAONE
 # "ruta donde vamos a alojar los mocks

java -jar wiremock-standalone-3.5.4.jar --port {{  }}  --verbose --root-dir  D:\dev_ops_unir\helloworld\test\wiremock


# URL FLASK: 5000
# URL WIREMOCK: 9090

