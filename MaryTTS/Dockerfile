ARG BUILD_FROM
FROM $BUILD_FROM AS BUILD


RUN apk add --no-cache \
		'wget=1.21.1-r1' \
		'unzip=6.0-r8'

ENV MARYTTS_VERSION 5.2
RUN wget -q --show-progress "https://github.com/marytts/marytts/releases/download/v${MARYTTS_VERSION}/marytts-${MARYTTS_VERSION}.zip" &&\
    unzip marytts-${MARYTTS_VERSION}.zip -d / && mv /marytts-${MARYTTS_VERSION} /app

FROM $BUILD_FROM AS RUNNING


RUN apk update && \
    apk add --no-cache 'openjdk8=8.272.10-r4'

COPY --from=BUILD /app /app

COPY root /
