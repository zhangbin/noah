FROM daocloud.io/tcsoft2016/springboot-maven

ENV RUN_ENV prod

COPY config/pom.xml /tmp/build/
COPY config/src /tmp/build/src

RUN echo "root:Q!W@E#R$" | chpasswd \
    && cd /tmp/build \
    && mkdir /app \
    && mvn clean package -q -P${RUN_ENV} -DskipTests=true \
    && mv target/*.jar /app/config.jar \
    && rm -rf /tmp/build

CMD ["java", "-Xmx200m", "-jar", "-Dspring.config.location=/app/application.yml", "/app/config.jar"]

EXPOSE 8761