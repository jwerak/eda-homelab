# EDA Homelab

## Quickstart

Create container

```bash
podman run -d --rm --name eda-listener \
  -p 5000:5000 \
  -v ${HOME}/git/eda-homelab:/etc/ansible:z \
  -v ${HOME}/.ssh:/home/runner/.ssh:z,ro \
  --workdir /etc/ansible \
  quay.io/ansible/ansible-rulebook:latest \
  ansible-rulebook --rulebook /etc/ansible/rulebooks/hello_rulebook.yml \
                   -i /etc/ansible/inventory \
                   --verbose
```

Test API

```bash
curl -X POST localhost:5000 -d '{"action": "hello"}'
```
