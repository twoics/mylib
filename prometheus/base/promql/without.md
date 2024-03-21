

	Предобрабатывает ряд, агрегация будет выполняться игнорируя метки указанные в
	without

Есть временной ряд
```
node_filesystem_free_bytes{device="/dev/sda1",fstype="vfat",
instance="localhost:9100",job="node",mountpoint="/boot/efi"} 1

node_filesystem_free_bytes{device="/dev/sda5",fstype="ext4",
instance="localhost:9100",job="node",mountpoint="/"} 2
```

```PromQL
>>> sum without(device, fstype, mountpoint)
{instance="localhost:9100",job="node"} 3
```
