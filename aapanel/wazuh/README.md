1. Create certs.yml in /www/server/panel/data/compose/wazuh/

2. Run comands:

```bash
cd /www/server/panel/data/compose/wazuh/
rm -rf wazuh-certificates
docker run --rm -v $(pwd):/config -v $(pwd)/wazuh-certificates:/certificates wazuh/wazuh-certs-generator:0.0.1

# Entra na pasta
cd /www/server/panel/data/compose/wazuh/

# 1. Garante permissão de leitura
chmod -R 755 wazuh-certificates/
chown -R 1000:1000 wazuh-certificates/

# 2. O COMANDO MÁGICO PARA ROCKY LINUX (Desbloqueia o SELinux)
chcon -R -t container_file_t wazuh-certificates/

# 3. Garante memória para o Indexer (ou ele cai depois)
sysctl -w vm.max_map_count=262144
```
