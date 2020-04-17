# devops-playground
Infraestructure to play with jenkins, gitlab, ansible and puppet

Start devops infraestructure
```
docker-compose build
docker-compose up -d
```

## Post actions
### Puppet Agents
docker exec -it remote-host bash
Generar el certificado: `puppet agent -t`

### Fix volumes mounts in local as root for root user docker images
sudo chown $(whoami):$(whoami) -R volumes
