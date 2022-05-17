FROM debian:bullseye

ENV LC_ALL=C
ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends\
       sudo systemd systemd-sysv \
       python3 python3-pip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && rm -Rf /usr/share/doc && rm -Rf /usr/share/man

# Make sure systemd doesn't start agettys on tty[1-6].
RUN rm -f /lib/systemd/system/multi-user.target.wants/getty.target

CMD [ "/lib/systemd/systemd", "log-level=info", "unit=sysinit.target" ]

