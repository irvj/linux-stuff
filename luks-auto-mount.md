## Auto-Mount a LUKS Partition

### Create Secret Key

    $ dd if=/dev/urandom of=/etc/luks-keys/disk_secret_key bs=512 count=8

### Add Key To Partition's Key Slots With Current Password

    $ sudo cryptsetup -v luksAddKey /dev/sda1 /etc/luks-keys/disk_secret_key    #change /dev/sda1 to actual location of your partition
    Enter any passphrase: passphrase
    Key slot 0 unlocked.
    Command successful.

### Check To See If Key Add Was Successful

    $ sudo cryptsetup luksDump /dev/sda1 | grep "Key Slot"
    Key Slot 0: ENABLED
    Key Slot 1: ENABLED     #This is probably your new key
    Key Slot 2: DISABLED
    Key Slot 3: DISABLED
    Key Slot 4: DISABLED
    Key Slot 5: DISABLED
    Key Slot 6: DISABLED
    Key Slot 7: DISABLED

### Get UUID Of Partition

    $ sudo cryptsetup luksDump /dev/sda1 | grep "UUID"
    UUID: 2a2375bf-2262-413c-a6a8-fbeb14659c85          #just an example UUID, yours will be different

### Add UUID To Crypttab

    $ sudo nano /etc/crypttab
    sda1_crypt UUID=2a2375bf-2262-413c-a6a8-fbeb14659c85 /etc/luks-keys/disk_secret_key luks

### Map Crypttab to Fstab

    $ sudo nano /etc/fstab
    /dev/mapper/sda1_crypt /home/user/data ext4    defaults   0       2
