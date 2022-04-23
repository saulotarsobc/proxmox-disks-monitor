# Proxmox Monitoramento de Discos

## **[Saulo Costa - Telegram](https://t.me/saulotarsobc)**

> Monitoramento de discos das VM's com Python
>
> Lib: paramiko==2.10.3

![GRAFANA](img/exemplo2.png)

## Proxmox

### Comando LVS

```csv
root@pve:~# lvs
  LV            VG  Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  data          pve twi-aotz-- 702.90g             57.29  2.95
  root          pve -wi-ao----  96.00g
  swap          pve -wi-ao----   8.00g
  vm-100-disk-0 pve Vwi-aotz-- 480.00g data        3.57
  vm-101-disk-0 pve Vwi-aotz--  32.00g data        9.76
  vm-102-disk-0 pve Vwi-aotz-- 100.00g data        27.14
  vm-103-disk-0 pve Vwi-aotz-- 200.00g data        38.28
  vm-104-disk-0 pve Vwi-aotz-- 100.00g data        23.06
  vm-105-disk-0 pve Vwi-aotz--  32.00g data        8.69
  vm-106-disk-0 pve Vwi-aotz--  32.00g data        46.28
  vm-107-disk-0 pve Vwi-aotz-- 700.00g data        18.02
  vm-108-disk-0 pve Vwi-aotz-- 480.00g data        4.91
  vm-109-disk-0 pve Vwi-aotz-- 480.00g data        13.38
  vm-110-disk-0 pve Vwi-aotz-- 120.00g data        11.92
  vm-111-disk-0 pve Vwi-aotz--  32.00g data        8.13
  vm-112-disk-0 pve Vwi-a-tz--  32.00g data        0.00
  vm-114-disk-0 pve Vwi-aotz--  32.00g data        22.57
```

## Script + Parâmetros

### Via bash

```sh
script.py [proxmox ip eddress] [proxmox ssh port] [proxmox username] [proxmox password]
```

### Via Discovery

```js
proxmox_disks_ssh[{HOST.IP}, {$SSH_PORT}, {$SSH_USER}, {$SSH_PASS}]
```

## Macro

```js
{#VM} = $..vm.first()
{#PVE} = $..pve.first()
```

## JSON Path

```js
$[?(@.vm == "{#VM}" && @.pve == "{#PVE}")].total.first()
$[?(@.vm == "{#VM}" && @.pve == "{#PVE}")].uso.first()
$[?(@.vm == "{#VM}" && @.pve == "{#PVE}")].uso_percent.first()
```

## Retorno do script

![-](img/exemplo1.png)

## Template Zabbix

### Itens

![itens](img/itens1.png)

### Trigger

![trigger](img/trigger2.png)
