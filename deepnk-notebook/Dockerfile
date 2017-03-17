FROM jupyter/tensorflow-notebook

USER jovyan

# conda install --yes -c asmeurer pango
# NOTE: http://stackoverflow.com/questions/40009184

# Install Python 3 OpenCV 3.2.0
RUN conda install --yes -c asmeurer pango && \
    conda install --yes -c menpo opencv3=3.2.0 && \
    python -c "import cv2; print(cv2.__version__)"

# Install Python 2 OpenCV 3.2.0
RUN conda install --yes -n python2 -c asmeurer pango && \
    conda install --yes -n python2 -c menpo opencv3=3.2.0 && \
    /bin/bash -c "source /opt/conda/envs/python2/bin/activate python2" && \
    python -c "import cv2; print(cv2.__version__)" && \
    /bin/bash -c "source deactivate"

# Change user name to `prov`
USER root
WORKDIR /
RUN usermod -l prov -m -d /home/prov jovyan

# Switch to new user
ENV HOME /home/prov
USER prov
WORKDIR /home/prov
