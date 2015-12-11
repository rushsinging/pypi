FROM python27

ENV PYPI_HOST 0.0.0.0
ENV DATA_DIR /data
ENV OUTSIDE_URL pypi.wishstone.me

RUN apt-get install -y --force-yes nginx && pip install devpi-server devpi-web 

RUN echo -e 'rm /etc/nginx/sites-enabled/default \ndevpi-server --outside-url $OUTSIDE_URL --host $PYPI_HOST --port 4040 --serverdir $DATA_DIR --gen-config \ncp /gen-config/nginx-devpi.conf /etc/nginx/sites-enabled/ \nrm /etc/nginx/sites-enabled/default \nservice nginx start \ndevpi-server --outside-url $OUTSIDE_URL --host $PYPI_HOST --port 4040 --serverdir $DATA_DIR --start \ntail -f $DATA_DIR/.xproc/devpi-server/xprocess.log' > start.sh 
    
CMD sh start.sh

