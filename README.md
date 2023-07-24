# Apache

Install & configure apache

## Requirements
Podman is installed

## Var

```
rootCA_dir: /root/ssl/rootCA.crt
QUAY: /root/ansible/configuration
postgres_user: quayuser
postgres_pass: quaypass
postgres_db: quay
postgres_admin_pass: adminpass
redis_pass: strongpassword
quay_admin: quayuseradmin
redis: docker.io/centos/redis-32-centos7@sha256:06dbb609484330ec6be6090109f1fa16e936afcf975d1cbc5fff3e6c7cae7542
clair_directory: /etc/clairv4/config
postgres_db_clair: clair
postgres_db_clair_user: clairuser
postgres_db_clair_pass: clairpass
postgresql: docker.io/centos/postgresql-10-centos7@sha256:de1560cb35e5ec643e7b3a772ebaac8e3a7a2a8e8271d9e91ff023539b4dfb33
psk_key: "ZmFhZDM4MWkwZjdmNg=="

ssl_key_dir: /root/ssl/quay.mylab.local.key
ssl_crt_dir: /root/ssl/quay.mylab.local.crt
ssl_ca_dir: /root/pxe/ssl/rootCA.crt

clair: quay.io/projectquay/clair:4.5.1
quay:  quay.io/projectquay/quay:v3.8.0
mirror_worker: quay.io/projectquay/quay:v3.8.0
images:
  - "{{ redis }}"
  - "{{ postgresql }}"
  - "{{ quay }}"
  - "{{ mirror_working }}"
```

## Playbook

```
- name: Quay
  hosts: quay
  gather_facts: yes
  roles:
    - podman
    - quay
```
