linux_base
========

Update apt and upgrade all packages.  Also, installs the following packages:

* git
* ntp
* unattended-upgrades
* build-essential
* libreadline6
* libreadline6-dev
* curl
* zlib1g
* zlib1g-dev
* libssl-dev
* libyaml-dev
* libsqlite3-dev
* sqlite3
* libxml2-dev
* libxslt1-dev
* autoconf
* libc6-dev
* libncurses5-dev
* automake
* libtool
* bison
* pkg-config

This role is used as the foundation to Ruby and Node web apps.

```
- name: Base | Update apt
  apt: update_cache=yes
  sudo: yes

- name: Base | Ensure build-essential is installed
  apt: pkg={{ item }} state=latest
  sudo: yes
  with_items:
    - git
    - ntp
    - unattended-upgrades
    - build-essential
    - libreadline6
    - libreadline6-dev
    - curl
    - zlib1g
    - zlib1g-dev
    - libssl-dev
    - libyaml-dev
    - libsqlite3-dev
    - sqlite3
    - libxml2-dev
    - libxslt1-dev
    - autoconf
    - libc6-dev
    - libncurses5-dev
    - automake
    - libtool
    - bison
    - pkg-config

- name: Base | Upgrade apt
  apt: upgrade=safe
  sudo: yes

- name: Base | Setup Time Zone
  template: src=timezone.j2 dest=/etc/timezone
  sudo: yes

- name: Base | Take owenership of /srv
  shell: chown deploy:deploy /srv
  sudo: yes

- name: Base | Take owenership of /tmp
  shell: sudo chown deploy:deploy /tmp
  sudo: yes
```

Requirements
-----------
Operating system developed for: Linux (Ubuntu 12.04LTS)

Role Variables
-----------
No Variables for this playbook

Dependencies
-----------
None

License
-----------
GPL v3