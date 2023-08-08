FROM canal/osbase:v2_arm64

LABEL agapple (jianghang115@gmail.com)

ENV LANGUAGE "en_US.UTF-8"
ENV LANG "en_US:zh_CN.UTF-8"
ENV LC_ALL "C"

# install canal
COPY image/ /tmp/docker/
COPY canal.deployer-*.tar.gz /home/admin/

RUN \
    ln -s /usr/bin/python2 /usr/bin/python && \
    cp -R /tmp/docker/alidata /alidata && \
    chmod +x /alidata/bin/* && \
    mkdir -p /home/admin && \
    cp -R /tmp/docker/app.sh /home/admin/  && \
    cp -R /tmp/docker/admin/* /home/admin/  && \
    /bin/cp -f alidata/bin/lark-wait /usr/bin/lark-wait && \

    mkdir -p /home/admin/canal-server && \
    tar -xzvf /home/admin/canal.deployer-*.tar.gz -C /home/admin/canal-server && \
    /bin/rm -f /home/admin/canal.deployer-*.tar.gz && \

    mkdir -p home/admin/canal-server/logs  && \
    chmod +x /home/admin/*.sh  && \
    chmod +x /home/admin/bin/*.sh  && \
    chown admin: -R /home/admin && \
    yum clean all && \
    true

# 11110 admin , 11111 canal , 11112 metrics, 9100 exporter
EXPOSE 11110 11111 11112 9100

WORKDIR /home/admin

ENTRYPOINT [ "/alidata/bin/main.sh" ]
CMD [ "/home/admin/app.sh" ]
