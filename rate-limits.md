# Rate Limits

Para conseguirmos prover maior segurança e tempo de resposta para os usuarios das APIs, utilizamos os limites de requests. Nossos limites funcionam da seguinte forma:

| Grupo          | Chamadas         | Política       | Tempo de espera |
| -------------- | ---------------- | -------------- | --------------- |
| Todas chamadas | Qualquer chamada | 100 solitações | 1 minuto        |



### Erros por exceder o limite <a href="#retornos" id="retornos"></a>

**Erro 429, Chamdas excedidas**

```
{
    "statusCode": 429,
    "message": "Rate limit is exceeded. Try again in 69 seconds."
}
```
