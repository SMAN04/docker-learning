
#stage 1 Build

FROM python:3.9-slim as build

WORKDIR /app
 
RUN apt-get update && apt-get install -y \
gcc \
python3-dev \
libmariadb-dev \
pkg-config

COPY . .

RUN pip install flask mysqlclient

#Stage 2: production

FROM python:3.9-slim
WORKDIR /app
COPY --from=build /app /app
EXPOSE 5002
CMD ["python", "app.py"]
