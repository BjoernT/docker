FROM fedora:latest
MAINTAINER Bjoern Teipel <bjoern@teipel.ws>

RUN dnf -y update 
RUN dnf -y install inadyn-mt

ENV DYN_USER username
ENV DYN_PASS password
ENV DYN_ALIAS myhome.dnsalias.net
ENV DYN_INTERVAL 120

CMD /usr/sbin/inadyn --username $DYN_USER --password $DYN_PASS --update_period_sec $DYN_INTERVAL --alias $DYN_ALIAS