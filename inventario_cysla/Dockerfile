FROM python:3.13.5-alpine3.22

WORKDIR /app

# Instala dependencias necesarias para compilar y conectar con MariaDB
RUN apk add --no-cache \
    gcc \
    musl-dev \
    python3-dev \
    libffi-dev \
    mariadb-dev \
    build-base \
    pkgconfig \
    mariadb-connector-c-dev  # A veces necesario con mysqlclient

# Copia el archivo de dependencias
COPY requirements.txt .

# Instala las dependencias de Python
RUN pip install --no-cache-dir -r requirements.txt

# Copia el resto del código
COPY . .

# Expón el puerto para acceder a Django desde fuera
EXPOSE 8000

# Comando por defecto para ejecutar la app
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
