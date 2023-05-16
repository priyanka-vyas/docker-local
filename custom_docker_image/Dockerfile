# FROM apache/airflow:2.5.3
# FROM python:3.11.2
# WORKDIR /custom_docker_image
# #COPY /dags.py ./custom_docker_image
# #COPY /requirements.txt ./custom_docker_image
# COPY /dags.py .
# COPY /requirements.txt .
# RUN pip3 install -r requirements.txt
# CMD ["python3","dags.py"]


# FROM apache/airflow:2.5.3

# WORKDIR /custom_docker_image

# COPY dags.py .
# COPY requirements.txt .

# RUN pip install -r requirements.txt

# CMD ["python", "dags.py"]


# Build 
FROM python:3.11.2 AS build

WORKDIR /build

COPY requirements.txt .
RUN pip3 install --user --no-cache-dir -r requirements.txt

COPY dags.py .

# Production stage
FROM apache/airflow:2.5.3

WORKDIR /custom_docker_image

COPY --from=build /root/.local /root/.local
COPY --from=build /build/dags.py .

#CMD ["python3","dags.py"]

