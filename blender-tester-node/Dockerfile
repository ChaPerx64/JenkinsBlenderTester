# FROM jenkins/inbound-agent:windowsservercore-ltsc2019
FROM jenkins/inbound-agent:alpine-jdk11 as jnlp

FROM python:3.11.5-bookworm

RUN apt-get update
RUN apt-get install -y default-jre

COPY --from=jnlp /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=jnlp /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar

COPY blender-engine /blender-engine
RUN ln -s /blender-engine/blender /usr/local/bin

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

ENTRYPOINT ["/usr/local/bin/jenkins-agent"]
