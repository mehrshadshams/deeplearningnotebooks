# Deep Learning notebooks

## Setup Python

1. Download a python distribution, like [Anaconda](https://www.anaconda.com/download/success)
2. If you are using Anaconda, create a conda environment

    ```bash
    conda create -n deeplearning python=3.11
    ```

3. Activate environment and install pip

    ```bash
    conda activate deeplearning
    conda install pip
    ```

4. (optional) Install [CUDA](https://developer.nvidia.com/cuda-downloads) This will be needed to use GPU

5. Install requirements. Depending the availability of GPU please run either *requirements-cpu.txt* or *requirements-gpu.txt*

    ```bash
    pip install -r requirements.txt
    pip install -r requirements-gpu.txt
    ```

## Setup ElasticSearch

How to start:

1. Run ElasticSearch:

    ```bash
    docker run --rm --name elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:8.15.0
    ```

2. Reset ElasticSearch password

    ```bash
    docker exec -it elasticsearch /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
    ```

3. Export password

    ```bash
    export ELASTIC_PASSWORD="<password>"
    ```

4. Copy ElasticSearch cert

    ```bash
    docker cp elasticsearch:/usr/share/elasticsearch/config/certs/http_ca.crt .
    ```

5. Verify connectivity

    ```bash
    curl --cacert http_ca.crt -u elastic:$ELASTIC_PASSWORD https://localhost:9200
    ```
