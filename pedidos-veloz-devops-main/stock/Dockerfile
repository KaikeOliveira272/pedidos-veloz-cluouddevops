FROM node:20-alpine
# Segurança: Cria usuário sem privilégios 
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
WORKDIR /app
COPY . .
RUN chown -R appuser:appgroup /app
USER appuser
# Porta 3001 para o Stock
CMD ["sh", "-c", "echo Servico de Estoque Online na porta 3001 && tail -f /dev/null"]