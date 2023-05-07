FROM python:3.9-slim
ADD requirements.txt requirements.txt
RUN pip install -r requirements.txt
ADD name.txt name.txt
ADD mail.txt mail.txt
ENV CONTAINERENV True
EXPOSE 5000
ADD app.py app.py
ENTRYPOINT python3 app.py
