git_deploy_domain_sales_template
=========

Ansible role to deploy a basic HTML templated site for selling a domain. I purchased a license for this site template so it does not fall under the open source license of this Ansible role. If you want to use the template in this license then you'll need to purchase a license from the provider that sells it.

Requirements
------------

You'll want to already have some sort of webserver setup (Apache, NginX, etc.).

Role Variables
--------------

Domain display name
```
	git_deploy_domain_sales_template_domain_display_name: "MyDomain.com"
```

Email address to receive offers:
```
	git_deploy_domain_sales_template_email_address_to_receive_offers: "myemail@mydomain.com"
```

Buy now amount:
```
	git_deploy_domain_sales_template_buy_now_amount: "$2500"
```

List of sites to setup Git deployments for. Not needed unless the "git_deploy_domain_sales_template_use_list" variable is set to true. Default is true.
```
	git_deploy_domain_sales_template_sites_to_setup:
	  - {
		  name: "somesite"
		  template_type: 'domain-sales'
		  display_name: "SomeSite.com",
		  buy_now_amount: "$2500"
		}
```



(Default) Background image:
```
	git_deploy_domain_sales_template_background_image: "16.jpg"
```

(Default) Year for copyright image:
```
	git_deploy_domain_sales_template_copyright_year: "2018"
```

(Default) Call to action heading #5
```
	git_deploy_domain_sales_template_call_to_action: "Interested in buying this domain name? Make an offer."
```

(Default) Site Title
```
	git_deploy_domain_sales_template_site_title: "{{ item.display_name | default(git_deploy_domain_sales_template_domain_display_name) }} For Sale"
```

(Default) Will you be passing a list of domains to deploy templates to?
```
	git_deploy_domain_sales_template_use_list: true
```

(Default) The default git repo to use when downloading and installing the application / template
```
	git_deploy_domain_sales_template_git_repo: "https://github.com/stancel/domain-sales-template.git"
```

(Default) If you are using your own forked repo an want to use a branch instead of a tagged release then fill in a value and comment out the "tagged_release_version" variable 
```
	git_deploy_domain_sales_template_git_branch: "master"
```

(Default) Choose the git tagged release that you would like to download and install. Comment this out if using a git branch instead.
```
	git_deploy_domain_sales_template_tagged_release_version: ""
```

(Default) The Document Root or file path where the files will be stored and served up by your webserver. The default path is "/var/www/html" and assumes you are running Apache2 on Debian or Ubuntu
```
	git_deploy_domain_sales_template_web_files_path: "/var/www"
	git_deploy_domain_sales_template_web_directory_for_application: "/html"
```

(Default) The linux username used by your webserver. The default value is "www-data" which assumes Apache is used on a Debian or Ubuntu linux
```
	git_deploy_domain_sales_template_web_user: "www-data"
```

(Default) The linux group used by your webserver. The default value is "www-data" which assumes Apache is used on a Debian or Ubuntu linux
```
	git_deploy_domain_sales_template_web_group: "www-data"
```

(Default) Is this a "new", "upgrade" or "restore" installation? "new" and "upgrade" installs install files from Git, "restore" skips any git deployments and expect a later role to restore files to the needed directory.
```
	git_deploy_domain_sales_template_installation_type: "new"
```

(Default) Is this instance to be used for a "dev", "qa" or "prod" environment? Only "prod" environments will deploy any needed cron jobs or schedulers.
```
	git_deploy_domain_sales_template_environment_type: "prod"
```

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

	- hosts: your_server
	  vars_files:
	    - vars/main.yml
	  roles:
	    - stancel.git_deploy_domain_sales_template 

or just pass the variables in the playbook

	- hosts: your_server 
	  vars:
		git_deploy_domain_sales_template_domain_display_name: "MyDomain.com"
		git_deploy_domain_sales_template_email_address_to_receive_offers: "myemail@mydomain.com"
		git_deploy_domain_sales_template_buy_now_amount: "$2500"
	  roles:
	    - stancel.git_deploy_domain_sales_template


License
-------

GPLv3

Author Information
------------------

[Brad Stancel](https://github.com/stancel) 


