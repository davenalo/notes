# SRE - site reliability engineering

Mejorar la fiabilidad del sistema (infraestructura y procesos) actuando sobre sus características como se haría con software.

La fiabilidad en ese sentido se puede medir como la capacidad de controlar esa infraestructura y sus procesos relacionados: en tanto se pueda actuar sobre ellos preveyendo sus capacidades para que no se generen incidencias, más fiable será ese sitio o sistema; por ejemplo automatizando el monitorizado, o sus nuevos lanzamientos.

SLA (Service Level Agreement) hace referencia al acuerdo entre el servicio y el cliente sobre cuanto tiempo el sistema se mantendrá activo; asumiendo que las incidencias nunca van a ser 0, se puede alcanzar un 100% de SLA a través de predicciones y automatizaciones del servicio, pero la cuestión es acordar un límite en que resulta aceptable un porcentaje menor; el máximo permitido.

>Users: no tienen que notar nunca esa fiabilidad, es un proceso interno; sin embargo sí notan las incidencias, que es lo que se quiere evitar a través del control de la fiabilidad. No obstante si hay problemas en, por ejemplo, los dispositivos de esos usuarios o su proveedor de internet, entonces no solo no va a alcanzarse el 100% (no se puede acceder al servicio) si no que además no es necesario. Es una pérdida de SLA aceptable.

Potencialmente, cualquier cambio al sistema puede provocar una disrupción de su fiabilidad. Evidentemente no se pueden detener los cambios, pero se puede controlar la forma de entenderlos, implementarlos, monitorizarlos, etc.

##### Aún y así, qué hacer cuando un corte (outage) sucede?

- La monitorización debe haber podido avisar de posibles problemas en su estado temprano
- La persona indicada, encargada o responsable de diferentes partes del sistema, debe poder ser avisada
- El mensaje automatizado debería contener la máxima información posible, evitando ambigüedades.
>Tal sistema o proceso que pertenece a tal función reporta un traceback o error de un tipo o número concreto. Tratar de responder de forma concisa a las preguntas "cual problema sucede dónde a raíz de qué"
- Comunicar tanto al equipo técnico como al equipo que tiene trato directo con usuarios y clientes la información que se tenga: ayudar a tomar decisiones a uno, y a prever que casos van a tratar con los clientes el otro. De esta manera el valor que aporta conocer las incidencias de forma concreta se puede compartir para que otros equipos trabajen mejor.
- Postmortem: documentar el incidente (outage), las causas, los procesos y datos relacionados, y tomas de decisiones que han tomado las personas encargadas, así como plantear soluciones para minimizar las posibilidades que esas incidencias vuelvan a cometerse. La prioridad, alta o baja, de implantación de esas soluciones dependerá del equipo encargado, su carga de trabajo, situación del servicio, etc.
>En este sentido, el documento de Postmortem no tiene la intención de señalar culpables, ni hacer responsables del problema a un equipo; si no que queda como parte del aprendizaje interno, pudiéndolo acomodar a los protocolos. Se incentiva la búsqueda sincera (científica? en el sentido de que "el conocimiento es bueno por sí mismo") de causas para aprender conjuntamente y no para castigar, de lo contario se viciaría la utilidad del Postmortem en sí mismo.

##### KPI

Key Performance Indicator: indicadores que establecen criterios objetivos (evaluables) para considerar que un proyecto se está realizando de la forma esperada.

>Es un indicador de un proyecto de los de toda la vida, lo que pasa que lo dices en inglés, lo pones en siglas, y parece que sea un concepto que ha salido de un puto garaje de california.



