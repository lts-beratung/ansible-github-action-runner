# Ansible Role GitHub Action Runner (self-hosted)

Ansible Role to install and configure a self-hosted GitHub Actions Runner on a machine. Use this role to install, configure and even uninstall GitHub Action self-hosted runner aka build runners.

Have a look at the official [GitHub Action self-hosted Runner documentation](https://docs.github.com/en/actions/reference/software-installed-on-github-hosted-runners) to figure out how things work.

## GitHub Action Build Status

![Molecule Test](https://github.com/lts-beratung/ansible-github-action-runner/workflows/Molecule%20Test/badge.svg)

## Role Variables

Please have a look at the comments and variables in the default files on how to configure this role.

Use the `runner_action` to determine what which action to perform. You can either set it to `install` (install Github Runner on machine but do not configure), `configure` (configure Guthub Runner) and `remove` to delete configured Github Runner. Any combination like `install,configure` is possible.

Have a look at all the variables at [defaults/main.yml](defaults/main.yml)

## Example Playbook

You may use the example playbook to test the waters:

[playbook.yml](playbook.yml)

To install a GitHub Runner, set the variables in `playbook.yml` to suit your GubHub Configuration.

You can find the `runner_config_token` value in your Github Organisation or Github Repository, depending on which level you want to register the Runner. Go to `Settings | Actions` and click on `Add Runner` to get the `runner_config_token` value.

Once configured, run

```
ansible-playbook  --connection=local --inventory 127.0.0.1, playbook.yml
```

If you want to remove a runner and its workspace again, set the `runner_config_token` variable to the removal token provided by Github and run with the `runner_action` set to `"uninstall"` (either as command line parameter or in your Ansible Playbook).

```
ansible-playbook  --connection=local --extra-vars="runner_action=remove" --inventory 127.0.0.1, playbook.yml
```

## License

MIT

## Author Information

Martin Albiez @ LTS Beratung GmbH

- [http://www.lts-beratung.de](http://www.lts-beratung.de)