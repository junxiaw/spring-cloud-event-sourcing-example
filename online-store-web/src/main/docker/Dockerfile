FROM 192.168.1.52/tenx_containers/oraclejdk:8u151


ENV PROFILE       development
ENV eureka_host   spring-cloud-discovery
ENV edge_service_host    edge-service
ENV user_service_host    user-service
ENV public_user_service  msa-user-service-8181.tenxapp.com:17869

WORKDIR "/app"
VOLUME /tmp
ADD online-store-web-0.0.1-SNAPSHOT.jar /app/app.jar
EXPOSE 8787

CMD ["java", "-Xms256m", "-Xmx1g", \
     "-XX:+UnlockExperimentalVMOptions", \
     "-XX:+UseCGroupMemoryLimitForHeap", \
     "-Dspring.profiles.active=${PROFILE}", \
     "-Dspring.config.location=/app/config", \
     "-Deureka.host${eureka_host}", \
     "-Dedge_service.host=${edge_service_host}", \
     "-Duser_service.host=${user_service_host}", \
     "-Dpublic_user_service.host=${public_user_service}", \
     "-jar", "/app/app.jar"]