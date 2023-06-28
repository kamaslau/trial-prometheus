# trial-prometheus

- [Grafana](https://grafana.com/docs/grafana/latest/setup-grafana/installation/docker/): http://localhost:3000
- [Prometheus](https://prometheus.io/docs/prometheus/latest/installation/#using-docker): http://localhost:9090

## 默认端口及账号

http://localhost:3000

admin/admin

## 部署

确保主节点的 `3000`、`9090` 端口，被监控节点的 `9100` 端口已开放。

### 主节点

启动服务

```bash
docker compose up -d
```

#### 添加数据源

[http://localhost:3000/connections/datasources/new](http://localhost:3000/connections/datasources/new)

```bash
sudo nano prometheus.yml
```

#### 添加数据库

`URL` 字段填写 `http://prometheus:9090` 并回车即可。

#### 导入 Dashboard

[http://localhost:3000/dashboard/import](http://localhost:3000/dashboard/import)

1. 在 `Import via grafana.com` 字段填写 `1860` ，点击 `Load`
1. 点选 `promethues` 字段项，点击 `Import`

### 被监控节点

```bash
docker run --name node-exporter --restart always -d -p 9100:9100 prom/node-exporter
```
