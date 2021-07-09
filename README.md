## NFS-Server into Alpine OS
-----

#### Pull image
```
docker pull izone/nfs-server
```
#### Run
```
docker run -name nfs \
--restart=unless-stopped \
-p 2049:2049 \
-v /mnt/nfs_share:/mnt/nfs_share \
-v /etc/exports.txt:/etc/exports:ro \
--cap-add SYS_ADMIN \
-d izone/nfs-server
```
```
docker run -name nfs \
--restart=unless-stopped \
-p 2049:2049 \
-v /mnt/nfs_share:/mnt/nfs_share \
-e NFS_EXPORT_0='/mnt/nfs_share                  *(ro,no_subtree_check)' \
-e NFS_EXPORT_1='/mnt/nfs_share 123.123.123.123/32(rw,no_subtree_check)' \
--cap-add SYS_ADMIN \
-d izone/nfs-server
```
-----
#### Build
```
docker build -t izone/nfs-server .
```

