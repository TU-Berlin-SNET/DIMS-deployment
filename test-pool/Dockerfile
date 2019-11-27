FROM idchain/test-pool:1.5

ARG uid=1000
ARG indy_stream=stable

# (exclusive) initial port nr for indy nodes to bind to
# 9700 means the 4 nodes will be available at 9701-9708
ENV IDC_PORT_START=9700
ENV IDC_POOL_NAME=sandbox

COPY docker-entrypoint.sh /usr/bin/docker-entrypoint.sh

ENTRYPOINT ["/usr/bin/docker-entrypoint.sh"]
CMD ["/usr/bin/supervisord"]

