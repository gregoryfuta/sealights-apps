FROM tomcat:8.5.29-jre8-alpine

COPY test.txt /opt/test2.txt
COPY sl-token.txt /opt/sl-token.txt
COPY java-agent-bootstrapper-ftv-4.0.0-SNAPSHOT.jar /opt/sl-cd-agent.jar
COPY context.xml /usr/local/tomcat/conf

RUN mkdir /opt/xws
COPY xws2.zip /opt/xws
WORKDIR /opt/xws
RUN unzip xws2.zip
RUN rm -f xws2.zip

WORKDIR /usr/local/tomcat/webapps
RUN ln -s /opt/xws xws

# -Dci.sl.propertiesActive=true
# -Dsl.tokenFile=/opt/sl-token.txt
ENV circle_node_index test-for-yishay
ENV CATALINA_OPTS -javaagent:/opt/sl-cd-agent.jar -Dsl.appName=xws -Dsl.tokenFile=/opt/sl-token.txt -Dsl.buildName=raiff.002 -Dsl.labId=integ_main_xws -Dsl.includes=i01.sealights.* -Dsl.log.level=debug -Dsl.log.toConsole=true -Dsl.logback=true -Dsl.log.toFile=true -Dsl.workspace=/usr/local/tomcat/webapps/xws -Dsl.log.folder=/opt -Dsl.log.filename=custom-file.name.log
ENV sl_token eyJhbGciOiJSUzUxMiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJodHRwczovL0RFVi1ncmVnLmF1dGguc2VhbGlnaHRzLmlvLyIsImp3dGlkIjoiREVWLWdyZWcsaS0wOGFjODQxODlhYWFhZWFkMyxBUElHVy0zM2M0MTY5MS02MTU1LTRhMzktYTU5OC0yZjVkMGE0YTE4NGQsMTY4MjU3NzEwODA1NSIsInN1YmplY3QiOiJTZWFMaWdodHNAYWdlbnQiLCJhdWRpZW5jZSI6WyJhZ2VudHMiXSwieC1zbC1yb2xlIjoiYWdlbnQiLCJ4LXNsLXNlcnZlciI6Imh0dHBzOi8vZGV2LWdyZWctZ3cuZGV2LnNlYWxpZ2h0cy5jby9hcGkiLCJzbF9pbXBlcl9zdWJqZWN0IjoiIiwiaWF0IjoxNjgyNTc3MTA4fQ.ZqDvrmq1mrCPqWNE7p900fImKTnYZmV0ZBkte0aEF0BTDXn7b4wjsBpgvkmeCfZxgd8fSqxmFniqEsLaWNOJ_mQKLpfQP7rKUEJyy629r5Ni-eouh8wxLlCuWPLnkSBLG4gSEy7NUjfPCQT0hzOjSVQ61GJNEaqJ2QxpGihf85RiFwArxA-mIHa8QB1vSgAJfRePlX8foPF2exce43JdJobLYSCsqDv0cmxHHV813TPgxclMVX1R7a20nOJ0GkaMEel3GSXCVhhxbSW2tOK-WgCoOJIypP7RNBUnUU2t2zHh8_FrfpHweIKWOQK22mpKqpGTqc7y7Df0pX7rXXDWs3Fx_ayTBP-PmU2LMlv4tptKwKTtbz9uFkUasWmH27tnMEw06M9mJGecKYPzaGdMDNn2a814XnMKRlbnv2O_Ux8cvHhb2aUX4zqmU_cDCPw4dJY46wFjATkzDN8hwak0R8XXUK1STNW9ksc4gbbXkiuHybs7c7gdo0QiHnClu3KU3Rh_Ml0RScXCVBlXHJF9DXc7UueLI5mGBFfEUxas6zYQvft4QElj4caPIOYOI7Ss-vgjAJ1lQHqKcWZPBf_5hRK16woiAdix6oag1aR5EYeUZ4IQV5pshyxIhg3I4bJr3oZok_JBWa4LuRoa1Q7_f_09aR6-LQ8nlGxLbd5nCdQ