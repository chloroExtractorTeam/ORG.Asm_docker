FROM ubuntu

RUN apt-get update && apt-get install -y git python3 python3-pip python3-venv
RUN pip3 install -U pip
RUN pip install -U sphinx
RUN pip install -U cython
RUN git clone https://git.metabarcoding.org/org-asm/org-asm.git
RUN cd /org-asm && python3 setup.py --serenity install
RUN ln -s /org-asm/ORG.asm-1.0.00-alpha*/bin/oa /usr/bin/oa
RUN ln -s /org-asm/ORG.asm-1.0.00-alpha*/bin/orgasmi /usr/bin/orgasmi
VOLUME /data
WORKDIR /data