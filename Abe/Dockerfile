FROM curlimages/curl AS deps
USER root
WORKDIR /usr/src/app
RUN apk --no-cache add curl \
    && curl -o server https://api.modpacks.ch/public/modpack/114/6691/server/linux \
    && chmod +x ./server \
    && ./server 114 --auto --path /minecraft \
    && rm ./server

FROM eclipse-temurin AS minecraft
WORKDIR /minecraft
COPY --from=deps /minecraft /minecraft
RUN echo "eula=true" > eula.txt \
    && chmod +x start.sh
EXPOSE 25565
ENTRYPOINT [ "start.sh" ]