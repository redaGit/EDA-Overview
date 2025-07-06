
To deliver the "Try EDA" experience, we have created an EDA playground - a repository that contains everything you need to install and provision a demo EDA instance with the virtual network on the side. 

# Installation:
Proceed with cloning the EDA playground repository that contains everything you need to install and provision a demo EDA instance.

```
git clone https://github.com/nokia-eda/playground && \
cd playground
```
The prerequisites "make" and "docker" have already been installed in the VM.

Set the EXT_DOMAIN_NAME environment variable in your shell:
```
export EXT_DOMAIN_NAME=<x>.wwrkshpz.net
```
Note: if you want to enable the Natural Language support for the EDA Query functionality, provide the LLM key (OpenAI) with an additional environment variabl.

```
export LLM_API_KEY=<your-OpenAI-API-key>
```
Run the EDA install:
```
make try-eda
```
The installation will take approximately 10 minutes to complete. Once it is done, you can optionally verify the installation.
You should be able to use kubectl -n eda-system get pods to verify that EDA core components have started and in the Ready state:
```
kubectl -n eda-system get pods | awk 'NR==1 || /eda/'
```
The list of EDA pods and status should be:
```
NAME                                  READY   STATUS    RESTARTS   AGE
cx-eda--leaf1-sim-864b97d58d-g9zq2    2/2     Running   0          12h
cx-eda--leaf2-sim-6698fc668f-4blcm    2/2     Running   0          12h
cx-eda--spine1-sim-677f5499cf-fn2pg   2/2     Running   0          12h
eda-api-9985cb78-gphnk                1/1     Running   0          12h
eda-appstore-8d679c5b-fqmt6           1/1     Running   0          12h
eda-asvr-dc9877c8d-5j62k              1/1     Running   0          12h
eda-bsvr-6bf77b64c-9l2zx              1/1     Running   0          12h
eda-ce-84c6486cb7-f8jzc               1/1     Running   0          12h
eda-cx-5dc6cf9d96-dcrrf               1/1     Running   0          12h
eda-fe-54d8db877f-xk7l8               1/1     Running   0          12h
eda-fluentbit-hkwvd                   1/1     Running   0          12h
eda-fluentd-54cf4bd5d7-j98zg          1/1     Running   0          12h
eda-git-754df68df5-8kgx4              1/1     Running   0          12h
eda-git-replica-784dbdbfc8-5zdzz      1/1     Running   0          12h
eda-keycloak-5d569565b7-2gmc7         1/1     Running   0          12h
eda-metrics-server-799d54cb7-688nz    1/1     Running   0          12h
eda-npp-eda-leaf1                     1/1     Running   0          12h
eda-npp-eda-leaf2                     1/1     Running   0          12h
eda-npp-eda-spine1                    1/1     Running   0          12h
eda-postgres-cd89bfc57-q56cc          1/1     Running   0          12h
eda-sa-576c98865f-66vq9               1/1     Running   0          12h
eda-sc-84546648c5-djr49               1/1     Running   0          12h
eda-se-1                              1/1     Running   0          12h
eda-toolbox-84c95bd8c6-lqxh7          1/1     Running   0          12h
```

Try-EDA default make create a topoogy with 2 leafs and 1 spine. This  topology deployed as part of the quickstart resulted in creation of topology nodes, with each node represented by an SR Linux simulator. The topology nodes in EDA are represented by the TopoNode resource, and this resource has a status field to indicate its health.

The easiest way to tell the current state of nodes is via the UI, or via kubectl
```
kubectl -n eda get toponodes
```
```
NAME     PLATFORM       VERSION   OS    ONBOARDED   MODE     NPP         NODE     AGE
leaf1    7220 IXR-D3L   24.10.1   srl   true        normal   Connected   Synced   12h
leaf2    7220 IXR-D3L   24.10.1   srl   true        normal   Connected   Synced   12h
spine1   7220 IXR-D5    24.10.1   srl   true        normal   Connected   Synced   12h
```

Using UI:
```
--> The UI can be accessed using https://<x>.wrkshpz.net:9443 
--> INFO: EDA is launched
    Username: admin
    Password: admin
```
