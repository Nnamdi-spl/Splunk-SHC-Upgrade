<h1>Splunk Search Head Cluster Upgrade</h1>


<h2>Description</h2>
This project is a walk-through for a Splunk Search Head Cluster Rolling upgrade from Splunk Enterprise version 8.2.4 to Splunk Enterprise version 9.0.2.A rolling upgrade performs a phased upgrade of cluster members with minimal interruption to your ongoing searches. A rolling upgrade  is primarily preferred for distributed clustered deployments where minimal search disruption is needed when upgrading cluster members to a new version of Splunk Enterprise.Cluster members are upgraded one at a time.Rolling upgrade only applies to upgrades from version 7.1.x to higher versions of Splunk Enterprise.During a rolling upgrad,clustering maintenance operations, such as rolling restart, bundle pushes, or node additions should not be performed.

<br />


<h2>Lab Environment Setup</h2>

- <b>11 t2micro EC2 Intances running in AWS</b> 
- <b>Windows 10 work station (21H2)</b>
- <b>MobaXterm SSH Client</b>
- <b>Bash</b>

<h2>Splunk Clustered Deployment Instances</h2>

- <b>Indexer1 - IDX1</b> 
- <b>Indexer2 - IDX2</b>
- <b>Indexer3 - IDX3</b>
- <b>Cluster Master - CM</b>
- <b>Search Head - SH1</b>
- <b>Search Head - SH2</b>
- <b>Search Head - SH3</b>
- <b>Universal Forwarder - UF1</b>
- <b>Universal Forwarder - UF2</b>
- <b>Universal Forwarder - UF3</b>
- <b>Deployment Server - DS</b>

<h2>Program walk-through:</h2>



<br />
Install and configure 11 Splunk  instances running in AWS with labels:  <br/>
<img src="https://user-images.githubusercontent.com/112047285/205214716-5ded9750-c344-486f-9a9f-a053953d134f.png" height="80%" width="80%"/>
<br />
<br />
Run preliminary health checks on any Search Head Cluster member to establish a baseline of performance before the upgrade so you can tell 
if the system is performing within expected ranges after the upgrade.Run the CLI command on $SPLUNK_HOME ./splunk show shcluster-status --verbose.
Verify the Splunk version from the output: <br/>
<img src="https://user-images.githubusercontent.com/112047285/205215933-20f8310f-f6de-4889-bcd4-648cd036ccb9.png" height="80%" width="80%"/>
<br />
<br />
Initialize rolling upgrade on any Search Head Cluster Member:  <br/>
<img src="https://user-images.githubusercontent.com/112047285/205216725-9a90fd43-1e44-4105-88fe-cb5cf68fbdc7.png" height="80%" width="80%"/>
<br />
<br />
Select a Search Head Cluster member other than the Captain and put that member into manual detention mode:  <br/>
<img src="https://user-images.githubusercontent.com/112047285/205217013-a2951a1c-e7b6-45db-8618-6ae49110509c.png" height="80%" width="80%"/>
                                                             
<br />
<br />
Confirm the member is ready for upgrade.
Run the following command to confirm that all historical and ad-hoc searches are complete:  <br/>
<img src="https://user-images.githubusercontent.com/112047285/205217607-301fdaea-122e-4484-a502-c71654f5f4d0.png" height="80%" width="80%"/>
<br />
<br />

Upgrade the Search Head Cluster Member:  <br/>
<img src="https://user-images.githubusercontent.com/112047285/205218492-06b8f09e-c21f-4b49-83e0-5e090482d829.png" height="80%" width="80%"/>
<br />
<br />

Review migration options:  <br/>
<img src="https://user-images.githubusercontent.com/112047285/205218917-2059f872-fd6a-4d14-99dd-4d72dcf1b302.png" height="80%" width="80%"/>
<br />
<br />
Verify Splunk version upgrade:  <br/>
<img src="https://user-images.githubusercontent.com/112047285/205219458-0de642ac-0230-4300-93f5-a021d4952675.png" height="80%" width="80%"/>
<br />
<br />
Verify all  Seach Head Cluster members are up and running on the GUI:  <br/>
<img src="https://user-images.githubusercontent.com/112047285/205220093-28923050-3b83-4554-80ff-90c051e7f70e.png" height="80%" width="80%"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
