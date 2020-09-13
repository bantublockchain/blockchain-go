FROM ubuntu:focal
RUN apt-get update
RUN apt-get install -y ca-certificates
COPY expansion /sbin/expansion
ENTRYPOINT ["/sbin/expansion"]