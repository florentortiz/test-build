# Which image will we use to create our ?
FROM centos:7
# Directory where we will go
WORKDIR /var/www/html
# Copy the local content of the "build directory" of Openshift into the "WORKDIR"
COPY . .
# Some commande to try it
RUN echo "toto" > /tmp/test.txt
RUN touch /tmp/test_touch.txt
RUN yum install -y httpd
# Which port will be available for the container once deployed ?
EXPOSE 8080
# Which command will be execute at the container startup ?
CMD ["httpd","start"]
