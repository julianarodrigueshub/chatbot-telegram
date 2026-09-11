# Chatbot Telegram - Temperatura com OpenWeather

## Descrição
Chatbot desenvolvido em n8n que recebe `Cidade,UF,BR` pelo Telegram, consulta a API OpenWeather e retorna a temperatura atual em português.

## Fluxo
Telegram Trigger → Set (`queue`) → HTTP Request (OpenWeather) → Code (validação) → IF → Code (formatação) → Telegram.

## Variáveis
- `OPENWEATHER_API_KEY`: chave da API OpenWeather.
- `TELEGRAM_BOT_TOKEN`: token do bot Telegram.

**Nunca coloque valores reais dessas variáveis no GitHub.**

## Configuração

### OpenWeather
Configure `OPENWEATHER_API_KEY` no ambiente do n8n e reinicie o n8n se necessário. O workflow usa:
`={{ $env.OPENWEATHER_API_KEY }}`

### Telegram
No n8n, crie uma credencial **Telegram API** e informe nela o token obtido no BotFather. Associe essa credencial ao Telegram Trigger e aos dois nós Telegram de envio. A variável esperada para o ambiente é `TELEGRAM_BOT_TOKEN`.

## Importação
1. Abra o n8n.
2. Importe `workflow-chatbot-telegram.json` usando **Import from File**.
3. Selecione a credencial do Telegram nos nós Telegram.
4. Confirme que `OPENWEATHER_API_KEY` está disponível no ambiente.
5. Salve e ative o workflow.

## Uso
Envie ao bot, por exemplo:
`Brasília,DF,BR`

Resposta:
`🌤️ A temperatura em Brasília é de 25°C.`

Para entrada inválida ou cidade inexistente:
`❌ Cidade não encontrada. Use o formato Cidade,UF,BR (ex.: São Paulo,SP,BR).`

## Testes
Teste pelo menos:
- Brasília,DF,BR
- São Paulo,SP,BR
- Rio de Janeiro,RJ,BR
- CidadeInexistente,XX,BR

## Segurança
O JSON não contém tokens ou API keys reais. As credenciais devem permanecer configuradas no n8n e fora do repositório.

## Entrega
- `workflow-chatbot-telegram.json`
- `README.md`
