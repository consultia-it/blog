---
layout: post
title: "Infraestructura como código (IaC)"
categories: serverless iac
featured_image: IaC_feature_image.png
author: Jesús Gallego
---

Tal como comentamos en el artículo anterior, _Serverless_ es un modelo de desarrollo nativo en la nube que ayuda a los desarrolladores a crear y ejecutar aplicaciones sin necesidad de gestionar servidores. Los servidores siguen existiendo en este modelo, pero están separados del desarrollo de la aplicación. El proveedor de la nube es quien suele llevar a cabo el trabajo rutinario de aprovisionar, mantener y escalar la infraestructura del servidor.

Aunque esto suena muy bien, tampoco es magia. Es necesario definir de alguna manera qué necesita cada entorno para que el proveedor pueda proporcionarlo. Es aquí donde entra en juego la **Infraestructura como Código**, también conocido como **IaC**, por sus siglas en inglés.

> La Infraestructura como código es un proceso que utiliza un lenguaje de codificación descriptivo de alto nivel para automatizar la provisión de la infraestructura de TI.

La Infraestructura como Código **se basa en el principio de idempotencia**, lo que permite configurar los entornos de destino con los mismos ajustes independientemente de su estado inicial. 

El equipo de arquitectura crea descripciones de entornos (o configuraciones) que luego se aplican automáticamente a los entornos necesarios en el pipeline de entrega. Esto asegura un proceso de desarrollo rápido, preciso y más eficiente, ya que introducir ajustes en el entorno se convierte en algo tan sencillo como hacer un cambio en la descripción original. 
Y lo que es más importante, la automatización que conlleva IaC supone una optimización sustancial de los costes, ya que libera el tiempo de los ingenieros de desarrollo, permitiéndoles centrarse en tareas más importantes.

![serverless principales triggers]({{ "/assets/IaC.png" | relative_url }})

Esta automatización **elimina la necesidad de los desarrolladores de aprovisionar y gestionar** manualmente servidores, sistemas operativos, conexiones a bases de datos, almacenamiento y otros elementos de infraestructura **cada vez** que quieren desarrollar, probar o desplegar una aplicación de software en diferentes entornos.

## ¿En qué nos ayuda IaC?

Como ya hemos mencionado, IaC gestiona y proporciona la infraestructura utilizando código en lugar de procesos manuales.

En el pasado, la única forma de gestionar la infraestructura informática era mediante la intervención manual. Había que montar los servidores en los racks, instalar los sistemas operativos y conectar y configurar las redes.  Esto no era tan problemático en su momento porque los ciclos de desarrollo eran tan largos que los cambios de infraestructura no eran frecuentes.

Sin embargo, más tarde, varias tecnologías como la virtualización y la nube, junto con el auge de DevOps y las prácticas ágiles, acortaron los ciclos de desarrollo de software de forma drástica. Debido a esto, hubo una demanda de mejores técnicas de gestión de la infraestructura. Las organizaciones no podían permitirse esperar horas o días para desplegar servidores.

La infraestructura como código es una forma de mejorar el nivel de gestión de la infraestructura y el tiempo de despliegue.  Mediante el uso de un lenguaje declarativo de alto nivel, la IaC ayuda a crear y configurar de forma segura los elementos de infraestructura en cuestión de segundos. Con IaC se crean archivos de configuración, y es en estos donde se definen las especificaciones de su infraestructura, lo que facilita la edición y distribución de las configuraciones.

> Al igual que el mismo código fuente genera siempre el mismo binario, un modelo IaC genera el mismo entorno cada vez que se despliega

Además, la IaC también contribuye a la gestión de la configuración y ayuda a evitar cambios de configuración _ad hoc_ no documentados mediante la codificación y documentación de sus especificaciones de configuración.

## Frameworks IaC

Hay muchas herramientas o _frameworks_ que cumplen con las capacidades de automatización de la infraestructura y utilizan IaC. Echemos un vistazo a la más populares.

![serverless principales triggers]({{ "/assets/IaC - tools.png" | relative_url }})

### Terraform

**Terraform** es una herramienta de código abierto, lo que la hace completamente gratuita y muy flexible. Además de poder personalizarla según las necesidades específicas, también puede aprovechar las diversas herramientas y scripts que la comunidad desarrolla constantemente.

Muy importante también, **Terraform es un orquestador agnóstico de la nube**, lo que significa que puede utilizarse con cualquier servicio nativo (AWS, Azure o GCP). La capacidad de interactuar con las plataformas a través de sus APIs permite a Terraform gestionar infraestructuras en varias plataformas, lo que lo convierte en la opción perfecta para soluciones de nube híbrida.

