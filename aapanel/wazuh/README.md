1. Create certs.yml in /www/server/panel/data/compose/wazuh/

2. Run comands:

```bash
cd /www/server/panel/data/compose/wazuh/
rm -rf wazuh-certificates
docker run --rm -v $(pwd):/config -v $(pwd)/wazuh-certificates:/certificates wazuh/wazuh-certs-generator:0.0.1
chown -R 1000:1000 wazuh-certificates/
```
