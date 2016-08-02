http://play.etcd.io/

https://github.com/henszey/etcd-browser

deb http://get.docker.io/ubuntu docker main


sudo docker run -d -p 4001:4001 -p 2380:2380 -p 2379:2379 --name etcd0 quay.io/coreos/etcd:v3.0.4 /usr/local/bin/etcd \
 -name etcd0 \
 -advertise-client-urls http://localhost:2379,http://localhost:4001 \
 -listen-client-urls http://localhost:2379,http://localhost:4001 \
 -initial-advertise-peer-urls http://localhost:2380 \
 -listen-peer-urls http://localhost:2380 \
 -initial-cluster-token etcd-cluster-1 \
 -initial-cluster etcd0=http://localhost:2380,etcd1=http://localhost:2480,etcd2=http://localhost:2580

 sudo docker run -d -p 4101:4101 -p 2480:2480 -p 2479:2479  --name etcd1 quay.io/coreos/etcd:v3.0.4 /usr/local/bin/etcd \
 -name etcd1 \
 -advertise-client-urls http://localhost:2479,http://localhost:4101 \
 -listen-client-urls http://localhost:2479,http://localhost:4101 \
 -initial-advertise-peer-urls http://localhost:2480 \
 -listen-peer-urls http://localhost:2480 \
 -initial-cluster-token etcd-cluster-1 \
 -initial-cluster etcd0=http://localhost:2380,etcd1=http://localhost:2480,etcd2=http://localhost:2580

sudo docker run -d -p 4201:4201 -p 2580:2580 -p 2579:2579 --name etcd2 quay.io/coreos/etcd:v3.0.4 /usr/local/bin/etcd \
 -name etcd2 \
 -advertise-client-urls http://localhost:2579,http://localhost:4201 \
 -listen-client-urls http://localhost:2579,http://localhost:4201 \
 -initial-advertise-peer-urls http://localhost:2580 \
 -listen-peer-urls http://localhost:2580 \
 -initial-cluster-token etcd-cluster-1 \
 -initial-cluster etcd0=http://localhost:2380,etcd1=http://localhost:2480,etcd2=http://localhost:2580