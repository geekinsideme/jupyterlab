ARG jupyter_image=datascience-notebook
ARG jupyter_tag=python-3.9.13
FROM jupyter/${jupyter_image}:${jupyter_tag}

ARG modules="llvmlite==0.38.1 pycaret[full] mlflow[extras]"
ARG extras="autopep8 flake8 pyright"

RUN python3 -m pip --no-input install --upgrade pip
RUN python3 -m pip --no-input install ${modules}

COPY IPAexfont00401/ipaexg.ttf ipaexg.ttf
RUN cp ipaexg.ttf /opt/conda/lib/python3.9/site-packages/matplotlib/mpl-data/fonts/ttf/ipaexg.ttf && \
    echo "font.family : IPAexGothic" >>  /opt/conda/lib/python3.9/site-packages/matplotlib/mpl-data/matplotlibrc && \
    rm -r ipaexg.ttf

RUN python3 -m pip --no-input install ${extras}

RUN id && chown -hR 1000 /home/jovyan/ && ls -la /home/jovyan && env && pip freeze > /home/jovyan/requirements.txt

EXPOSE 8888
