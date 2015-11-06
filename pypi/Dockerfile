FROM python27


RUN pip install virtualenv virtualenvwrapper && . `which virtualenvwrapper.sh` && pip install pep381client && mkdir -p pypi_mirror/data/

CMD pep381run pypi_mirror/data/
