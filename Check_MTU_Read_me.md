# vpc_network


### Sentinel file "google_check_mtu.sentinel" is having code to deploy the policies. In order to check the value of MTU is 1500 , We need to validate  policy successfully.**

* the purpose of this policy is to validate the value of the MTU.

#### Variables :
* messages: It is being used to hold the complete message of policies violation to show to the user.

#### Method :

* allResources: This is the function, being used to get the all resourses regarding to "vpc-network".

* control statements: here we are looping and assigning the all the resourses into two parameters 
    * Parameters
      |Name|Description|
      |----|-----|
      |address|The key inside of resource_changes section for particular GCP Resource in tfplan mock|
      |rc|The value of address key inside of resource_changes section for particular GCP Resource in tfplan mock|

* condition: if condition is comparing the value of mtu is not 1500 it will generate appropriate message to show the users.


**Terraform version**
Terraform v1.0.7

**sentinel versions**
Sentinel v0.18.4



#### modules to import:
* import "tfplan-functions"
* import "strings"
* import "types"

#### Testing a Policy
     sentinel test <sentinel file>
example :
$ sentinel test google_check_mtu.sentinel

  PASS - google_check_mtu.sentinel

  PASS - test/google_check_mtu/fail.hcl

  PASS - test/google_check_mtu/null.hcl
  
  PASS - test/google_check_mtu/success.hcl


