FROM python:3.6-slim-stretch

RUN apt update && \
    apt install -y python3-dev gcc

WORKDIR app

ADD requirements.txt .
RUN pip install -r requirements.txt
#pip install --no-cache-dir -r
ADD models models
ADD src src

EXPOSE 80

# Run it once to trigger resnet download
RUN python src/app.py prepare

# Start the server
CMD ["python", "src/app.py", "serve"]
