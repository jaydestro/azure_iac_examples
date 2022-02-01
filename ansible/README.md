The Ansible guide will give you an example of creating an Azure Virtual Machine, Network Security Group, and a Virtual Network.  You'll need to add a public ssh key to the `ssh_public_keys:` line within the [ansible/main.yaml](ansible/main.yaml) file.  Preferred method of storing this ssh key is with Azure Key Vault.  Full documentation on this procedure can be reviewed in the Microsoft Docs article [Create a Linux virtual machines in Azure using Ansible.](https://cda.ms/3LB). This VM will by default have the SSH port (22) deny for security purposes in this demo.  We won't actually need to access the VM for this example.

Example from the [main.yml](main.yml) template:

```yaml
  - name: Create Network Security Group that allows SSH
​    azure_rm_securitygroup:
​      resource_group: myResourceGroup
​      name: myNetworkSecurityGroup
​      rules:
​        - name: SSH
​          source_address_prefix: Internet
​          source_port_range: "*"
​          protocol: Tcp
​          destination_port_range: 22
​          access: Deny
​          priority: 1001
​          direction: Inbound
```

[Get Started: Configure Ansible using Azure Cloud Shell](https://cda.ms/3LC) will give you details on configuration methods including setting your subscription context.

You will need to install the python modules into the Cloud Shell for Ansible as a prerequisite.

```bash
curl https://raw.githubusercontent.com/ansible-collections/azure/dev/requirements-azure.txt > requirements-azure.txt`
pip -r requirements-azure.txt`
```

## Deploy

**Clone this repo in Azure Cloud Shell and enter the `ansible` directory**

```bash
git clone git@github.com:jaydestro/azure_iac_examples.git
cd azure_iac_examples/ansible
```

**Create an ssh public key or use your existing one.**

```bash
ssh-keygen -m PEM -t rsa -b 4096
```

Copy the contents of the public key file. By default, the public key file is named `id_rsa.pub`. The value is a long string starting with "ssh-rsa ". You'll need this value in the next step.

Update in `main.yml` on line 59.  Replace the "Insert ssh public key here" section.

**Example**

Before `key_data: "Insert ssh key here"`
After `key_data: "ssh-rsa exampleexampleexample"`

Deploy the template via Cloud Shell:

```bash
ansible-playbook main.yml
```

This will run the playbook and then give you information on success or failure of the deployment:

```
localhost                  : ok=9    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0```
```

## Deleting Azure Resources

Run the playbook using the [ansible-playbook](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html) command. Replace the placeholder with the name of the resource group to be deleted. All resources within the resource group will be deleted.

```bash
ansible-playbook rg_destroy.yml --extra-vars "name=myResourceGroup"
```