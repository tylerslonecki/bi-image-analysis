FROM mambaorg/micromamba:1-mantic
LABEL authors="tjs334"

WORKDIR /home/mambauser/

COPY --chown=$MAMBA_USER:$MAMBA_USER env.yml /tmp/env.yml

RUN micromamba install -y -n base -f /tmp/env.yml && \
    micromamba install -y -n base jupyter && \
    micromamba clean --all --yes

ARG MAMBA_DOCKERFILE_ACTIVATE=1

ENV ENV_NAME=base
RUN python -m ipykernel install --user --name $ENV_NAME

EXPOSE 8888

CMD [ "jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--allow-root" ]