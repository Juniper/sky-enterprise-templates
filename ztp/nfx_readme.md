# NFX ZTP Template

This template is designed to onboard the jdm and jvm (vjunos) of the NFX. In order for this to work you will need to do the folowing in Sky Enterprise:

## JVM 

Create the jvm as regular device (not ZTP and type switch). Retrieve the contents of the configlet

e.g. lab-nfx1-jvm

Configlet:

``` text
set system services ssh protocol-version v2
set system login user skyenterprise class super-user authentication encrypted-password $1$2passwordhash
set system services outbound-ssh client skyenterprise-ncd01 device-id lab-nfx1-jvm-ztpexample secret hcsecrethash
set system services outbound-ssh client skyenterprise-ncd01 services netconf keep-alive retry 3 timeout 5
set system services outbound-ssh client skyenterprise-ncd01 skyent-ncd01.juniper.net port 4087 timeout 60 retry 1000
set system services outbound-ssh client skyenterprise-ncd02 device-id lab-nfx1-jvm-ztpexample secret hcsecrethash
set system services outbound-ssh client skyenterprise-ncd02 services netconf keep-alive retry 3 timeout 5
set system services outbound-ssh client skyenterprise-ncd02 skyent-ncd02.juniper.net port 4087 timeout 60 retry 1000
```

## JDM 

Create the jdm as an nfx ZTP Device and use the device-id, secret, username and password from the JVM configlet in the variables:

e.g. lab-nfx1-jdm

Variables:

``` yaml
hostname: lab-nfx1
jvm_host_id: lab-nfx1-jvm-ztpexample
jvm_secret: hcsecrethash
jvm_username: skyenterprise
jvm_password: $1$2passwordhash
```

## Results

When the device completes ZTP both jdm and jvm will be online.
