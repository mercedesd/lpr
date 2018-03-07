# LPR HOWTO - Como comenzar a trabajar con LPR  

se puede trabajar de varias maneras Dependiendo de la necesidad:
### A) Trabajo en distintos lugares, sin posibilidad de modificar el Sistema Operativo de cada PC
Requisitos:
- LiveCD (DVD) o USB (4G) con sistema operativo LPR
- USB (4G) para almacenar imagenes y llevarlas a los distintos lugares   

La imagen de LPR puede ser descargada desde < URL unsl >  

Usar k3b u otra herramienta para grabar el DVD o el USB

Bootear la maquina desde DVD o USB y saltar a la seccion ""D""

### B) Trabajo en distintos lugares, con posibilidad de modificar el Sistema Operativo de cada PC
- Virtualizacion de sistema operativo LPR (Virtualbox, Vmware,etc)
- USB (4G) para almacenar imagenes y llevarlas a los distintos lugares  

La imagen de LPR puede ser descargada desde < URL unsl >  

Usar el virtualizador para crear una maquina virutal llamada LPR con las siguientes caracteristicas:
- Tipo Linux
- ubuntu 64 bits
- al menos 2G de ram
- En almacenamiento conectar la imagen ISO al la lectora de DVD
- Configurar el booteo de la maquina virtual desde DVD
- Conectar el USB a la maquina virtual 

Bootear la maquina virtual y saltar a la seccion ""D"

### B) Trabajo en un solo lugar, con posibilidad de modificar el Sistema Operativo de cada PC
- Virtualizacion de sistema operativo LPR (Virtualbox, Vmware,etc)
- Particion virtual (4G) para almacenar imagenes

La imagen de LPR puede ser descargada desde < URL unsl >

Usar el virtualizador para crear una maquina virutal llamada LPR con las siguientes caracteristicas:
- Tipo Linux
- ubuntu 64 bits
- al menos 2G de ram
- En almacenamiento conectar la imagen ISO al la lectora de DVD
- Configurar el booteo de la maquina virtual desde DVD
- crear un disco virtual tipo vdi , dinamico de 4G

Bootear la maquina virtual y saltaar a la seccion ""D"


### D)

una vez iniciado loguearse con usuario root password lprlpr

aplications -> terminal emulator

hacer un fdisk -l y tomar nota del nombre del disco de 4G que creamos

cd Documents
./inicializar.sh

este procedimiento importara las imagenes al disco que se creo mas arriba

va a pedir como parametro el nombre del disco, luego lo formateará y creará las imagenes de docker 

una vez que termine, podes poner docker images -a para ver que este todo bien ....

dependiendo de la maquina real que tienen, el proceso puede demorar un par de minutos (no mas de eso)


luego cambiarse a ssor

cd ssor
 y ahi estan todos los practicos (hasta ahora probe los 4 primeros)

el script iniciar.sh es para iniciar las practicas .... ( crea los contenedores a partir de las imagenes)
una vez que se cambiaron archivos y configuraciones, se puede guardar ese estado (pausar.sh)
el script pausar.sh hace commit de las maquinas a unas nuevas imagenes llamadas "practico"-nombre_del_contenedor

aca hay dos alternativas :


A) si lo queremos llevar a casa para seguir trabajando luego usamos exportar.sh

ese script pide un disco donde pondremos los archivos tar exportados (usb)

luego en la casa correr importar.sh, que carga en docker las imagenes exportadas anteriormente

finalmente correr continuar.sh

B) en el caso de querer seguir otro dia en el mismo lugar, correr el script continuar.sh, que crea nuevos contenedores a partir de las imagenes temporales guardadas en el script pausar


NOTA: en ambos casos, para el practico de dhcp y dns NO se guarda la configuracion de red ... hay que volver a configurar las placas en los contenedores con ifconfig bla bla bla y las rutas si fueran necesarias, tambien





