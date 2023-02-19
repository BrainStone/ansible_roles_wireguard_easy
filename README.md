# wireguard_easy

An Ansible role that will install WireGuard Easy (https://github.com/WeeJeWel/wg-easy).

## Requirements

This role requires NodeJS installed if you decide to skip letting the role install it, git and sudo (unless you set `wireguard_easy_user` to `root`.

## Role Variables

| Variable                                 | Description                                                                                                                                                                                                                                                                                                                                        |
|------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `wireguard_easy_base_path`               | The base path of the wg-easy installation.<br/><br/>Default: `/opt/wg-easy`                                                                                                                                                                                                                                                                        |
| `wireguard_easy_bin_path`                | The git path of the binaries of the wg-easy installation. Should be inside `wireguard_easy_base_path`.<br/><br/>Default: <br/>`{{ wireguard_easy_base_path }}/bin`                                                                                                                                                                                 |
| `wireguard_easy_config_path`             | The config path for WireGuard.<br/><br/>Default: `/etc/wireguard`                                                                                                                                                                                                                                                                                  |
| `wireguard_easy_nodejs_version`          | The NodeJS version to use. Typically shouldn't need to be changed.<br/><br/>Default: `14.x`                                                                                                                                                                                                                                                        |
| `wireguard_easy_password`                | Password for the webinterface. If empty, everyone can access the interface.<br/><br/>Default: *Empty*                                                                                                                                                                                                                                              |
| `wireguard_easy_port`                    | The webserver's port.<br/><br/>Default: `51821`                                                                                                                                                                                                                                                                                                    |
| `wireguard_easy_repo_path`               | The git repository path of the wg-easy installation. Should be inside `wireguard_easy_base_path`.<br/><br/>Default: <br/>`{{ wireguard_easy_base_path }}/repo`                                                                                                                                                                                     |
| `wireguard_easy_skip_nodejs`             | If set to true skip installing NodeJS (which means you should install it yourself).<br/><br/>Default: `false`                                                                                                                                                                                                                                      |
| `wireguard_easy_user`                    | Which user to own the files and run the service as. Will setup passwordless sudo for the user.<br/>Set to `root` to not use sudo<br/><br/>Default: `wireguard`                                                                                                                                                                                     |
| `wireguard_easy_wg_default_address`      | The subnet used for WireGuard. The host will be the first usable IP in that range.<br/><br/>Default: `10.8.0.0/24`                                                                                                                                                                                                                                 |
| `wireguard_easy_wg_default_dns`          | Which DNS servers should the clients use by default. Leave empty for none.<br/><br/>Default: The IP of the host in the WireGuard subnet (if the subnet is 10.8.0.0/24, it'll be 10.8.0.1)                                                                                                                                                          |
| `wireguard_easy_wg_host`                 | The ideally publicly reachable host name of the WireGuard installation.<br/><br/>Default: the inventory host name                                                                                                                                                                                                                                  |
| `wireguard_easy_wg_port`                 | The WireGuard port.<br/><br/>Default: `51820`                                                                                                                                                                                                                                                                                                      |
| `wireguard_easy_wg_mtu`                  | The MTU for the WireGuard connection.<br/><br/>Default: *unset*                                                                                                                                                                                                                                                                                    |
| `wireguard_easy_wg_persistent_keepalive` | The time interval in seconds to send keepalive packets from the client. This isn't enforce but suggested to the client.<br/><br/>Default: `0` (disabled)                                                                                                                                                                                           |
| `wireguard_easy_wg_allowed_ips`          | Suggest the client which `AllowedIPs` to use. This controls which addresses should be routed through the tunnel. (May be an array)<br/><br/>Default: `0.0.0.0/0, ::/0`                                                                                                                                                                             |
| `wireguard_easy_enforce_wg_allowed_ips`  | By default the client can change their `AllowedIPs` setting. Enabling this will enforce this server side, limiting the clients to whatever is set in `wireguard_easy_wg_allowed_ips`.<br/>Note; they can still change their own `AllowedIPs` setting, but any addresses outside the server side setting will be dropped.<br/><br/>Default: `false` |

## Dependencies

The software needs NodeJS install, which will be done via the role [geerlingguy.nodejs](https://galaxy.ansible.com/geerlingguy/nodejs). You can set the
option `wireguard_easy_skip_nodejs` to true.

## Example Playbook

I personally recommend using `host_vars` or `group_vars`, but a simple copy pastable block looks like this (the keys and passwords aren't real btw):

```yaml
- hosts: servers
  roles:
    - role: brainstone.wireguard_easy
      vars:
        wireguard_easy_skip_nodejs: false
```

## License

This Ansible role is licensed under the [MIT License](./LICENSE).

## Contact

To contact me, use GitHub issues or Discord (BrainStone#6759)

## Random Quote

> Remember that code is really the language in which we ultimately express the requirements. We may create languages that are closer to the requirements. We
> may create tools that help us parse and assemble those requirements into formal structures. But we will never eliminate necessary precision—so there will
> always be code.
>
> — <cite>Robert C. Martin</cite>
