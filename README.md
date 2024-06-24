# setup-digitalocean-firewall

__This action is a fork of [earthpyy/setup-digitalocean-firewall](https://github.com/earthpyy/setup-digitalocean-firewall)__

![GitHub](https://img.shields.io/github/license/ruby-logic/setup-digitalocean-firewall)
![GitHub Build Status](https://img.shields.io/github/actions/workflow/status/ruby-logic/setup-digitalocean-firewall/build.yml)
![Node Version](https://img.shields.io/badge/node-20-blue)

GitHub Action to temporary add GitHub shared runner IP into DigitalOcean's firewall rule

## Examples

### Basic Usage

```yml
- name: Setup DigitalOcean Firewall (uses ifconfig.co)
  uses: ruby-logic/setup-digitalocean-firewall@v1
  with:
    access-token: ${{ secrets.DO_ACCESS_TOKEN }}
    firewall-id: eb64eefd-f935-4d75-b0a4-97e3d1dbec87
```

### Custom Protocol/Port

```yml
  with:
    ...
    ports: '8888/udp'
```

### Multiple Ports

```yml
  with:
    ...
    ports: '22,8888/udp'
```

## Inputs

| Key | Required | Default | Description |
| --- | -------- | ------- | ----------- |
| `access-token` | Yes | | _DigitalOcean_'s personal access token |
| `firewall-id` | Yes | | Firewall ID |
| `ports` | No | `22` | Ports to allow (if no protocol specified, `tcp` is applied) |
| `dry-run` | No | `false` | Dry run (no firewall change) |

## Secrets

| Key | Description |
| --- | ----------- |
| `DO_ACCESS_TOKEN` | _DigitalOcean_'s personal access token |

## Outputs

| Key | Example | Description |
| --- | ------- | ----------- |
| `runner-ip` | `1.2.3.4` | IP of GitHub shared runner |
