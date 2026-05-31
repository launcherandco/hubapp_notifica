# 📱 HubApp Notifica WHMCS

O **HubApp Notifica** é um módulo Addon para WHMCS desenvolvido para automatizar a comunicação com seus clientes e administradores via WhatsApp. Ele integra o WHMCS à API da HubApp, permitindo notificações automáticas de faturamento, suporte e segurança, além de uma central para envios manuais.

---

## 🔌 Gateways Suportados

O módulo adapta automaticamente o formato de envio (Payload e Headers) conforme o gateway selecionado no painel:

1.  **Whaticket**: Integração nativa via campo `body` e autenticação Bearer.
2.  **Evolution API (v2/Baileys)**: Suporte completo via `text`, `apikey` e Instâncias.
3.  **Z-Pro**: Compatibilidade total exigindo `externalKey` e `body` para rastreabilidade avançada.

---

## ✨ Funcionalidades Principais

* **Zero Aprovação**: Envie mensagens de texto personalizadas diretamente do seu WHMCS. Edite o conteúdo a qualquer momento sem burocracia.
* **Central Unificada**: Painel administrativo para testes de conexão, envio manual de mensagens para clientes e gestão de textos automáticos.
* **Rastreabilidade**: Envio de chaves únicas (`externalKey`) para gateways que suportam confirmação de leitura e status.
* **Sanitização Inteligente**: O sistema limpa automaticamente a formatação dos números de telefone (DDI+DDD) para garantir a entrega.

---

## 🚀 Instalação Rápida

1.  Baixe e extraia o arquivo no diretório `/modules/addons/`.
2.  A estrutura deve ficar assim:
    * `modules/addons/hubapp_notifica/hubapp_notifica.php`
    * `modules/addons/hubapp_notifica/hooks.php`
    * `modules/addons/hubapp_notifica/lib/HubAppClient.php`
3.  No WHMCS, acesse **Opções > Módulos Addon** e ative o **HubApp Notifica WHMCS**.
4.  Clique em **Configurar** e defina:
    * **Gateway**: Escolha entre Whaticket, Evolution ou Z-Pro.
    * **Endpoint**: A URL de envio da sua API (Ex: `https://api.sua.com/message/sendText/instancia`).
    * **Token**: Sua chave de autenticação (API Key ou Token Bearer).

---

## ⚙️ Variáveis de Personalização

Você pode utilizar as variáveis abaixo para tornar suas mensagens dinâmicas. O módulo fará a substituição automática antes do envio.

| Variável | O que ela exibe | Exemplo |
| :--- | :--- | :--- |
| `{firstname}` | Primeiro nome do cliente | João |
| `{invoiceid}` | ID da Fatura | 1025 |
| `{total}` | Valor Total | 59.90 |
| `{duedate}` | Data de Vencimento | 15/02/2026 |
| `{invoice_url}` | Link da Fatura | https://seudominio.com/viewinvoice... |
| `{ticketsubject}`| Assunto do Ticket | Erro no VPS |
| `{ticketno}` | ID do Ticket | #849232 |
| `{domain}` | Domínio ou Produto | meudominio.com |
| `{username}` | Usuário do Serviço | admin_joao |
| `{password}` | Senha do Serviço | 123456 |
| `{x}` | Dias restantes (Domínio) | 5 |
| `{expirydate}` | Data de Expiração | 20/02/2026 |

---

## 📋 Automações Disponíveis (Hooks)

O módulo monitora e dispara mensagens para os seguintes eventos do WHMCS:

### 💰 Financeiro
* **Fatura Gerada**: Envia o link e vencimento assim que a fatura é criada.
* **Fatura a Vencer**: Aviso automático enviado nos dias anteriores à data de vencimento.
* **Pagamento Confirmado**: Agradecimento automático após a baixa.
* **Lembretes de Atraso**: Régua de cobrança completa (1º, 2º e 3º aviso antes da suspensão).

### 🛠️ Suporte & Admin
* **Resposta em Ticket**: Avisa o cliente quando o suporte responde.
* **Novo Ticket (Admin)**: Alerta o administrador sobre novos chamados abertos.
* **Login Admin**: Segurança proativa avisando sobre acessos ao painel administrativo.

### 📦 Produtos & Serviços
* **Serviço Ativado**: Envia dados de acesso (Login/Senha) após o provisionamento.
* **Serviço Suspenso**: Notifica sobre suspensão automática.
* **Renovação de Domínio**: Avisa dias antes do domínio expirar.

---

## 📄 Licença e Suporte

* **Desenvolvido por**: LD | HubApp / Launcher & Co.
* **Suporte e Atualizações**: [licencas.digital](https://licencas.digital)

---

## 💎 Recomendado para seu WHMCS

> **TENHA SEU WHMCS VERIFICADO**
>
> Garanta mais credibilidade e segurança para o seu sistema por apenas **R$ 250,00 anuais**.
>
> [**👉 CLIQUE AQUI PARA CONTRATAR AGORA**](https://licencas.digital/store/whmcs/whmcs-validado)