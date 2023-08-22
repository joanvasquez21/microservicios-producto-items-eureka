	# microservicios-producto-items-eureka
Implementación de Servidor de Registro Eureka, implementamos servicios como cliente eureka, escalamos con puerto dinámico, biblioteca hystrix para tolerancia a fallos y latencia, configuracion puerta de enlace zuul y fitros(pre,post))
1.-Creamos un nuevo proyecto llamado springboot-servicio-eurekaserver y en el pom o a traves de la herramienta de sts añadimos la dependencia  de eureka.server en el POM.

```

	<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
		</dependency>
```
2.-En los microservicios clientes añadimos la dependencia eureka-client

```
<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
</dependency>
```
