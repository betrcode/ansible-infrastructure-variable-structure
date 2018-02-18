Ansible Infrastructure Variables Structure
==========================================

The purpose of this Ansible playbook example is to demonstrate how you can structure variables a Ansible playbook which works 
with cloud modules. It is not specific to cloud modules, but really well suited for any playbook which does work which 
is not on *hosts*.

In "normal" Ansible playbook, you can use host groups and often use `host_vars` and `group_vars` to set different values
for variables for hosts in different groups. Host groups are often *staging* and *production* but can also be different
regions such as *EU*, *US*, *Asia*.

When you provision infrastructure (and not hosts), it is not as clear how to structure your variables. This playbook
intends to give you a good example.

Secrets handling is another problem, and in this playbook we show you how to use `git-crypt` to encrypt specific 
sensitive files and use some clever Ansible magic to load the secrets automatically.

Read the full blog post at: [https://blog.crisp.se/2018/02/18/maxwenzin/how-to-structure-ansible-variables-when-provisioning-infrastructure](https://blog.crisp.se/2018/02/18/maxwenzin/how-to-structure-ansible-variables-when-provisioning-infrastructure)

## How to run
Before you can run the demonstration playbook, you will need to decrypt the repository using `git-crypt unlock ./demo-git-crypt-key`.
In this demo, the key is published in the repository for demo purposes. You should of course never do this with any real project.

Unlock the encrypted files by: `git-crypt unlock ./demo-git-crypt-key`

Then run the playbook with:

`ansible-playbook -i environments/${ENVIRONMENT} deploy.yml`
where *${ENVIRONMENT}* is `germany` or `greatbritain`.

### Example output

## Troubleshooting
```
ERROR! 'utf8' codec can't decode byte 0xa9 in position 14: invalid start byte
```
You have probably not decrypted the repository secrets. Do it by running: `git-crypt unlock ./demo-git-crypt-key`
