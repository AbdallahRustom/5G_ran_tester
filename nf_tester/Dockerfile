FROM golang:1.14.4-stretch

WORKDIR /workspace

RUN git clone https://github.com/my5G/my5G-RANTester.git \
    && cd my5G-RANTester  \
    && go mod download 

RUN mkdir /iperf
COPY iperf_2.0.13+dfsg1-1build1_amd64.deb /iperf/
COPY gcc-10-base_10-20200411-0ubuntu1_amd64.deb /iperf/
COPY libgcc-s1_10-20200411-0ubuntu1_amd64.deb /iperf/
COPY libc6_2.29-0ubuntu1_amd64.deb /iperf/

RUN dpkg -i /iperf/libc6_2.29-0ubuntu1_amd64.deb
RUN dpkg -i /iperf/gcc-10-base_10-20200411-0ubuntu1_amd64.deb
RUN dpkg -i /iperf/libgcc-s1_10-20200411-0ubuntu1_amd64.deb
RUN dpkg -i /iperf/iperf_2.0.13+dfsg1-1build1_amd64.deb




    
# Move to the binary path
WORKDIR /workspace/my5G-RANTester/cmd

RUN go build -o app

# Config files volume
VOLUME [ "/workspace/my5G-RANTester/config" ]
