FROM 192.168.1.52/tenx_containers/oraclejdk:8u151


ENV PROFILE       development
ENV EUREKA_HOST   spring-cloud-discovery
ENV REDIS_HOST    spring-cloud-redis
ENV NEO4J_HOST    spring-cloud-neo4j
ENV NEO4J_USERNAME    neo4j
ENV NEO4J_PASSWORD    tenxcloud
WORKDIR "/app"
VOLUME /tmp
ADD inventory-service-0.0.1-SNAPSHOT.jar /app/app.jar
EXPOSE 8183

CMD ["java", "-Xms256m", "-Xmx1g", \
     "-XX:+UnlockExperimentalVMOptions", \
     "-XX:+UseCGroupMemoryLimitForHeap", \
     "-Dspring.profiles.active=${PROFILE}", \
     "-Dspring.config.location=/app/config", \
     "-Deureka.host${EUREKA_HOST}", \
     "-Dredis.host=${REDIS_HOST}", \
     "-Dneo4j.host=${NEO4J_HOST}", \
     "-Dneo4j.username=${NEO4J_USERNAME}", \
     "-Dneo4j.password=${NEO4J_PASSWORD}", \
     "-jar", "/app/app.jar"]
