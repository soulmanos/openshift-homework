https://docs.openshift.com/container-platform/3.9/admin_guide/manage_users.html#managing-users-adding-a-user
https://docs.openshift.com/container-platform/3.9/install_config/configuring_authentication.html#identity-providers_parameters

# Update htpasswd file

1. Create a new htpasswordfile and add user admin with password to it
    * `htpasswd -bc newpasswordfile admin R3dh47!`
2. Re-write the password file that was assigned at startup with ansible and restart services (all masters)
    1. `ansible masters -m copy -a "src=newpasswordfile dest=/etc/origin/master/htpasswd"`
3. Check file updated
    1. `ansible masters -m shell -a "cat /etc/origin/master/htpasswd"`
4. From system:admin (oc whoami) - Add new user (admin) to cluster-admin role
    1. `oadm policy add-cluster-role-to-user cluster-admin admin`
5. Login to WebConsole
    1. https://loadbalancer1.$GUID.example.opentlc.com

Optionally Restart services:
`ansible masters -m shell -a "systemctl restart atomic-openshift-master-api atomic-openshift-master-controllers"`

* Query current Authentication providers:
`ansible masters -m shell -a "cat /etc/origin/master/master-config.yaml | grep -A8 identityProviders"`

* Pull back system:admin config from master[0]
`ansible masters[0] -b -m fetch -a "src=/root/.kube/config dest=/root/.kube/config flat=yes"`
