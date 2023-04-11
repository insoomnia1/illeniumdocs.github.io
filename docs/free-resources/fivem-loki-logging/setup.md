# Setup

## System Requirements

You will need a Linux VM / VPS with the following specs:

| Name | Minimum | Recommended |
|----|----|----|
| OS | Linux (Ubuntu 22.04) | Linux (Ubuntu 22.04) |
| CPU | 2 vCPU | 4 vCPU |
| RAM | 2 GB | 4 GB |
| Disk | 20 GB | 50 GB |
| Custom Domain | Required | Required |

## Recommendations for VPS

I can recommend the following providers:

- [Hetzner (CPX11)](https://www.hetzner.com/cloud)
- [Contabo (Cloud VPS S)](https://contabo.com/en/vps/vps-s-ssd/?image=ubuntu.323&qty=1&contract=1&storage-type=vps-s-200-gb-ssd)

## Cloning the Repo

!!! warning

    Make sure that you have your VM / VPS IP, SSH user and SSH password before continuing

* Press the `Windows` key on the keyboard and type `cmd` and press enter to open up the terminal
* SSH into the machine by replacing `<username>` with your SSH user and `<ip>` with your VM / VPS IP below and then run the command on your terminal

  ```bash
  ssh <username>@<ip>
  ```
* Switch to the root user by running the following command in the same terminal (you may be asked to type your SSH password, so do that)

  ```bash
  sudo su -
  ```
* Now install `git` by running the following commands

  ```bash
  apt update
  apt install git -y
  ```
* Clone the `fivem-loki-logging` repo

  ```bash
  git clone https://github.com/iLLeniumStudios/fivem-loki-logging
  cd fivem-loki-logging
  ```

## Editing config.yaml

Now you need to make changes to the `config.yaml` file located in the repository. The default configuration file looks like this:

```bash
baseDomain: ""
email: example@domain.com # Only used if baseDomain is not ""
k3s:
  version: v1.26.3+k3s1
certManager:
  version: v1.11.1 # Do not modify
loki:
  version: 5.0.0 # Do not modify
  storage: 5Gi
  username: admin
  password: supersecurepassword
  exposedPort: 30001 # Only used if baseDomain is ""
  retention: 744h # 24 * 31 (1 Month)
grafana:
  version: 6.52.9 # Do not modify
  username: admin
  password: verysecurepassword
  exposedPort: 30000 # Only used if baseDomain is ""
```

Here’s a reference to the required variables and what they’re used for:

| Key | Description | Default |
|----|----|----|
| baseDomain | This will be the domain that will be used for accessing Loki and Grafana. The resulting URLs will look like so: `grafana.<baseDomain>`, `loki.<baseDomain>`. If you do not set this then your VM / VPS IP will be used instead of the domain and no SSL configuration will be done | `""` |
| email | You need to set this to a valid email **IF** you have set the `basedDomain`. It is used while provisioning SSL certificates  | `example@domain.com` |
| loki.storage | How much storage do you want to allocate to Loki for storing the logs. Make sure it is less than the total disk size and you leave atleast 10GB for the Operating System | `5Gi` |
| loki.username | Username for the Loki instance used for pushing the logs | `admin` |
| loki.password | Password for the Loki instance used for pushing the logs | `supersecurepassword` |
| loki.retention | Retention period of the logs stored in Loki. By default its set to keep logs of the past 31 days (1 month) | `744h` |
| grafana.username | Username for the Grafana instance used for logging in and viewing the logs | `admin` |
| grafana.password | Password for the Grafana instance used for logging in and viewing the logs | `verysecurepassword` |

You can open up `config.yaml` in a terminal text editor like nano using the following command:

```bash
nano config.yaml
```

* If you own a domain and want to use the domain and have SSL configured, then set `baseDomain` with your domain name (can also be a sub-domain)
* Set `loki.storage` based on how much storage you want to allocate to Loki
* Set `loki.username` and `loki.password` to match your preferences
* Set `loki.retention` to the number of hours you want to store the logs for. Old logs get removed automatically when they’re older than the retention period
* Set `grafana.username` and `grafana.password` to match your preferences

After making the changes, save the file by pressing `Ctrl + X` then `Y` and then `Enter`. Doing this properly will throw you back at the terminal. Confirm that the config has been updated by running

```bash
cat config.yaml
```

If it looks good then proceed to the next step

## Configure DNS Records (Only if you have set baseDomain to your domain name)

Skip this step if you do not own a domain or have not modified `baseDomain` key in the config

* Login to your domain provider and create 2 DNS records. Lets assume you have set `myfivemserver.com` as your baseDomain and your VM / VPS IP is `10.0.2.240`, your DNS records should look like the following:

| Name | Record Type | Value | TTL |
|----|----|----|----|
| grafana | A | 10.0.2.240 | 3600 |
| loki | A | 10.0.2.240 | 3600 |

!!! warning

    Make sure that you replace `10.0.2.240` with your VM / VPS IP, otherwise it will not work!!

## Running the installer

Once your DNS entries are in place if you have set baseDomain or left it as default, you can proceed.

Run the following command to start the installation process:

```bash
./install.sh
```

Patiently wait for it to finish as it will take some time to complete. Once finished, you should see something like this:

 ![](https://i.ibb.co/ry8HSxs/image.png)

!!! info

    You will also be presented with the ox_lib config that you can use in the next step. Make sure to take note of that.

You now have both Loki and Grafana running. You can open up the Grafana URL and login using the credentials to see if it works.

The installer automatically configures Loki as the default Datasource so you don’t need to do anything in Grafana except for looking at the logs

## Next steps

- [Using ox_lib with Loki](ox_lib.md)
