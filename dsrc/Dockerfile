FROM continuumio/miniconda3:latest

MAINTAINER Jeremy Volkening <jdv@base2bio.com>

# Install dependencies
WORKDIR /conda
COPY environment.yml .

# procps provides 'ps' for nextflow
RUN apt-get update && apt-get install -y \
      procps \
      vim \
    && conda env create --prefix /opt/cenv -f environment.yml \
    && rm -rf /opt/conda/pkgs/* && rm -rf /conda

# Create regular user
RUN useradd -m -U conda
USER conda
WORKDIR /home/conda/

# activate the conda environment
ENV PATH /opt/cenv/bin:$PATH

CMD [ "/bin/bash" ]
