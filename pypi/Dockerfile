FROM docker-registry.guokr.com/guokr/python27:olympus

ENV PYPI_HOST 0.0.0.0
ENV DATA_DIR /data
ENV OUTSIDE_URL pypi.wishstone.me

RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
	&& rm /bin/sh && ln -s /bin/bash /bin/sh && apt-get update && apt-get install -y --force-yes nginx 
RUN pip install -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com devpi-server devpi-web 

RUN echo -e 'rm /etc/nginx/sites-enabled/default \ndevpi-server --outside-url $OUTSIDE_URL --host $PYPI_HOST --port 4040 --serverdir $DATA_DIR --gen-config \ncp /gen-config/nginx-devpi.conf /etc/nginx/sites-enabled/ \nrm /etc/nginx/sites-enabled/default \nservice nginx start \ndevpi-server --outside-url $OUTSIDE_URL --host $PYPI_HOST --port 4040 --serverdir $DATA_DIR --start \ntail -f $DATA_DIR/.xproc/devpi-server/xprocess.log' > start.sh 
    
CMD sh start.sh

