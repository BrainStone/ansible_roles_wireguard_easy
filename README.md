# wireguard_easy

An Ansible role that will install WireGuard Easy (https://github.com/WeeJeWel/wg-easy).

## Requirements

This role requires NodeJS installed if you decide to skip letting the role install it and git.

## Role Variables

| Variable                        | Description                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| `wiregaurd_easy_nodejs_version` | The NodeJS version to use. Typically shouldn't need to be changed.<br/><br/>Default: `14.x`                   |
| `wiregaurd_easy_skip_nodejs`    | If set to true skip installing NodeJS (which means you should install it yourself).<br/><br/>Default: `false` |

## Dependencies

The software needs NodeJS install, which will be done via the role [geerlingguy.nodejs](https://galaxy.ansible.com/geerlingguy/nodejs). You can set the 
option `wiregaurd_easy_skip_nodejs` to true.

## Example Playbook

I personally recommend using `host_vars` or `group_vars`, but a simple copy pastable block looks like this (the keys and passwords aren't real btw):

```yaml
- hosts: servers
  roles:
    - role: brainstone.wireguard_easy
      vars:
        wiregaurd_easy_skip_nodejs: false
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
