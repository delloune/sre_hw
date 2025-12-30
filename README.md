## Как запустить

### PostgreSQL

```bash

export PATRONI_REPLICATION_PASSWORD="password"
export API_DATABASE_PASSWORD="password"
export PATRONI_SUPERUSER_PASSWORD="password"

cd ansible

ansible-playbook -i inventory/inventory playbooks/deploy_patroni_cluster.yml -e patroni_force_reinit=true
```

![Ansible deployment](png/ansible_init.png)

![Ansible results](png/ansible_res.png)

### Kubernetes

```bash
export KUBECONFIG=kubeconfig.yaml

helm upgrade --install api ./helm/api \
  --namespace sre-cource-student-12 \
  --set database.password="password"
```

![Helm deployment](png/helm.png)


## Результат
```bash
curl -H "Host: api.student12.local" http://77.105.182.79/swagger/index.html
```

![API verification](png/curl.png)
![API verification2](png/curl2.png)
