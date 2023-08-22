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
5.- Añadimos la anotación @HystrixCommand(fallbackMethod="nombredelmetodoalternativo")
![image](https://github.com/joanvasquez21/microservicios-producto-items-eureka/assets/70104624/fb92867e-6c5b-4d78-be82-dd6add92976c)
6.- Configurando los timeout para hystrix, añadimos en el application.properties
```
hystrix.command.default.execution.isolation.thread.timeoutInMilliseconds: 130000
ribbon.ConnectTimeout: 3000
ribbon.ReadTimeout: 10000
```
hystrix.command.default.execution.isolation.thread.timeoutInMilliseconds: 130000
Esta configuración establece el tiempo maximo (en milisegundos) que Hystrix esperara por la respuesta de un comando antes de considerarlo como una solicitud que ha excedido el tiempo de espera y debe ser manejada de acuerdo a las políticas de Hystrix (como activar el circuit breaker o ejecutar una lógica de respaldo).
ribbon.ConnectTimeout: 3000
Esta configuración se refiere a la cantidad de tiempo (en milisegundos) que el cliente Ribbon (utilizado para el balanceo de carga en entornos de microservicios) esperará para establecer una conexión con un servicio.
ribbon.ReadTimeout: 10000
Esta configuración se relaciona con el tiempo máximo (en milisegundos) que el cliente Ribbon esperará para recibir la respuesta de un servicio después de haber establecido la conexión.
