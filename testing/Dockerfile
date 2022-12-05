FROM michaelwetter/ubuntu-2004-omc:1.20.0_dev-314-g3033f43-1

USER root

# Install git, sudo
RUN apt-get update && \
    apt-get install -y git && \
    apt-get install -y sudo && \
#    apt-get install -y python && \
    apt-get install -y python3-pip

USER developer

ENV ROOT_DIR /usr/local

WORKDIR $HOME
ENV ROOT_DIR /usr/local

RUN mkdir $HOME/MODELICAPATH && mkdir git && \
    cd git && \
    git clone https://github.com/ibpsa/modelica-ibpsa.git && cd modelica-ibpsa && git checkout a8b77f6d2820c52a63cd5964db6db9913a5f669d && cd .. && \
    git clone https://github.com/open-ideas/IDEAS.git && \
    git clone https://github.com/lbl-srg/modelica-buildings.git && \
    ln -s $HOME/git/IDEAS/IDEAS $HOME/MODELICAPATH/IDEAS && \
    ln -s $HOME/git/modelica-buildings/Buildings $HOME/MODELICAPATH/Buildings && \
    ln -s $HOME/git/modelica-ibpsa/IBPSA $HOME/MODELICAPATH/IBPSA
#    ln -s $ROOT_DIR/JModelica/ThirdParty/MSL/Modelica $HOME/MODELICAPATH/Modelica && \
#    ln -s $ROOT_DIR/JModelica/ThirdParty/MSL/ModelicaServices $HOME/MODELICAPATH/ModelicaServices && \
#    ln -s $ROOT_DIR/JModelica/ThirdParty/MSL/Complex.mo $HOME/MODELICAPATH/Complex.mo
ENV MODELICAPATH $HOME/MODELICAPATH

RUN python3 -m pip install --user flask-restful==0.3.9 pandas requests==2.18.4 pyzmq
RUN python3 -m pip install -U https://github.com/OpenModelica/OMPython/archive/master.zip