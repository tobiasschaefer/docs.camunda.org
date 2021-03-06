---

title: 'bpm-platform.xml'
category: 'Descriptors'

---


The `bpm-platform.xml` file is part of the camunda BPM platform distribution and can be used for configuring process engines and the job executor.

It is used to configure camunda BPM platform in the following distributions:

*   [Apache Tomcat](ref:/guides/installation-guide/tomcat/#bpm-platform)
*   [Glassfish Application Server](ref:/guides/installation-guide/glassfish/#bpm-platform)
*   [IBM Websphere Application Server](ref:/guides/installation-guide/was/#bpm-platform)

<div class="alert alert-warning">
  <p>
    <strong>JBoss Application Server 7</strong>
  </p>
  <p>The <code>bpm-platform.xml</code> file is not used in the camunda BPM distribution for JBoss Application Server 7. There, the configuration is added to the central application server configuration file (<code>standalone.xml</code> or <code>domain.xml</code>). The XML schema is the same (i.e. the same elements and properties can be used). See the <a href="ref:/guides/user-guide/#runtime-container-integration-the-camunda-jboss-as-7-subsystem">section on the camunda BPM subsystem</a> for details.
  </p>
</div>


## Xml Schema Namespace

The namespace for the `bpm-platform.xml` file is `http://www.camunda.org/schema/1.0/BpmPlatform`. The XSD file can be found in the `camunda-engine.jar` file.


## Example

```xml
<?xml version="1.0" encoding="UTF-8"?>
<bpm-platform xmlns="http://www.camunda.org/schema/1.0/BpmPlatform"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://www.camunda.org/schema/1.0/BpmPlatform http://www.camunda.org/schema/1.0/BpmPlatform ">

  <job-executor>
    <job-acquisition name="default" />
  </job-executor>

  <process-engine name="default">
    <job-acquisition>default</job-acquisition>
    <configuration>org.camunda.bpm.engine.impl.cfg.JtaProcessEngineConfiguration</configuration>
    <datasource>jdbc/ProcessEngine</datasource>

    <properties>
      <property name="history">full</property>
      <property name="databaseSchemaUpdate">true</property>
      <property name="transactionManagerJndiName">java:appserver/TransactionManager</property>
      <property name="authorizationEnabled">true</property>
    </properties>

  </process-engine>

</bpm-platform>
```

## Syntax Reference

<table class="table table-striped">
  <tr>
    <th>Tag name </th>
    <th>Parent tag name</th>
    <th>Required?</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>&lt;bpm-platform&gt;</code></td>
    <td>None.</td>
    <td>true</td>
    <td>Root element of the bpm-platform.xml file.</td>
  </tr>
  <tr>
    <td><code>&lt;job-executor&gt;</code></td>
    <td><code>&lt;bpm-platform&gt;</code></td>
    <td>true</td>
    <td>See <a href="ref:#tags-job-executor-configuration">job-executor Reference</a></td>
  </tr>
  <tr>
    <td><code>&lt;process-engine&gt;</code></td>
    <td><code>&lt;bpm-platform&gt;</code></td>
    <td>false</td>
    <td>See <a href="ref:#tags-process-engine-configuration">process-engine Reference</a></td>
  </tr>
</table>