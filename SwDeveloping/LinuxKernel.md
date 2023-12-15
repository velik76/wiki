# Table of Contents

- [Table of Contents](#table-of-contents)
  - [ioremap](#ioremap)
  - [How does Linux determine the order of module init calls?](#how-does-linux-determine-the-order-of-module-init-calls)
  - [debugfs](#debugfs)

## ioremap

23.03.2015 [Information to the ioremap in LDD](http://www.makelinux.net/ldd3/chp-9-sect-4)

I have used ioremap in such way:

// PIOE
baseMemGpio = ioremap(0xfffffa00, 0x200);
	printk(KERN_ERR "*************** PIO_PSR  E: 0x%x\n", readl_relaxed(baseMemGpio + 0x08));
	printk(KERN_ERR "*************** PIO_OSR  E: 0x%x\n", readl_relaxed(baseMemGpio + 0x18));
	printk(KERN_ERR "*************** PIO_PUSR E: 0x%x\n", readl_relaxed(baseMemGpio + 0x68));
	printk(KERN_ERR "*************** PIO_ABSR E: 0x%x\n", readl_relaxed(baseMemGpio + 0x78));
iounmap(baseMemGpio);

## How does Linux determine the order of module init calls?

I used arch_initcall() to register plattform struct for the driver. [Link](http://stackoverflow.com/questions/10368837/how-does-linux-determine-the-order-of-module-init-calls)

## debugfs

```shell
mount -t debugfs debugfs /sys/kernel/debug
cat /sys/kernel/debug/gpio
```
