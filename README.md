#Docker Compose: Grafana e InfluxDB

Este é um aplicativo Docker multi-contêiner que inclui os seguintes serviços:

* Grafana k6

## Início Rápido

Para iniciar o aplicativo:

1. Clone este repositório.
2. Opcionalmente, altere as credenciais padrão ou a configuração de provisionamento do Grafana.
3. Execute o seguinte comando na raiz do repositório clonado:

```bash
docker-compose up -d
```

## Para parar o aplicativo:

Execute o seguinte comando na raiz do repositório clonado:

```bash
docker-compose down
```

## Executar Scripts

Para executar testes com o K6, use:

```bash
docker-compose run k6
```

## Portas

Os serviços do aplicativo estão disponíveis nas seguintes portas:

| Host Port | Service |
| - | - |
| 3000 | Grafana |

## Volumes

O aplicativo cria os seguintes volumes nomeados (um para cada serviço) para garantir que os dados não sejam perdidos quando o aplicativo for interrompido:

influxdb-storage
grafana-storage

## Usuários

O aplicativo cria dois usuários admin: um para o InfluxDB e outro para o Grafana. Por padrão, o nome de usuário e a senha de ambas as contas são admin. Para substituir as credenciais padrão, defina as seguintes variáveis de ambiente antes de iniciar o aplicativo:

INFLUXDB_USERNAME
INFLUXDB_PASSWORD
GRAFANA_USERNAME
GRAFANA_PASSWORD

## Banco de Dados

O aplicativo cria um banco de dados InfluxDB padrão chamado db0.

## Fontes de Dados
O aplicativo cria uma fonte de dados no Grafana chamada InfluxDB, conectada ao banco de dados InfluxDB padrão (ou seja, db0).

Para provisionar fontes de dados adicionais, consulte a documentação do Grafana e adicione um arquivo de configuração em ./grafana-provisioning/datasources/ antes de iniciar o aplicativo.

## Dashboards

Neste projeto foi utilizado o sadhboard oficila do k6.
Para utilizá-lo, importe o ID 2587 no Grafana em http://localhost:3000/dashboard/new?orgId=1.

Acessar o Dashboard

Logar com "admin"

http://localhost:3000/d/6iZ1NcTGz/k6-load-testing-results?orgId=1&refresh=5s