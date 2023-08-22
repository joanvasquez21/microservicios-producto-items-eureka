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
3.-Escalamos microservicios con puertos dinámicos,  generamos instancias distintas en un puerto distinto
![image](https://github.com/joanvasquez21/microservicios-producto-items-eureka/assets/70104624/6edba286-0297-49a5-8a0d-6f96aa3da147)

4.- Para trabajar con tolerancia a fallos y latencia en hystrix agregamos la siguiente dependencia 
```
<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-netflix-hystrix</artifactId>
</dependency>
```
y añadimos la anotación @EnableCircuitBraker en la clase principal para habilitarlo.
![image](https://github.com/joanvasquez21/microservicios-producto-items-eureka/assets/70104624/1ca75841-1650-404e-be82-7852232361aa)

