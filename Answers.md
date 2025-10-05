# Answers to Part 3

Add your answers to the questions in Part 3, Step 2 below. 

## Vulernability Remediation:
### Vulnerability 1: 
1. Which package or library are you addressing?
  Pillow 9.4.0
2. Which CVE is linked to this vulnerability?
  CVE-2023-50447. This flaw resides in the PIL.ImageMath.eval function and enables arbitrary code execution by manipulating the environment parameter. If images that are names sensitive names with no extensions i.e. system, load_module when the application tries to access the files it passes these calls to the environment. Lack of file type requirements (.jpg, .png) allow this exploit to exist. 
3. What remediation steps do you suggest?
  There are a few remediations suggested like running in a locked dowen sandbox or incorporating apparmor. It appears that this was a bug for a long time before it was resolved via patching/upgrading. According to ubuntu's security info this was resolved in versions 25.04, 24.04, 22.04, and 20.04. The latest with upgrading to Pillow version 10.2.0-1 and version 9.0.1-1ubuntu0.2 for ubuntu 22.04 LTS and version 7.0.0-4ubuntu0.8 for ubuntu 20.04. This can introduce other problems when patching up to a current release but if patching is part of your DevOps plan that the problems introduced will be should be a managable problem to solve. 
### Vulnerability 2:
1. Which vulnerability are you addressing?
  PyYaml 5.1
2. Which CVE is linked to this vulnerability?
  CVE-2019-20477. The issue iss that pyyaml has insufficient restrictions on the load and load_all functions because of a class deserialization issue. This stems from CVE-2017-18342 where the yaml.load() API could execute arbitrary code if used with untrusted data. 
3. What remediation steps do you suggest? 
  According to the CVE versions 5.1 - 5.1.2 are affected by this issue that stems from an incomplete from from an older CVE. Version 5.2 and newer are available if the package is still needed. Ubuntu's security team says that their versions 20.04, 18.04, 16.04, and 14.04 are not affected by this. So make sure that you are patched to the most update to date patch set if running anything dependant on those versions of Ubuntu. However Red Hat offered the tip of using yaml.safe_load when parsing untrusted input. They also mentions that the version pyyaml shipped with Red Hat Enterprise Linux 7 and 8 didn't include the class FullLoader which contains the vulnerability but the versions in their openstack are vulnerable. 
