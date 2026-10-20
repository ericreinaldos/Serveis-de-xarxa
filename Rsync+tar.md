(1) Hacer una copia en local con RSYNC. Repite el proceso con TAR.GZ

<img width="737" height="481" alt="image" src="https://github.com/user-attachments/assets/691ab018-b073-4413-a2b3-2b8f91d6ffcf" />

Como no hacen falta dos VM, uso el Debian como un equipo y mi PC como el otro. Para que se vean, le añadí a la VM un segundo adaptador de red en modo solo-anfitrión (el primero sigue en NAT para tener internet). 
Luego miré que la VM tuviera IP nueva, instalé SSH y rsync, y lo he comprobado con un ping desde el PC que se veían.Ç


Paso 1: Red de la VM (NAT + host-only)

Uso el Debian como un equipo y mi PC como el otro. A la VM le puse dos adaptadores: NAT (para internet) y solo-anfitrión (para verse con el PC). La NAT no cogía IP porque en /etc/network/interfaces estaba mal escrito allow hotplug (sin guion). 
Lo corregí a allow-hotplug enp0s3, reinicié la red y ya cogió 10.0.2.15. El host-only tiene IP fija 192.168.6.100.
<img width="739" height="484" alt="image" src="https://github.com/user-attachments/assets/73d2c767-c400-4271-8846-ee6834796729" />

Instalé `openssh-server` y `rsync` en el Debian y activé el servicio SSH para que arranque solo. Comprobé con `systemctl status ssh` que estaba en `active (running)`.
<img width="735" height="479" alt="image" src="https://github.com/user-attachments/assets/3a343e5e-c833-48cb-bbff-6d511b742e0a" />

Desde el PC (Windows) probé a conectarme a la VM. Al principio no se veían porque la IP de la VM estaba en otro rango (192.168.6.x) y el adaptador host-only del PC es 192.168.56.1. 
Cambié la IP de la VM a 192.168.56.100 en /etc/network/interfaces, reinicié la red y ya hubo ping y SSH.
