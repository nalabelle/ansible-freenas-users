ansible-freenas-users
=========

Sets up users and groups in [FreeNAS](http://www.freenas.org/)

Requirements
------------

a FreeNAS server.

Role Variables
--------------

Variables along with defaults:

    # Sets the hostname for the server. Localhost is fine if you're running it on the server directly.
    # You can also delegate to local and it'll work if you specify the actual host here.
    freenas_hostname: "localhost"
    # Customize the urls to the API if needed, should be okay as is.
    freenas_group_url: "http://{{ freenas_hostname }}/api/v1.0/account/groups/?format=json"
    freenas_user_url: "http://{{ freenas_hostname }}/api/v1.0/account/users/?format=json"
    # List of users
    freenas_user_list: []
    # List of groups
    freenas_group_list: []

To specify users and groups:

    freenas_user_list:
      - name: myusername
        password: hunter2
        uid: 900
        group: myusers
        email: "myusername@example.com"
    freenas_group_list:
      - name: myusers
        gid: 9000

Dependencies
------------

None, uses the uri built in.

Example Playbook
----------------

Note: if you run this on the FreeNas server instead of using `connection: local`, you'll likely need to set `ansible_python_interpreter: /usr/local/bin/python` for the host

    ---
    - hosts: servers
      roles:
        - ansible-freenas-users

License
-------

MIT

Author Information
------------------

https://github.com/nalabelle
