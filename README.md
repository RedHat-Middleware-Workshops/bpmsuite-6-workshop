# Red Red JBoss Business Process Management Suite 6 Workshop

This workshop uses a Virtual Machine built using the following tools:
 * [Vagrant](https://www.vagrantup.com/)
 * [VirtualBox](https://www.virtualbox.org/)

The final VM conatains everything you need to execute all the Labs described in [docs](docs/). 

## Vagrant Box (VM) Setup

1. Clone or [download](https://github.com/rafaeltuelho/bpmsuite-6-workshop/archive/master.zip) this repo locally

2. From the [Red Hat Customer Portal](https://access.redhat.com/) download the following packages:
   > you need an active Red Hat Subscription!
   
   * [JBoss EAP 6.4 \(zip distribution\)] (https://access.redhat.com/jbossnetwork/restricted/softwareDownload.html?softwareId=37393)
     * [6.4.x latest patches](https://access.redhat.com/jbossnetwork/restricted/listSoftware.html?product=appplatform&downloadType=patches&version=6.4)
        > for the latest 6.4 patch ([Update 21 at this time](https://access.redhat.com/jbossnetwork/restricted/softwareDownload.html?softwareId=61821)) you also need the following patches: [Update 9](https://access.redhat.com/jbossnetwork/restricted/softwareDownload.html?softwareId=45371) and [Update 19](https://access.redhat.com/jbossnetwork/restricted/softwareDownload.html?softwareId=56031)
   * [JBoss BPMS 6.4 Deployable for EAP 6.4](https://access.redhat.com/jbossnetwork/restricted/softwareDownload.html?softwareId=48451)
     * [latest patch](https://access.redhat.com/jbossnetwork/restricted/listSoftware.html?product=rhpam&downloadType=patches&version=6.4)

3. Copy the JBoss EAP, BPMS and its respective patches inside the `vagrant` sub-directory. See the dir structure in my machine:
   
```
> ~/workshops/BPMS/bpmsuite-6-workshop
.
├── README.md
├── docs
│   ├── images
...
└── vagrant
    ├── Vagrantfile
    ├── bpms-workshop-playbook.yml
    ├── jboss-bpmsuite-6.4.0.GA-deployable-eap6.x.zip
    ├── jboss-bpmsuite-6.4.11-patch.zip
    ├── jboss-eap-6.4.0.zip
    ├── jboss-eap-6.4.19-patch.zip
    ├── jboss-eap-6.4.21-patch.zip
    ├── jboss-eap-6.4.9-patch.zip
    └── roles
```

4. Change the the following ansible files if you need to change the name of some package file.
   
 * [vagrant/roles/eap/vars/main.yml](vagrant/roles/eap/vars/main.yml)

```yaml
eap_artifact_name: jboss-eap-6.4.0.zip
eap_patch_artifact_names:
  - jboss-eap-6.4.9-patch.zip
  - jboss-eap-6.4.19-patch.zip
  - jboss-eap-6.4.21-patch.zip
```

 * [vagrant/roles/bpms-base/vars/main.yml](vagrant/roles/bpms-base/vars/main.yml)

```yaml
bpms_artifact_name: jboss-bpmsuite-6.4.0.GA-deployable-eap6.x.zip
bpms_patch_artifact_name: jboss-bpmsuite-6.4.11-patch.zip   
```

1. Inside the  `vagrant` sub-directory run
```
vagrant up --provision
```

After a while you can access the **Business Central** Portal through http://localhost:8080/business-central

**Start following the [labs](docs/lab_use-case.adoc)!**