FROM peternguyentr/node-java-chrome:latest

# test here we come
RUN adduser jenkins sudo
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers
RUN chown root:jenkins /var/run/docker.sock

# Fix certificate issues
RUN apt-get update --no-install-recommends && \
    apt-get -y install ca-certificates-java && \
    apt-get clean && \
    update-ca-certificates -f;

WORKDIR /app
COPY . .

RUN npm install

CMD ["/app/docker/run-tests.sh"]
