# sphinxsearch

[![Build Status](https://drone.osshelp.ru/api/badges/ansible/sphinxsearch/status.svg)](https://drone.osshelp.ru/ansible/sphinxsearch)

Ansible role, which installs sphinxsearch and manages it configuration.

## Usage (example)

```yaml
    - role: sphinxsearch
      spinxsearch_initial_setup: true
      searchd_params:
        - name: 'source src1'
          type: mysql
          sql_host: localhost
          sql_user: root
          sql_pass: your_root_mysql_password
          sql_db: test
          sql_port: 3306
          sql_query: 'SELECT id, group_id, UNIX_TIMESTAMP(date_added) AS date_added, title, content FROM documents'
          sql_attr_uint: group_id
          sql_attr_timestamp: date_added
        - name: 'index test1'
          source: src1
          path: /var/lib/sphinxsearch/data/test1
          docinfo: extern
        - name: searchd
          listen: '9306:mysql41'
          log: '/var/log/sphinxsearch/searchd.log'
          pid_file: '/var/run/sphinxsearch/searchd.pid'
          seamless_rotate: 1
          preopen_indexes: 1
          unlink_old: 1
          max_children: 10
        - name: indexer
          mem_limit: 32M
```

## Available parameters

### Main

Short description here.

| Param | Default | Description |
| -------- | -------- | -------- |
| `sphinxsearch_setup` | `full` | Setup mode. See [OSSHelp KB article](https://oss.help/kb4895) |
| `spinxsearch_initial_setup` | `false` | Option for copy initial-setup script |
| `sphinx_configure` | `true` | Parameter for generating sphinxearch configuration file |
| `install_from_ppa` | `false` | Install sphinxsearch from ppa if true |

## FAQ

...

## Useful links

- [Official documentation](http://sphinxsearch.com/docs/)
- [Our article](https://oss.help/kb5226)

## TODO

- ...

## License

GPL3

## Author

OSSHelp Team, see <https://oss.help>
