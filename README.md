# wireguard_easy

An Ansible role that will install WireGuard Easy (https://github.com/WeeJeWel/wg-easy).

## Requirements

TODO

## Role Variables

TODO

## Dependencies

Only Ansible Builitins.

## Example Playbook

I personally recommend using `host_vars` or `group_vars`, but a simple copy pastable block looks like this (the keys and passwords aren't real btw):

```yaml
- hosts: servers
  roles:
    - role: brainstone.wireguard_easy
      vars:
        foo: bar
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
