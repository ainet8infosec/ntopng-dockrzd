# Clone, Build & Run for Xenial_LTS containerized ntopng
## Source: http://packages.ntop.org/apt/
###### Ref: https://github.com/lucaderi/ntopng-docker/

docker image build -t ntopng_img:ntopng_xenial_lts -f Dockerfile .

docker volume create ntopng_date

docker run -v ntopng_data:/data --net=host -t -p 3000:3000 -i ntopng_img:ntopng_xenial_lts --interface eno1
