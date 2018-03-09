# LPR HOWTO - Como comenzar a trabajar con LPR  

se puede trabajar de varias maneras Dependiendo de la necesidad:
### A) Trabajo en distintos lugares, sin acceder/modificar el disco de cada PC
1. Requisitos:
  - LiveCD (DVD) o USB (4G) con sistema operativo LPR
  - USB (4G) para almacenar imagenes y llevarlas a los distintos lugares   

2. Configuracion inicial:  
  - La imagen de LPR puede ser descargada desde < URL unsl >  

  - Usar k3b u otra herramienta para grabar la imagen ISO descargada en un DVD o USB

  - Bootear la maquina desde DVD o USB, segun corresponda 
  
3. Continuar en la seccion **D**  

### B) Trabajo en distintos lugares, pudiendo acceder/modificar el disco de cada PC
1. Requisitos:
  - Virtualizacion de sistema operativo LPR (Virtualbox, Vmware,etc)
  - USB (4G) para almacenar imagenes y llevarlas a los distintos lugares  
  
2. Configuracion inicial:  
  - La imagen de LPR puede ser descargada desde < URL unsl >  
  - Usar el virtualizador para crear una maquina virutal llamada LPR con las siguientes caracteristicas:
    - Tipo Linux
    - ubuntu 64 bits
    - al menos 2G de ram
    - En almacenamiento conectar la imagen ISO descargada al la lectora de DVD
    - Configurar el booteo de la maquina virtual desde DVD
    - Conectar el USB a la maquina virtual 
  - Bootear la maquina virtual
3. Continuar en a la seccion **D**

### C) Trabajo en un solo lugar, pudiendo acceder/modificar el dico de cada PC
1. Requisitos:
  - Virtualizacion de sistema operativo LPR (Virtualbox, Vmware,etc)
  - Espacio en disco rpigido al menos 4Gb) para crear una Particion virtual

2. Configuracion inicial:  
  - La imagen de LPR puede ser descargada desde < URL unsl >
  - Usar el virtualizador para crear una maquina virutal llamada LPR con las siguientes caracteristicas:
    - Tipo Linux
    - ubuntu 64 bits
    - al menos 2G de ram
    - En almacenamiento conectar la imagen ISO al la lectora de DVD
    - Configurar el booteo de la maquina virtual desde DVD
    - crear un disco virtual tipo vdi , dinamico de al menos 4Gb

  -Bootear la maquina virtual 
  3. Continuar en la seccion **D**


### D) Inicialización de imagenes de Docker

  - loguearse con usuario *root* password *lprlpr*
  - En el menu, seleccionar aplications -> terminal emulator
  - Averiguar el nombre de la particion que se usará para alamcenar las imagenes de docker
    - Para ello escribir el siguente comando en la terminal y tomar nota del nombre del disco de 4G que creamos o el usb que conectamos
      - fdisk -l
  - Cambiarse al directorio *Documents* e inicializar las imagenes docker.
    - Para ello ejecutar los siguentes comandos en la terminal:
      - cd Documents
      - ./inicializar.sh
  - Este procedimiento importara las imagenes al disco que se creo mas arriba. Pide como parametro el nombre del disco, luego lo formateará y creará las imagenes de docker
    - una vez que termine, se puede verificar las imagenes importadas ejecutand el comando:
      - docker images -a
  - NOTA: dependiendo de la maquina real que tienen y la velocidad de acceso de USB, el proceso puede demorar desde un par de minutos a 10 minutos ...
  - Ahora estan en condiciones de hacer los practicos.
    - Para ello ejecutan los siguientes comando en la terminal:
      - cd ssor
      - cd NOMBRE_DEL_PRACTICO
      - ./iniciar.sh
    
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





