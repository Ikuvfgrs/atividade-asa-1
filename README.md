# Projeto ASA - Entrega 01

Este projeto tem como objetivo demonstrar os conceitos básicos de containers com Docker, criando uma rede com dois serviços essenciais: um servidor DNS (BIND9) e um servidor Web (NGINX), que se comunicam entre si.

## 📁 Estrutura do Projeto

```
atividade-asa-01/
├── dns/
│   ├── Dockerfile
│   ├── db.asa.br
│   └── named.conf.local
├── web/
│   ├── Dockerfile
│   └── index.html
├── service.sh
└── README.md
```

## ⚙️ Como Usar

Antes de tudo, certifique-se de estar com o Docker instalado e funcionando.

1. **Crie uma rede personalizada:**

```
docker network create --subnet=172.20.0.0/16 asa-net
```

2. **Inicie o servidor DNS:**

```
./service.sh dns start
```

3. **Inicie o servidor Web:**

```
./service.sh web start
```

4. **Configure seu sistema (ou container cliente) para usar o servidor DNS:**

- DNS primário: `172.20.0.2`
- Acesse `http://www.asa.br` no navegador (se estiver com DNS corretamente resolvido via container ou /etc/hosts)

5. **Para parar os serviços:**

```
./service.sh dns stop
./service.sh web stop
```

## 🧠 Conceitos Aplicados

- **Dockerfile**: define como cada container deve ser construído.
- **Bind9 (DNS)**: resolve o nome `www.asa.br` para o IP do servidor web.
- **NGINX**: servidor web leve, exibe uma página simples.
- **service.sh**: script automatizador para construir e rodar os containers.
- **Rede Docker**: os containers se comunicam pela rede `asa-net`.


