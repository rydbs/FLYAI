# Dockerfile
FROM python:3.7-alpine
RUN apk update && \
        apk add --no-cache \
        bash
RUN apk add --update build-base python3-dev py-pip
ENV LIBRARY_PATH=/lib:/usr/lib
EXPOSE 3000
WORKDIR /var/www/html
COPY . /var/www/html/
RUN pip install flask

CMD ["python", "app.py"]
