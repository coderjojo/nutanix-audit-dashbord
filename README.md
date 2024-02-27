# Nutanix Audit/Information Dashboard

## Overview

Nutanix Audit/Information Dashboard is an Ansible-based project aimed at providing a comprehensive dashboard for auditing and monitoring Nutanix clusters. The project is currently being migrated to Golang for improved concurrency and logging capabilities. Prometheus exporter will be integrated for further monitoring.

## Disclaimer

**Please Read Carefully:** This project utilizes internal APIs that are not publicly supported by [Nutanix](https://www.nutanix.dev/). Use caution when deploying this project and ensure that you have thoroughly reviewed all APIs before running it in a production environment. Nutanix will not be responsible for any issues arising from the use of this project and will not provide support for its implementation.

## Compatibility

Tested on:
- Nutanix AOS 6.x till 6.5.5.1
- PC: 2022.9 - 2023.4

**Note:** Some fields may contain negative value, which could be due to licensing violations or API issues.

## Getting Started

To get started with this project, follow these steps:

1. Ensure Ansible is installed on your system.
2. Make the necessary configuration changes in `vars/main.yml` to include your Nutanix PC information.
3. Create or update the `.vault_pass` file with the appropriate credentials:

   ```bash
   echo "nutanix/4u" > .vault_pass
   ```

4. Update the vault_user and pc_password in `vault.yml` and rekey the vault if required:

   ```bash
   ansible-vault edit group_vars/all/vault.yml
   ```

5. Execute the playbook:

   ```bash
   ansible-playbook main.yml --vault-password-file=.vault_pass
   ```

## Customization

Jinja templates are available under `roles/nutanix_generate_report` role, allowing you to customize the generated reports. Sample reports can be found under the `output` folder. You can add additional fields as needed.

Cron Job can be set to schedule running this playbook.

   ```bash
   */10 * * * * cd /path/to/folder/nutanix_audits && ~/.local/bin/ansible-playbook main.yml > logfile.log 2>&1
   ```


## Data Generated

The following data is currently generated for the Nutanix cluster can be found under `output/json_output.html`:


## Support

If you encounter any issues or need assistance, please raise an issue.

