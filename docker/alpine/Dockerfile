FROM eclipse-temurin:11-jre-alpine

RUN apk --no-cache add --update bash openssl

RUN addgroup jportal2 && adduser -S -h /jportal2 -D -G jportal2 jportal2
WORKDIR /jportal2

USER jportal2

ARG jportal2_version
ENV JPORTAL2_VERSION=${jportal2_version}

COPY ./target/jportal2-$JPORTAL2_VERSION.jar /jportal2
COPY --chown=jportal2:jportal2 ./docker/jportal2.sh /jportal2

ENV PATH="/jportal2:${PATH}"

RUN chmod 755 /jportal2/jportal2.sh
ENTRYPOINT ["/jportal2/jportal2.sh"]
CMD ["-?"]