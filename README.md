
---

## 📄 `email-service`

```markdown
# ✉️ Email Service

Este microserviço é responsável por consumir mensagens enviadas ao RabbitMQ por outros serviços (como o User Service) e realizar o envio de e-mails.

---

## 🚀 Funcionalidades

- Consumir mensagens da fila RabbitMQ.
- Enviar e-mails usando as informações recebidas.
- Registrar status do envio (SENT ou ERROR) no banco de dados.

---

## 🛠 Tecnologias Utilizadas

- Java 17
- Spring Boot
- Spring Web
- Spring Data JPA
- Spring AMQP
- JavaMailSender (Spring Email)
- RabbitMQ
- Postman
- Postgres

---

## 📦 Estrutura de Pacotes

- `listener`: escuta e processa mensagens da fila.
- `service`: lógica de envio do e-mail.
- `model`: representa a entidade do e-mail no banco.
- `repository`: persistência dos registros de envio.

---

## 📨 Estrutura do EmailModel

Campos:
- `emailFrom`, `emailTo`, `subject`, `text`
- `sendDateEmail`: data de envio
- `statusEmail`: enum (`SENT`, `ERROR`)

---

## 🔁 Fluxo do Serviço

1. RabbitMQ entrega mensagem da fila `email.queue`.
2. O listener transforma os dados em um `EmailModel`.
3. Tenta enviar o e-mail com o `JavaMailSender`.
4. Salva no banco com status de envio.

---

## 📦 Fila Escutada

- **Exchange**: `email.exchange`
- **Fila**: `email.queue`
- **Routing Key**: `email.routingKey`

---

## 🧪 Testes

Este serviço será ativado automaticamente quando mensagens forem enviadas para a fila pelo User Service.

Você pode monitorar a fila via painel do RabbitMQ:
