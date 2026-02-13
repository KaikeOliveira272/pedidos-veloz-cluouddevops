FROM node:20-alpine
# Segurança: Cria usuário sem privilégios 
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
WORKDIR /app
COPY . .
RUN chown -R appuser:appgroup /app
USER appuser
# Porta 8080 para o Gateway
CMD ["sh", "-c", "echo Gateway Online na porta 8080 && tail -f /dev/null"]