### AWS CloudFormation

**CloudFormation** es la herramienta de infraestructura como código de AWS. A diferencia de Terraform, no es agnóstica a la nube y está pensada para su uso con la plataforma AWS. Sin embargo, lo compensa al integrarse perfectamente con ella.

Además, CloudFormation está equipado con varias características útiles que mejoran su experiencia en la nube de AWS. Por ejemplo, permite previsualizar cualquier cambio y su efecto antes del despliegue, y retroceder a estados anteriores para evitar que cualquier error llegue a producción.

Por último, al ser la herramienta oficial IaC de AWS, tiene mucha documentación oficial y también garantiza el soporte siempre que sea necesario.

### Azure Resource Manager (ARM)

La herramienta IaC de Azure, **Azure Resource Manager**, es similar a CloudFormation de AWS, sólo que está pensada únicamente para Azure. Como es lógico, viene con una variedad de herramientas útiles que potencian las capacidades de la plataforma Azure. 

Por ejemplo, tiene soporte nativo para el control de acceso basado en roles (RBAC), que permite controlar fácilmente el acceso a todos los servicios. Además, ARM permite desplegar múltiples recursos simultáneamente gracias al uso de plantillas. Por último, tiene excelentes capacidades para la gestión de recursos, ya que permite aplicar etiquetas a los servicios y organizarlos de forma lógica.

### Google Cloud Deployment Manager 

**Google Cloud Deployment Manager** es similar a las herramientas IaC de AWS y Azure en muchos aspectos. Automatiza la creación, la configuración, el aprovisionamiento y la gestión de la plataforma mediante un lenguaje declarativo. Por ejemplo, al igual que con AWS, permite previsualizar los cambios antes del despliegue.

Sin embargo, lo que lo diferencia es su nivel de integración con Google Cloud Platform. Al ofrecer soporte de interfaz de usuario dentro de la consola de desarrollador, esta herramienta permite a los ingenieros visualizar rápidamente la arquitectura de despliegue.

## Buenas prácticas en IaC

Para implementar la IaC con éxito a largo plazo, es muy importante seguir las mejores prácticas. A continuación, se mencionan algunas de ellas.

### Codificar todo en IaC

Todas las especificaciones de la infraestructura deben codificarse explícitamente en el archivo de configuración, como los [playbooks de Ansible](https://www.redhat.com/es/topics/automation/what-is-an-ansible-playbook), las plantillas de AWS CloudFormation o cualquier otra herramienta de IaC que se esté utilizando.

> No se debe caer en la tentación de realizar ajustes manuales en la infraestructura, en lugar de definirlos en el fichero de configuración.

Estos archivos de configuración **deben ser la única fuente de verdad de la especificación de infraestructura** y describen qué componentes de infraestructura se utilizarán y su configuración. También describe la interrelación entre ellos.

Por tanto, todos los cambios deben hacerse a través del archivo de configuración, y luego volver a desplegar cuando haya necesidad de una actualización.

### Reducir la documentación

La definición de la infraestructura en IaC sirve propiamente como documentación, por lo que no hay necesidad de tener documentadas instrucciones adicionales. En el pasado, cuando había que hacer alguna actualización en algún componente de infraestructura, se exigía que la documentación estuviera al día para garantizar que no hubiera espacio para la incoherencia. Sin embargo, esto no siempre ocurría. Con la implantación de IaC, la documentación está siempre actualizada.

### Mantener el código en un sistema de control de versiones

El archivo de configuración debe ser mantenido en sistemas de control de versiones, como Git o Subversión, del mismo modo que cualquier otro código de aplicación.

Con esta práctica se puede rastrear, gestionar y restaurar fácilmente cualquier cambio potencial en los sistemas, con una mayor trazabilidad y visibilidad, además de fomentar la colaboración o revisión por pares.

Proporcionar un control de versiones para IaC es especialmente útil en los casos en los que se necesita depurar y diagnosticar los problemas, o posiblemente revertir a una versión anterior. Además, también permite que el sistema de control de versiones desencadene automáticamente acciones cuando se confirma un cambio, lo que es clave para permitir los pipelines de integración y entrega continuas.

### Cuidado con los datos sensibles en los ficheros de configuración

Tener datos sensibles, como credenciales, expuestos en los ficheros de configuración IaC puede ser un gran riesgo, ya que esto significa potencialmente dar contraseñas a los atacantes y el fracaso de las medidas de autenticación. 

Una buena práctica es **evitar** mantener esos secretos en archivos enviados a un servicio basado en la web, como los sistemas de control de versiones, en lugar de utilizar un almacén de secretos seguro.