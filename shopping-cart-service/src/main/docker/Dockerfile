FROM 192.168.1.52/tenx_containers/oraclejdk:8u151


ENV PROFILE       development
ENV eureka_host   spring-cloud-discovery
ENV mysql_host    spring-cloud-mysql
ENV edge_service_host    edge-service
ENV user_service_host    user-service
ENV online_store_web    online-store-web

WORKDIR "/app"
VOLUME /tmp
ADD shopping-cart-service-0.0.1-SNAPSHOT.jar /app/app.jar
EXPOSE 8185

CMD ["java", "-Xms256m", "-Xmx1g", \
     "-XX:+UnlockExperimentalVMOptions", \
     "-XX:+UseCGroupMemoryLimitForHeap", \
     "-Dspring.profiles.active=${PROFILE}", \
     "-Dspring.config.location=/app/config", \
     "-Deureka.host${eureka_host}", \
     "-Dmysql.host=${mysql_host}", \
     "-Dedge_service.host=${edge_service_host}", \
     "-Duser_service.host=${user_service_host}", \
     "-Donline_store_web.host=${online_store_web}", \
     "-jar", "/app/app.jar"]