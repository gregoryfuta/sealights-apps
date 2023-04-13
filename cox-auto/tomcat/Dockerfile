FROM tomcat:8.5.29-jre8-alpine

COPY test.txt /opt/test.txt
COPY sl-token.txt /opt/sl-token.txt
COPY java-agent-bootstrapper-ftv-4.0.2242.jar /opt/sl-cd-agent.jar
RUN mkdir /usr/local/tomcat/webapps/xws
COPY xws.zip /usr/local/tomcat/webapps/xws
COPY context.xml /usr/local/tomcat/conf

RUN cd /usr/local/tomcat/webapps/xws
RUN unzip xws.zip
RUN rm -f xws.zip

ENV CATALINA_OPTS -javaagent:/opt/sl-cd-agent.jar -Dsl.appName=xws -Dsl.buildName=cox.001 -Dsl.labId=integ_main_xws -Dsl.includes=*i0.sealights.* -Dsl.log.level=debug -Dsl.log.toConsole=true -Dsl.tokenFile=/opt/sl-token.txt -Dsl.logback=true -Dsl.log.toFile=true -Dsl.workspace=/usr/local/tomcat/webapps/xws