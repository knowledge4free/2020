FROM python:3.7-alpine
RUN apk update && \
    apk add \
        bash \
        supervisor

RUN adduser -D -u 1001 -s /bin/bash app

WORKDIR /opt/app
RUN mkdir -p /opt/app

ADD run.sh /run.sh
ADD flag.txt /flag.txt
ADD supervisord-flask.ini /etc/supervisor.d/supervisord-flask.ini
COPY src/ /opt/app/
RUN chmod +x /opt/app/check
RUN chmod 755 /*.sh

RUN pip install -r requirements.txt

RUN chown -R app:app /opt/app
RUN chmod -R a-w /opt/app

EXPOSE 8000
CMD ["/run.sh"]
