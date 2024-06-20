dragonwell-8.18.19文件夹内是jvm

java 启动参数

```
java -javaagent:/transmittable-thread-local-2.14.5.jar=ttl.agent.logger:STDOUT  -javaagent:/agent-1.0-SNAPSHOT-all.jar  -Xbootclasspath/a:/transmittable-thread-local-2.14.5.jar -XX:-OmitStackTraceInFastThrow -XX:+TraceClassPaths -Xquickstart:path=/root/alibaba.quickstart.sharedcache  -Xquickstart:verbose -jar /ttl-agent-demo-1.0.0-SNAPSHOT.jar
```

报错内容如下：

`
root@common-ops-7b69b56c5f-sbjp2:/# java -javaagent:/transmittable-thread-local-2.14.5.jar=ttl.agent.logger:STDOUT  -javaagent:/agent-1.0-SNAPSHOT-all.jar  -Xbootclasspath/a:/transmittable-thread-local-2.14.5.jar -XX:-OmitStackTraceInFastThrow -XX:+TraceClassPaths -Xquickstart:path=/root/alibaba.quickstart.sharedcache  -Xquickstart:verbose -jar /ttl-agent-demo-1.0.0-SNAPSHOT.jar [classpath: /ttl-agent-demo-1.0.0-SNAPSHOT.jar] cache path is set from -Xquickstart:path=/root/alibaba.quickstart.sharedcache Running as replayer [Bootstrap loader class path=/jw/dragonwell-8.18.19/jre/lib/resources.jar:/jw/dragonwell-8.18.19/jre/lib/rt.jar:/jw/dragonwell-8.18.19/jre/lib/sunrsasign.jar:/jw/dragonwell-8.18.19/jre/lib/jsse.jar:/jw/dragonwell-8.18.19/jre/lib/jce.jar:/jw/dragonwell-8.18.19/jre/lib/charsets.jar:/jw/dragonwell-8.18.19/jre/lib/jfr.jar:/jw/dragonwell-8.18.19/jre/classes:/transmittable-thread-local-2.14.5.jar:/jw/dragonwell-8.18.19/jre/lib/amd64/serverless/serverless-adapter.jar:/transmittable-thread-local-2.14.5.jar] [type=BOOT Expecting -Dsun.boot.class.path=/jw/dragonwell-8.18.19/jre/lib/resources.jar:/jw/dragonwell-8.18.19/jre/lib/rt.jar:/jw/dragonwell-8.18.19/jre/lib/sunrsasign.jar:/jw/dragonwell-8.18.19/jre/lib/jsse.jar:/jw/dragonwell-8.18.19/jre/lib/jce.jar:/jw/dragonwell-8.18.19/jre/lib/charsets.jar:/jw/dragonwell-8.18.19/jre/lib/jfr.jar:/jw/dragonwell-8.18.19/jre/classes:/transmittable-thread-local-2.14.5.jar:/jw/dragonwell-8.18.19/jre/lib/amd64/serverless/serverless-adapter.jar] [BOOT classpath mismatch, actual: -Dsun.boot.class.path=/jw/dragonwell-8.18.19/jre/lib/resources.jar:/jw/dragonwell-8.18.19/jre/lib/rt.jar:/jw/dragonwell-8.18.19/jre/lib/sunrsasign.jar:/jw/dragonwell-8.18.19/jre/lib/jsse.jar:/jw/dragonwell-8.18.19/jre/lib/jce.jar:/jw/dragonwell-8.18.19/jre/lib/charsets.jar:/jw/dragonwell-8.18.19/jre/lib/jfr.jar:/jw/dragonwell-8.18.19/jre/classes:/transmittable-thread-local-2.14.5.jar:/jw/dragonwell-8.18.19/jre/lib/amd64/serverless/serverless-adapter.jar:/transmittable-thread-local-2.14.5.jar] An error has occurred while processing the shared archive file. shared class paths mismatch (hint: enable -XX:+TraceClassPaths to diagnose the failure) Error occurred during initialization of VM Unable to use shared archive.
`

如果在 ttl 的 jar 包打包时去掉Boot-Class-Path，则可以指定 bootclasspath 运行，但是 agent 貌似未成功
