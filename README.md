ssh into aws instance. Replace the ip address found on aws for instance.

```
sudo ssh -i credentials/downloader.pem ubuntu@PublicIPv4address
```
The credential directory is ignored by git. You'll have to create a credential dir if you don't have one.

Attach volume:

Go to the aws volume and attach volume. Select downloader instance.

## Creating and mounting volume

SSD gp2 or gp3. gp3 is faster.

You must create a snapshot of the volume for it to be attachable.

To mount the volume from the downloader instance do the following.

1. Attach the volume from aws console.

2. Identify the block device name on downloader instance.

```
lsblk
```

3. Create a file system on the volume if it's new and doesn't have one

Just and example and block device name may differ.

```
sudo mkfs -t ext4 /dev/xvdf
```

4. Mount the volume.

```
sudo mkdir /data
```

5. Confirm by running

```
df -h
```

## Download transmission-cli

```
sudo apt update
sudo apt install transmission-cli
```

Download.

```
transmission-cli <torrent_file_or_magnet_link>
```