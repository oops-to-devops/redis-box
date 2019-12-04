redis_box
=========

Underlying ansible roles: `sa-redis`.  Check roles documentation for whole set of parameters to override.

Supported tags:

`sa_redis`

Supported parameters overrides:


```
```


Using with vagrant boilerplate (https://github.com/Voronenko/devops-vagrant-ansible-boilerplate)

```

    config.vm.provision "redis-box", type: "ansible" do |ansible|
        ansible.playbook = "deployment/provisioners/redis_box/playbook.yml"
        ansible.galaxy_role_file = "deployment/provisioners/redis_box/requirements.yml"
        ansible.galaxy_roles_path = "deployment/provisioners/redis_box/roles"
        ansible.verbose = true
        ansible.groups = {
            "redis_box" => [vconfig['vagrant_machine_name']]
        }
        # ansible.tags = ["sa_redis"]
        ansible.extra_vars = {
            box_provider: "vagrant",
            env: "vagrant"
        }
    end


```
