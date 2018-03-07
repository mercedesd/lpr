# LPR HOWTO - Como comenzar a trabajar con LPR (Laboratorio Portatil de Redes)


instalar virtualbox 
verificar que funcione ;-)
crear una maquina virtual llamada lpr
tipo linux 
ubuntu 64 bits
al menos 2 Gb de ram

en caso de usar el disco y no el usb
crear un disco virtual tipo vdi , dinamico de 4G

agregar la iso de lpr en controladora IDE de lectora virtual de la maquina 
y modificar que arranque primero de dvd en orden de booteo

listo !

darle RUN ... (maximizar la ventana apenas arranque la maquina virtual ... si no, despues no se puede)

una vez iniciado loguearse con root lprlpr

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


eso es todo ...

SaluTTY

pd: me estoy dando cuenta que podíamos poner el jpg del grafico de cada práctico en el DVD :-)


