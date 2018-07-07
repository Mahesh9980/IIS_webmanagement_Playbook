## IAM - OpenAM WebAgent Installation in IIS 7

### Overview

This playbook installs OpenAM Web Agent in IIS7. The Agent host, profile name, OpenAM host, port, and other attributes needed to create the configuration file (config.txt) needed by the Web Agent installer are passed as variables to the playbook.

### Prerequisites

- Requires Ansible 2.0 or newer.
- Expects Windows 2008/2012 server with IIS7

### Extra variables

- destination_dir: 'C:\Downloads'
- config_file: 'config.txt'
- IIS_Agent_ZIP_File: 'IIS-v7-WINNT-64-Agent-3.3.4'

- Web_Site_Identifier: 1
- AGENT_HOST: localhost
- AGENT_PREF_PORT: 80
- AM_SERVICES_HOST: 'openam.ctepl.com'
- AM_SERVICES_PORT: 8080
- AGENT_PROFILE_NAME: 'IISAgent1'
- AGENT_URL_PREFIX: 'http://localhost:80'
- AUDIT_LOG_FILENAME: 'amAgent_localhost.log'

- applicationHost_dir: C:\Windows\System32\inetsrv\config
- applicationHost_file: 'applicationHost.config'

- Process_Model_Identity: 'LocalSystem'
- Enable_32_bit: 'False'
- Recycling_Time: '00:00:00'

### Usage and example

Run the playbook through command line or from Tower:

         ansible-playbook -i hosts -l windows site.yml

### Output

- Copies the installation archive (IIS-v7-WINNT-64-Agent-3.3.4.zip) to the target host
- Creates the configuration file (config.txt) needed by the Web Policy Agent installer
- Installs Web Policy Agent
- Configures Application Pool Settings
- Restart IIS

### Assumptions
- The Web Agent Profile does not exist
