# Dockerfile-Debian-Apache:1.0

Este repositório contém um Dockerfile que constrói uma imagem baseada em **Debian**, já configurada com o **Apache2**, para servir um site estático dentro de um container Docker.  
O objetivo é fornecer um ambiente simples, reutilizável e funcional para estudos, testes ou deploy rápido de páginas web.

---

## 📦 Sobre a imagem

A imagem gerada:

- Instala e configura o **Apache2**
- Extrai os arquivos do site para `/var/www/html`
- Expõe a porta **80**
- Mantém o Apache rodando em *foreground*
- Pode ser iniciada rapidamente com `docker run`

---

## 🛠️ Dockerfile utilizado

```dockerfile
FROM debian

RUN apt-get update && apt-get install -y apache2 && apt-get clean

ADD site.tar /var/www/html

LABEL description="Apache Webserver 1.0"

VOLUME /var/www/html/

EXPOSE 80

ENTRYPOINT ["/usr/sbin/apachectl"]

CMD ["-D", "FOREGROUND"]
```

---

## 🚀 Como usar esta imagem

### 1. Construir a imagem

```bash
docker image build -t debian-apache:1.0 .
```

### 2. Executar o container

```bash
docker run -dti -p 80:80 --name meu-apache debian-apache:1.0
```

Acesse o site em:

```
http://localhost
```

---

## 🙏 Créditos

Os arquivos do site utilizados nesta imagem Docker foram obtidos do projeto:

🔗 **Denilson Bonatti** — https://github.com/denilsonbonatti/linux-site-dio

Agradecimentos também à **Jill**, pelo conteúdo relacionado ao material educacional.

Veja **CREDITS.md** para mais detalhes.

---

## ⚖️ Licença e responsabilidade

Este repositório utiliza conteúdo criado por terceiros.  
Verifique a licença do projeto original antes de redistribuição comercial ou derivada.

