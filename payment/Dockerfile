FROM python:3.15-rc-alpine as builder
RUN  apk add --no-cache python3-dev build-base linux-headers pcre-dev
WORKDIR /opt/app 
COPY payment.ini .
COPY payment.py . 
COPY rabbitmq.py .
COPY requirements.txt .
RUN pip3 install --prefix=/install -r requirements.txt 

FROM python:3.15-rc-alpine 
WORKDIR /opt/app 
RUN apk add --no-cache pcre
RUN  addgroup -S roboshop && adduser -S roboshop -G roboshop 
COPY --from=builder --chown=roboshop:roboshop /install /usr/local 
COPY --from=builder --chown=roboshop:roboshop /opt/app .
USER roboshop
CMD ["uwsgi","--ini","payment.ini"]
