# Kubernetes-LimitRange

# Kubernetes LimitRange - How to create LimitRange & define Pods/Containers which follows those ranges

N=limitrange-example

k create namespace $N

k get ns $N

ls

vim limitrange.yaml
:q!

k create -f limitrange.yaml

k -n $N describe limitranges limitrange-min-max-demo

k -n $N get limitranges limitrange-min-max-demo -oyaml | vim -
:q!

cd cpu

ls

vim constraints-cpu-demo.yaml
:q!

k create -f constraints-cpu-demo.yaml

k -n $N get pod constraints-cpu-demo -oyaml | vim -
:q!

k -n $N delete pod constraints-cpu-demo

vim limitrange-exceed-cpu-pod.yaml
:q!

k create -f limitrange-exceed-cpu-pod.yaml

vim limitrange-subceed-cpu-pod.yaml
:q!

k create -f limitrange-subceed-cpu-pod.yaml

cd ../memory

ls

vim constraints-memory-demo.yaml
:q!

k create -f constraints-memory-demo.yaml

k -n $N get pod constraints-memory-demo -oyaml | vim -
:q!

k -n $N delete pod constraints-memory-demo

vim limitrange-exceed-memory-pod.yaml
:q!

k create -f limitrange-exceed-memory-pod.yaml

vim limitrange-subceed-memory-pod.yaml
:q!

k create -f limitrange-subceed-memory-pod.yaml

k -n $N  delete limitranges limitrange-min-max-demo

k delete ns $N

cd ..
