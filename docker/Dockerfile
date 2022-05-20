FROM peternguyentr/node-java-chrome:latest

# Fix certificate issues
RUN apt-get update --no-install-recommends && \
    apt-get -y install ca-certificates-java && \
    apt-get clean && \
    apt-get -y install sudo && \
    update-ca-certificates -f;

# test here we come
VOLUME /var/run/docker.sock

RUN adduser jenkins sudo

RUN echo “jenkins ALL=NOPASSWD: ALL” >> /etc/sudoers

RUN usermod -aG docker jenkins

RUN chmod 777 /var/run/docker.sock

RUN chown root:jenkins /var/run/docker.sock

USER jenkins


WORKDIR /app
COPY . .

RUN npm install

CMD ["/app/docker/run-tests.sh"]
