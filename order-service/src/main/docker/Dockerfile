FROM 192.168.1.52/tenx_containers/oraclejdk:8u151


ENV PROFILE       development
ENV mongo_host    spring-cloud-mongo
ENV eureka_host   spring-cloud-discovery
ENV user_service_host    user-service

WORKDIR "/app"
VOLUME /tmp
ADD order-service-0.0.1-SNAPSHOT.jar /app/app.jar
EXPOSE 8186

CMD ["java", "-Xms256m", "-Xmx1g", \
     "-XX:+UnlockExperimentalVMOptions", \
     "-XX:+UseCGroupMemoryLimitForHeap", \
     "-Dspring.profiles.active=${PROFILE}", \
     "-Dspring.config.location=/app/config", \
     "-Dmongo.host=${mongo_host}", \
     "-Deureka.host${eureka_host}", \
     "-Duser_service.host=${user_service_host}", \
     "-jar", "/app/app.jar"]
