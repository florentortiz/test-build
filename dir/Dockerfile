# Which image will we use to create our ?
FROM ubuntu:latest
# Directory where we will go
WORKDIR /var/www/html
# Copy the local content of the "build directory" of Openshift into the "WORKDIR"
COPY . .
# Some commande to try it
RUN echo "toto" > /tmp/test.txt
RUN touch /tmp/test_touch.txt
