# Copyright 2017 Nicolas Lamirault <nicolas.lamirault@gmail.com>
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# VERSION 010
# AUTHOR:         Nicolas Lamirault <nicolas.lamirault@gmail.com>
# DESCRIPTION:    zeiot/rpi-coredns

FROM resin/armv7hf-debian:stretch
MAINTAINER Nicolas Lamirault <nicolas.lamirault@gmail.com>

ENV COREDNS_VERSION 010

ADD https://github.com/coredns/coredns/releases/download/v${COREDNS_VERSION}/coredns_${COREDNS_VERSION}_linux_armv6l.tgz /coredns.tgz

RUN tar -zxvf /coredns.tgz
RUN rm /coredns.tgz
RUN /coredns /usr/bin/coredns
#RUN mv /coredns.tgz/coredns /usr/bin/coredns && \
#    mkdir /etc/coredns && \
#    mkdir -p /var/log/coredns

ADD ./Corefile /etc/coredns/Corefile

EXPOSE 9053
EXPOSE 8080

VOLUME ["/etc/coredns", "/var/log/coredns/" ]

ENTRYPOINT ["/usr/bin/coredns"]

CMD ["-conf", "/etc/coredns/Corefile", "-dns.port", "9053"]
