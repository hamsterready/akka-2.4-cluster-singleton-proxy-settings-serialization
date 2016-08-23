Problem with ClusterSingletonProxySettings serialization.

```
> test
[warn] Scala version was updated by one of library dependencies:
[warn] 	* org.scala-lang:scala-library:2.11.7 -> 2.11.8
[warn] To force scalaVersion, add the following:
[warn] 	ivyScala := ivyScala.value map { _.copy(overrideScalaVersion = true) }
[warn] Run 'evicted' to see detailed eviction warnings
[info] Compiling 1 Scala source to /home/hamster/Downloads/akka-sample-multi-node-scala/target/scala-2.11/multi-jvm-classes...
[info] * sample.multinode.MultiNodeSampleSpec
[JVM-1] Run starting. Expected test count is: 2
[JVM-1] MultiNodeSampleSpecMultiJvmNode1:
[JVM-1] A MultiNodeSample
[JVM-2] Run starting. Expected test count is: 2
[JVM-2] MultiNodeSampleSpecMultiJvmNode2:
[JVM-2] A MultiNodeSample
[JVM-2] - must wait for all nodes to enter a barrier
[JVM-1] - must wait for all nodes to enter a barrier
[JVM-1] [ERROR] [08/23/2016 12:35:26.159] [MultiNodeSample-akka.remote.default-remote-dispatcher-6] [akka.tcp://MultiNodeSample@localhost:34446/system/endpointManager/reliableEndpointWriter-akka.tcp%3A%2F%2FMultiNodeSample%40localhost%3A35960-0/endpointWriter] Transient association error (association remains live)
[JVM-1] java.io.NotSerializableException: No configured serialization-bindings for class [akka.cluster.singleton.ClusterSingletonProxySettings]
[JVM-1] 	at akka.serialization.Serialization.serializerFor(Serialization.scala:172)
[JVM-1] 	at akka.serialization.Serialization.findSerializerFor(Serialization.scala:151)
[JVM-1] 	at akka.remote.serialization.MessageContainerSerializer.serializeSelection(MessageContainerSerializer.scala:43)
[JVM-1] 	at akka.remote.serialization.MessageContainerSerializer.toBinary(MessageContainerSerializer.scala:34)
[JVM-1] 	at akka.remote.MessageSerializer$.serialize(MessageSerializer.scala:37)
[JVM-1] 	at akka.remote.EndpointWriter$$anonfun$serializeMessage$1.apply(Endpoint.scala:886)
[JVM-1] 	at akka.remote.EndpointWriter$$anonfun$serializeMessage$1.apply(Endpoint.scala:886)
[JVM-1] 	at scala.util.DynamicVariable.withValue(DynamicVariable.scala:58)
[JVM-1] 	at akka.remote.EndpointWriter.serializeMessage(Endpoint.scala:885)
[JVM-1] 	at akka.remote.EndpointWriter.writeSend(Endpoint.scala:780)
[JVM-1] 	at akka.remote.EndpointWriter.delegate$1(Endpoint.scala:669)
[JVM-1] 	at akka.remote.EndpointWriter.writeLoop$1(Endpoint.scala:680)
[JVM-1] 	at akka.remote.EndpointWriter.sendBufferedMessages(Endpoint.scala:693)
[JVM-1] 	at akka.remote.EndpointWriter.becomeWritingOrSendBufferedMessages(Endpoint.scala:639)
[JVM-1] 	at akka.remote.EndpointWriter$$anonfun$initializing$1.applyOrElse(Endpoint.scala:613)
[JVM-1] 	at akka.actor.Actor$class.aroundReceive(Actor.scala:484)
[JVM-1] 	at akka.remote.EndpointActor.aroundReceive(Endpoint.scala:447)
[JVM-1] 	at akka.actor.ActorCell.receiveMessage(ActorCell.scala:526)
[JVM-1] 	at akka.actor.ActorCell.invoke(ActorCell.scala:495)
[JVM-1] 	at akka.dispatch.Mailbox.processMailbox(Mailbox.scala:257)
[JVM-1] 	at akka.dispatch.Mailbox.run(Mailbox.scala:224)
[JVM-1] 	at akka.dispatch.Mailbox.exec(Mailbox.scala:234)
[JVM-1] 	at scala.concurrent.forkjoin.ForkJoinTask.doExec(ForkJoinTask.java:260)
[JVM-1] 	at scala.concurrent.forkjoin.ForkJoinPool$WorkQueue.runTask(ForkJoinPool.java:1339)
[JVM-1] 	at scala.concurrent.forkjoin.ForkJoinPool.runWorker(ForkJoinPool.java:1979)
[JVM-1] 	at scala.concurrent.forkjoin.ForkJoinWorkerThread.run(ForkJoinWorkerThread.java:107)
[JVM-1] 
[JVM-1] - must send to and receive from a remote node *** FAILED ***
[JVM-1]   java.lang.AssertionError: assertion failed: timeout (10 seconds) during expectMsg while waiting for pong
[JVM-1]   at scala.Predef$.assert(Predef.scala:170)
[JVM-1]   at akka.testkit.TestKitBase$class.expectMsg_internal(TestKit.scala:350)
[JVM-1]   at akka.testkit.TestKitBase$class.expectMsg(TestKit.scala:336)
[JVM-1]   at akka.testkit.TestKit.expectMsg(TestKit.scala:737)
[JVM-1]   at sample.multinode.MultiNodeSample$$anonfun$1$$anonfun$apply$mcV$sp$2$$anonfun$apply$mcV$sp$3.apply$mcV$sp(MultiNodeSample.scala:69)
[JVM-1]   at akka.remote.testkit.MultiNodeSpec.runOn(MultiNodeSpec.scala:335)
[JVM-1]   at sample.multinode.MultiNodeSample$$anonfun$1$$anonfun$apply$mcV$sp$2.apply$mcV$sp(MultiNodeSample.scala:64)
[JVM-1]   at sample.multinode.MultiNodeSample$$anonfun$1$$anonfun$apply$mcV$sp$2.apply(MultiNodeSample.scala:63)
[JVM-1]   at sample.multinode.MultiNodeSample$$anonfun$1$$anonfun$apply$mcV$sp$2.apply(MultiNodeSample.scala:63)
[JVM-1]   at org.scalatest.Transformer$$anonfun$apply$1.apply$mcV$sp(Transformer.scala:22)
[JVM-1]   ...
[JVM-2] - must send to and receive from a remote node
[JVM-1] [ERROR] [08/23/2016 12:35:36.121] [MultiNodeSample-akka.remote.default-remote-dispatcher-6] [akka.tcp://MultiNodeSample@localhost:34446/system/endpointManager/reliableEndpointWriter-akka.tcp%3A%2F%2FMultiNodeSample%40localhost%3A35960-0/endpointWriter] AssociationError [akka.tcp://MultiNodeSample@localhost:34446] -> [akka.tcp://MultiNodeSample@localhost:35960]: Error [Shut down address: akka.tcp://MultiNodeSample@localhost:35960] [
[JVM-1] akka.remote.ShutDownAssociation: Shut down address: akka.tcp://MultiNodeSample@localhost:35960
[JVM-1] Caused by: akka.remote.transport.Transport$InvalidAssociationException: The remote system terminated the association because it is shutting down.
[JVM-1] ]
[JVM-2] Run completed in 11 seconds, 155 milliseconds.
[JVM-2] Total number of tests run: 2
[JVM-2] Suites: completed 1, aborted 0
[JVM-2] Tests: succeeded 2, failed 0, canceled 0, ignored 0, pending 0
[JVM-2] All tests passed.
[JVM-1] [WARN] [08/23/2016 12:35:36.190] [MultiNodeSample-akka.actor.default-dispatcher-15] [akka://MultiNodeSample/user/controller/127.0.0.1:45630-server1] received dead letter from Actor[akka://MultiNodeSample/deadLetters]: ClientDisconnected
[JVM-1] Run completed in 11 seconds, 246 milliseconds.
[JVM-1] Total number of tests run: 2
[JVM-1] Suites: completed 1, aborted 0
[JVM-1] Tests: succeeded 1, failed 1, canceled 0, ignored 0, pending 0
[JVM-1] *** 1 TEST FAILED ***
[error] Failed: sample.multinode.MultiNodeSampleSpecMultiJvmNode1
[info] Run completed in 9 milliseconds.
[info] Total number of tests run: 0
[info] Suites: completed 0, aborted 0
[info] Tests: succeeded 0, failed 0, canceled 0, ignored 0, pending 0
[info] No tests were executed.
[error] Failed tests:
[error] 	sample.multinode.MultiNodeSampleSpec
[error] (test:test) sbt.TestsFailedException: Tests unsuccessful
[error] Total time: 13 s, completed Aug 23, 2016 12:35:36 PM

```
