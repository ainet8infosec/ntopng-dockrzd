# Clone, Build & Run for Xenial_LTS containerized ntopng
## Source: http://packages.ntop.org/apt/
##### BaseRef: https://github.com/lucaderi/ntopng-docker/

####Xenial_LTS

docker image build -t ntopng_img:ntopng_xenial_lts -f ubu16/Dockerfile .

docker volume create ntopng_data

docker run -v ntopng_data:/data --net=host -t -p 3000:3000 -i ntopng_img:ntopng_xenial_lts --interface eno1

####Bionic_LTS

docker image build -t ntopng_img:ntopng_bionic_lts -f ubu18/Dockerfile .

docker volume create ntopng_data

docker run -v ntopng_data:/data --net=host -t -p 3000:3000 -i ntopng_img:ntopng_bionic_lts --interface eno1
