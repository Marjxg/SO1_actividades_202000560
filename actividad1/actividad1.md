Marjorie Gissell Reyes Franco - 202000560

KERNEL

TIPOS DE KERNEL

El Kernel es el software encargado de relacionar el hardware con las aplicaciones del ordenador, es decir, las órdenes del Kernel son las únicas que interactúan con los dispositivos físicos tales como la memoria RAM, el disco duro o el procesador. Este es también conocido como núcleo, dado a que contiene las funciones del sistema operativo utilizadas con mayor frecuencia. En la actualidad existen cuatro tipos de Kernel:
1. Monokernel o Kernel monolítico
2. Exokernel
3. Kernel Híbrido
4. Microkernel
   
Estos se diferencian entre sí por la forma en que organizan y estructuran las funciones básicas del sistema. Tanto el microkernel como el exokernel tienen un tamaño más reducido que el híbrido y el monolítico.

La implementación más conocida del Kernel monolítico es el Kernel de Linux, en este enfoque las funciones básicas del sistema se ejecutan como un solo programa pues sus procedimientos están enlazados entre sí en un programa binario. Por otra parte, los microkernel son desarrollados con un efoque minimalista, pues solo se implementan a nivel de Kernel los elementos principales, lo que disminuye el tamaño en líneas de código. En los microkernel muchos de los elementos que en el monolítico se encuentran a nivel de Kernel se encuentran a nivel de usuario, lo que reduce el tamaño y, por ende, reduce las posibilidades de vulnerabilidades en las líneas de código.

En cuanto al exokernel, este logra un acceso casi directo al hardware por aplicaciones o bibliotecas específicas, pues su función es garantizar la seguridad y multiplexación de los recursos de hardware. El proceso de mantenimiento de este enfoque es complejo, lo que provoca un mayor uso de los enfoques anteriormente mencionados. Por último, el Kernel híbrido contiene código no esencial a nivel Kernel para que este se ejecute más rápido que si estuviera a nivel de usuario. Las implementaciones más conocidas de este enfoque son Microsoft Windows y Mac OS.

MODO USUARIO VS MODO KERNEL

Dependiendo del tipo de código que esté corriendo en el procesador, este puede cambiar entre modos. En términos generales las aplicaciones se ejecutan en modo usuario y los componentes principales del sistema operativo en modo Kernel, mientras que en el caso de los controladores algunos pueden ejecutarse en modo usuario y otros en modo Kernel.

En el modo usuario las aplicaciones carecen de acceso directo a recursos de hardware. Al iniciarse una aplicación en modo usuario se crea un proceso, el cual crea un espacio para direcciones virtuales privadas, al ser privadas no pueden alterar otras aplicaciones y si existe un fallo se limita a la misma aplicación, no afecta otras aplicaciones ni al sistema operativo.

En el modo Kernel hay un aumento de privilegios, lo que trae un riesgo consigo. Todo lo que se inicie en modo Kernel comparte el mismo espacio de direcciones virtuales, al no estar separadas pueden afectarse unas a otras, por lo que si existe una falla el sistema operativo falla.
