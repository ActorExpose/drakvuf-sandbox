ARG IMAGE
FROM $IMAGE

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y wget curl python3 python3-venv python3-pip debhelper devscripts lsb-release && \
    if [ $(apt-cache search --names-only '^python3\.8$' | wc -l) -ne 0 ]; then apt-get install -y python3.8 python3.8-dev ; else apt-get install -y python3.7 python3.7-dev ; fi && \
    curl "https://debs.icedev.pl/manual/dh-virtualenv/$(lsb_release -cs)/dh-virtualenv_1.2~dev-1_all.deb" -o dh-virtualenv.deb && \
    curl -sL https://deb.nodesource.com/setup_13.x | bash - && \
    apt-get install -y nodejs && \
    python3 -m pip install pip && \
    pip3 install virtualenv && \
    apt install -y ./dh-virtualenv.deb

COPY drakcore /build
WORKDIR /build
