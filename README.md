# HELM General chart


## Usage

Install nginx (deployment + service) 
```shell
helm upgrade \
  --install \
  --set image.repository=nginx \
  --set image.tag=latest \
  --set ports.http.port=80 \
  reverse-proxy .
```

### Resources

```yaml
resources:
  requests:
    memory: "64Mi"
    cpu: "250m"
  limits:
    memory: "128Mi"
    cpu: "500m"
```

### Probes

```yaml
probe:
  httpGet:
    path: /
    port: http
```

### Private registry 

```yaml
imagePullSecrets:
  mycompany:
    create: true
    registry: registry.example.com
    username: user
    password: pass
    email: admin@example.com
```

If parameter `create` is set to `true`, then secret with name `mycompany` will be created.



## TODO
- Job instead of deployment