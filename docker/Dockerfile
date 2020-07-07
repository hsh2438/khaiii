FROM pytorch/pytorch:latest

RUN apt-get update && apt-get install -y git build-essential

RUN git clone https://github.com/kakao/khaiii.git
WORKDIR /workspace/khaiii

RUN pip install -r requirements.txt

WORKDIR /workspace/khaiii/build

# build khaiii
RUN cmake ..
RUN make all
RUN make resource
RUN make install

# for python binding
WORKDIR /workspace/khaiii/build/package_python
RUN pip install .

# locale setting
RUN apt-get update && apt-get install -y language-pack-ko
RUN locale-gen en_US.UTF-8
RUN update-locale LANG=en_US.UTF-8
