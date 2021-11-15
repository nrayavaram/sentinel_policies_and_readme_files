# Secret_Manager_policies


### Sentinel file "google_secret_manager_secret.sentinel" is having code to deploy the policies. In order to check the location is US or other than US, We need to validate  policy successfully.**

* the purpose of this policy is to validate the value of the location.

#### Variables :

* prefix: It is being used locally to have information of valid location.
* messages: It is being used to hold the complete message of policies violation to show to the user.

#### methods :

* allResources: This is the function, being used to get the all resourses regarding to "Secret manager".


* is_valid_location: This function is being used to validate the value of parameter "Location". As per the policy, its value needs to be prefix with "US-". It can not be empty/null. If the policy won't be validated successfully, it will generate appropriate message to show the users. This function will have below 2-parameters:

Parameters
* location => The key inside of resource_changes section for particular GCP Resource in tfplan mock
* valid_location_prefix => The value of location key inside of resource_changes section for particular GCP Resource in tfplan mock

#### control statements: 
* here we are iterating and assigning the all the resourses into two parameters 
    * Parameters
      |Name|Description|
      |----|-----|
      |address|The key inside of resource_changes section for particular GCP Resource in tfplan mock|
      |rc|The value of address key inside of resource_changes section for particular GCP Resource in tfplan mock|

#### condition:
* if condition is comparing the value of location with prefix variable. if both are equal the policy will be true else it will generate appropriate message to show the users.


#### Terraform version
* Terraform v1.0.7

#### sentinel versions
* Sentinel v0.18.4



modules to import:
------------------
* import "tfplan-functions"
* import "strings"
* import "types"


#### Testing a Policy
     sentinel test <sentinel file>

example :
$  sentinel test google_secret_manager_secret.sentinel

  PASS - google_secret_manager_secret.sentinel

  PASS - test/google_secret_manager_secret/fail.hcl

  PASS - test/google_secret_manager_secret/null.hcl
  
  PASS - test/google_secret_manager_secret/pass.hcl







