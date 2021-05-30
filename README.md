# f5-drasi

actions (english) => drasi (greek)

## idea

Since 2019 github actions have become super powerful with options like simple bash scripting, nodejs apps, and even full blown docker containers.

Some of these docker containers can get pretty beefy some full CI/CD solutions include full application testing and deployment.

Infrastucture as Code (IaC) is a very common goal for F5 customers as we continue to automate and accelerate deployments.

Several have started some simple solutions to integrate SCM directly with managing f5 configurations.  Some of those solutions have worked very well for some.

It's time to create a solution to push the idea to the next level

## architecture

At it's core, this will be a nodejs application that integrats with github actions.  The action can execute on push/pull-request/merge as needed;

### phase 1 - applications

Phase 1 will include the action to watch a "tenants" folder.  Each file in the folder will be a tenant.  When a tenant has been modified, the action will execute the appropriate AS3 call to the defined F5 device.

This can currently be achieved with f5-conx-core.

### phase 2 - system settings

Phase 2 will include managing system settings (vlans/ips/dns/ntp/snmp/...)

- First thought is to use DO, but DO doesn't handle day 1+ operations, like at all...
- the next thought was to use something like ansible so things can be managed imperatively
- All this information could be based off a DO declaration;
  -  Use DO for day 0 deployment
  -  then use DO declaration, parsed for specific details to run an ansible playbook to update any changes

### phase 3 - device deployment

For now, we will just be focused on F5 VE (cloud/gcp/azure/aws/vmware)

The idea is that new repo could be copied (or created from template) that would include all the necessary details to deploy an f5 ve (or pair), onboard device settins, and deploy applications

Any future changes would be hanlded by previous phase funcationality

## Installation
Outline the requirements and steps to install this project. 

## Usage

import github action, setup actions files and secrets, deploy!

## Development

Figuring this out.  Seems the best way is to use a project called ACT to locally test github actions

## Support
For support, please open a GitHub issue.  Note, the code in this repository is community supported and is not supported by F5 Networks.  For a complete list of supported projects please reference [SUPPORT.md](SUPPORT.md).

## Community Code of Conduct
Please refer to the [F5 DevCentral Community Code of Conduct](code_of_conduct.md).


## License
[Apache License 2.0](LICENSE)

## Copyright
Copyright 2014-2020 F5 Networks Inc.


### F5 Networks Contributor License Agreement

Before you start contributing to any project sponsored by F5 Networks, Inc. (F5) on GitHub, you will need to sign a Contributor License Agreement (CLA).

If you are signing as an individual, we recommend that you talk to your employer (if applicable) before signing the CLA since some employment agreements may have restrictions on your contributions to other projects.
Otherwise by submitting a CLA you represent that you are legally entitled to grant the licenses recited therein.

If your employer has rights to intellectual property that you create, such as your contributions, you represent that you have received permission to make contributions on behalf of that employer, that your employer has waived such rights for your contributions, or that your employer has executed a separate CLA with F5.

If you are signing on behalf of a company, you represent that you are legally entitled to grant the license recited therein.
You represent further that each employee of the entity that submits contributions is authorized to submit such contributions on behalf of the entity pursuant to the CLA.
