This directory contains Linux 3.4.103+ kernel suitable for a **Klipad HC-913** tablet.

- **config.gz** - kernel configuration
- **modules.tar.xz** - kernel loadable modules (to be extracted in /lib/mondules)
- **uImage** - The kernel itself.

### Note
As OTG is enabled, a system running this kernel will always have a load >=1.
It's a known bug in the kernel, which is **harmless** : it's linked with a background tasks for OTG which doesn't impact system performances and/or energy consumption (*check with **top**, the CPU usage is always null on a quiet system).
