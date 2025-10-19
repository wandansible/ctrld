Ansible role: ctrld
===================

Install and configure Control D DNS to DoH proxy which
allows local DNS queries to be proxied to an upstream DoH
server.

Role Variables
--------------

```
ENTRY POINT: *main* - Install and configure Control D DoH proxy

          Install and configure Control D DNS to DoH proxy which
          allows local DNS queries to be proxied to an upstream DoH
          server.

Options (= indicates it is required):

- ctrld_arch_map  Mapping of the possible values of
                   ansible_architecture to the ctrld package
                   architectures
          default:
            aarch64: arm64
            armv6l: armv6
            armv7l: armv7
            i386: 386
            x86_64: amd64
          type: dict

- ctrld_bin_dir  Directory for the ctrld binaries
          default: /opt/ctrld/
          type: str

- ctrld_binary  Name of the ctrld binary
          default: ctrld
          type: str

- ctrld_checksum_type  The ctrld package checksum type
          default: sha256
          type: str

- ctrld_clean_src_dir  Remove old downloaded archive files from ctrld
                        src directory
          default: true
          type: bool

- ctrld_config  Contents of the ctrld.toml configuration file, or
                 empty string to leave file as is
          default: ''
          type: str

- ctrld_config_dir  Configuration directory for ctrld
          default: /etc/controld
          type: str

- ctrld_github_checksum_filename  Filename for the ctrld package
                                   checksums file on github
          default: checksums.txt
          type: str

- ctrld_github_org  Name of organisation for ctrld github repository
          default: Control-D-Inc
          type: str

- ctrld_github_repo  Name of ctrld github repository
          default: ctrld
          type: str

- ctrld_group  Name of the ctrld unix group
          default: ctrld
          type: str

- ctrld_install  If true, install ctrld
          default: true
          type: bool

- ctrld_manage_user  If true, add ctrld unix user and group
          default: true
          type: bool

- ctrld_run_args  List of additional arguments to start ctrld with
          default: []
          elements: str
          type: list

- ctrld_run_dir  Runtime directory for ctrld
          default: /run/ctrld
          type: str

- ctrld_src_dir  Directory for the downloaded ctrld src archive
          default: /opt/ctrld/src
          type: str

- ctrld_src_files  List of files to extract from the source archive
          default: [ctrld]
          elements: str
          type: list

- ctrld_strip_components  Strip NUMBER leading components from file
                           names on extraction
          default: 2
          type: int

- ctrld_user  Name of the ctrld unix user
          default: ctrld
          type: str

- ctrld_version  version to install (use "latest" for the latest
                  version)
          default: latest
          type: str
```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/ctrld,main,wandansible.ctrld

Or, by adding the following to `requirements.yml`:

    - name: wandansible.ctrld
      src: https://github.com/wandansible/ctrld

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: all
      roles:
         - role: wandansible.ctrld
           become: true
