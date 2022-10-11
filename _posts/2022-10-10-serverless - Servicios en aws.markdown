---
layout: post
title: "Servicios Serverless en AWS"
categories: serverless aws
featured_image: Amazon Web Services.png
---

AWS ofrece una amplia gama de servicios en la nube que cubren todos los aspectos y requisitos de las soluciones de _backend_, como recursos de cómputo, diferentes tipos de almacenamiento, servicios de bases de datos, servicios de seguridad para autenticación y cifrado, procesamiento de flujos de _big data_, servicios de _machine learning_, servicios de mensajería y monitorización y muchos más.

Estos servicios están estrechamente integrados entre sí y proporcionan una manera conveniente de construir aplicaciones de una manera flexible y potente. En este artículo vamos a darle un vistazo general a los **servicios sin servidor más importantes de AWS**. En un artículo posterior, veremos algunos casos de uso para mostrar cómo se pueden utilizar para crear aplicaciones sin servidor.

## AWS Lambda

[AWS Lambda](https://aws.amazon.com/es/lambda/) nos permite ejecutar código como una función activada por varias fuentes de eventos como, por ejemplo: solicitudes HTTP a través del AWS API Gateway, actualizaciones de archivos en S3 o alarmas de métricas en AWS Cloudwatch.

Lambda es la solución FaaS (Function as a Service) de AWS donde se puede ejecutar código para cualquier tipo de aplicación o servicio _backend_. Sólo es necesario configurar y cargar el código y Lambda se encarga del resto. El código se ejecuta en una infraestructura totalmente gestionada y de alta disponibilidad, y realiza todas las tareas de administración de los recursos informáticos, incluido el mantenimiento del servidor y del sistema, el aprovisionamiento de capacidad y el escalado automático, la monitorización del código y el registro de logs. Sólo se paga por el tiempo de computación que la aplicación realmente consume. 

Lambda puede combinarse con muchos otros servicios de AWS y es posible utilizarlo en muchos escenarios, como la autorización de una solicitud HTTP mediante la validación de un token web JSON, el filtrado y la transformación de datos en _streaming_ en tiempo real, el procesamiento de ficheros tras ser almacenados en S3, la gestión de bases de datos y muchos más.

## AWS Fargate

[AWS Fargate](https://aws.amazon.com/es/fargate/) nos permite ejecutar contenedores Docker sin necesidad de administrar servidores o clústeres. Es una solución de orquestación de contenedores que facilita la implementación, la administración y el escalado de aplicaciones en contenedores. No es necesario definir los tipos de instancia EC2, ni gestionar la programación de clústeres, ni optimizar la utilización de los servidores o definir las métricas de vigilancia de la nube para escalar las instancias. Fargate gestiona la infraestructura necesaria para ejecutar sus contenedores de forma altamente disponible. 

Para lanzar una aplicación, tan sólo es necesario empaquetar los contenedores, especificar los requisitos de CPU y memoria, y definir las políticas de red y de IAM.

Éste es un servicio especialmente interesante para arquitecturas de microservicios.

## Amazon S3

[Amazon Simple Storage Service](https://aws.amazon.com/es/s3/) (Amazon S3) ofrece a los desarrolladores y equipos de TI un almacenamiento seguro, duradero y altamente escalable a un costo muy bajo. Podemos almacenar y recuperar cualquier cantidad de datos, en cualquier momento, desde cualquier lugar de la web a través de una sencilla interfaz de servicio web. Podemos escribir, leer y eliminar objetos de hasta 5 TB de datos. 

Amazon S3 permite el acceso concurrente de lectura o escritura a los datos por parte de muchos clientes o hilos de aplicación independientes. Además, puede ser escalado infinitamente, lo que significa que no es necesario especificar la cantidad de almacenamiento que se necesita al crear un _bucket_ de S3.

Podríamos usar Amazon S3 como plataforma para alojar sitios web estáticos, como almacenamiento de copias de seguridad, para guardar archivos estáticos o multimedia (como fotos y vídeos) para aplicaciones web o móviles.

También proporciona servicios como la encriptación y el versionado, donde puedes encriptar el contenido de un _bucket_ y también habilitar el versionado que te ayuda a retroceder a una versión anterior de una manera más rápida y fácil.

## Amazon DynamoDB

[Amazon DynamoDB](https://aws.amazon.com/es/dynamodb/) es un servicio base de datos NoSQL de clave-valor y documentos, diseñada para ejecutar aplicaciones de alto desempeño a cualquier escala, debido a la baja latencia en el acceso (muy pocos milisegundos). Es completamente escalable, de hecho, se puede decir que proporciona almacenamiento ilimitado.

DynamoDB ofrece seguridad integrada, copias de seguridad continuas, replicación multirregional automatizada, almacenamiento de caché en memoria y herramientas de exportación de datos.

## AWS API Gateway
