FROM library/python:3.7-slim

RUN apt update && apt install -y build-essential portaudio19-dev sqlite3 python3-webob

COPY anki-sync-server /app/anki-sync-server

WORKDIR /app/anki-sync-server

RUN pip3 install -r src/requirements.txt

RUN mkdir /app/data && \
    mv /app/anki-sync-server/src/ankisyncd.conf /app/anki-sync-server/ankisyncd.conf.example && \
    ln -s /app/data/ankisyncd.conf /app/anki-sync-server/src/

COPY config /app/config
COPY scripts /app/scripts

CMD /app/scripts/startup.sh

EXPOSE 27701
