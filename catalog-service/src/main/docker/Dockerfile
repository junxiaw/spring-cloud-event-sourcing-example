FROM 192.168.1.52/tenx_containers/oraclejdk:8u151


ENV PROFILE       development
ENV rabbitmq_host spring-cloud-rabbitmq
ENV rabbitmq_port 5672
ENV eureka_host   spring-cloud-discovery
ENV mysql_host    spring-cloud-mysql
ENV REDIS_HOST    spring-cloud-redis

WORKDIR "/app"
VOLUME /tmp
ADD catalog-service-0.0.1-SNAPSHOT.jar /app/app.jar
EXPOSE 8182

CMD ["java", "-Xms256m", "-Xmx1g", \
     "-XX:+UnlockExperimentalVMOptions", \
     "-XX:+UseCGroupMemoryLimitForHeap", \
     "-Dspring.profiles.active=${PROFILE}", \
     "-Dspring.config.location=/app/config", \
     "-Dmysql.host=${mysql_host}", \
     "-Deureka.host${eureka_host}", \
     "-Drabbitmq.host=${rabbitmq_host}", \
     "-Drabbitmq.port=${rabbitmq_port}", \
     "-Dredis.host=${REDIS_HOST}", \
     "-jar", "/app/app.jar"]