Flask es una dependencia para produccion

gunicorn, el servidor que utiliza flask,

requirements.in: tiene las dependencias de alto nivel

pip-compli requirements.in

despues de crear el requirements.txt, es el que usará el docker para instalar las dependencias de procuccion

dev-requirements.in

por ejemplo el pytest tiene que estar dentro 