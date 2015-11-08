FROM python27

RUN apt-get install -y --force-yes nginx \
    && pip install devpi-server devpi-web \
    && devpi-server --host pypi.wishstone.in --port 4040 --serverdir /data --gen-config \
    && cp /gen-config/nginx-devpi.conf /etc/nginx/sites-enabled/ \
    && rm /etc/nginx/sites-enabled/default \
    && echo -e "devpi-server --host pypi.wishstone.in --port 4040 --serverdir /data --start \n service nginx start \n tail -f /root/.devpi/server/.xproc/devpi-server/xprocess.log" > start.sh 
    
CMD sh start.sh

