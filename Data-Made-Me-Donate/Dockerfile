#start with 3.7.2 version of python
FROM python:3.7.2

MAINTAINER Hari Devanathan <hd2zm@tailordev.fr>

#ENV PYTHONUNBUFFERED 1

ADD PIT/PIT_Federal_MK_Comparison.py PIT_Federal_MK_Comparison.py 
ADD SPDAT/SPDAT.py SPDAT.py 

#update packages instlaled in the os
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        libatlas-base-dev gfortran

#Copy the list of python packages to install
COPY requirements.txt requirements.txt

#Copy all government data used
COPY ./data ./data

#Now install the python packages
RUN pip install -r requirements.txt

#Run script
ENTRYPOINT [ "entrypoint.sh" ]

#Allow access on port 8888
EXPOSE 8888