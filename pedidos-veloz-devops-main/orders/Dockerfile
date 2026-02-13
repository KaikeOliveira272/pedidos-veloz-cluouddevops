FROM node:20-alpine
# Segurança: Cria usuário sem privilégios 
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
WORKDIR /app
COPY . .
RUN chown -R appuser:appgroup /app
USER appuser
# Porta 3000 para o Orders
CMD ["sh", "-c", "echo Servico de Pedidos Online na porta 3000 && tail -f /dev/null"]