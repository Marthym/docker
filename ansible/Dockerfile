FROM marthym/base:1.2.0
MAINTAINER marthym@ght1pc9kc.fr

RUN export DEBIAN_FRONTEND=noninteractive && \
    apt -y update && \ 
    apt -y install python-pip python-setuptools gcc python-pip python-apt python-dev libffi-dev libssl-dev && \
    pip install --upgrade pip cffi wheel setuptools && \
    pip install ansible && \

    apt -f -y --auto-remove remove gcc python-dev libffi-dev libssl-dev && \
    apt clean && \
    apt autoclean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*