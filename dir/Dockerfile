# Which image will we use to create our ?
FROM centos:7

# Directory where we will go
WORKDIR /var/www/html

# Copy the local content of the "build directory" of Openshift into the "WORKDIR"
COPY . .

# Some commande to try it
RUN echo "toto" > /tmp/test.txt
RUN touch /tmp/test_touch.txt

# HTTPD install
RUN yum install -y httpd httpd-tools

# Right change as on Openshift we can't execute by default container with root uid, so we change the file rights to the container "root" as our user uid will be in this group
# https://docs.openshift.com/container-platform/4.12/openshift_images/create-images.html#images-create-guide-openshift_create-images
RUN chgrp -R 0 /run && chmod -R g=u /run
RUN chgrp -R 0 /etc/httpd/logs && chmod -R g=u /etc/httpd/logs

# To bind port 80 on the container
RUN setcap cap_net_bind_service=+ep /usr/sbin/httpd
EXPOSE 80

# Change configuration to listen on port 8080 as openshift container can't use port bellow 1024
#RUN sed -i 's/Listen 80/Listen 8080/g' /etc/httpd/conf/httpd.conf
#EXPOSE 8080

# Which command will be execute at the container startup ?
# / ! \ Il faut bien un espace entre chaque virgule et la suite, sinon j'ai l'impression que tout est collé et ça ne fonctionne pas.....
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
