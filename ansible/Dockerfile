FROM marthym/base:1.3.0 
LABEL maintainer="marthym@ght1pc9kc.fr" \
      version="1.1.0"

RUN export DEBIAN_FRONTEND=noninteractive && \
    apt -y update && \ 
    apt -y install python-pip python-setuptools gcc python-apt python-dev libffi-dev libssl-dev && \
    pip install --upgrade cffi wheel setuptools && \
    pip install ansible && \
# Cleanup install
    apt -f -y --auto-remove remove gcc python-dev libffi-dev libssl-dev && \
    apt clean && \
    apt autoclean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*