```yaml
version: '3.7'

services:
  n8n:
    image: n8nio/n8n
    container_name: n8n
    environment:
      - DB_TYPE=postgresdb
      - DB_POSTGRESDB_HOST=my_postgres
      - DB_POSTGRESDB_PORT=5432
      - DB_POSTGRESDB_USER=postgres
      - DB_POSTGRESDB_PASSWORD=postgres
      - DB_POSTGRESDB_DATABASE=n8n
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=admin        # Substitua pelo nome de usuário desejado
      - N8N_BASIC_AUTH_PASSWORD=admin # Substitua pela senha desejada
      - GENERIC_TIMEZONE=America/Sao_Paulo
    ports:
      - "5678:5678"
    networks:
      - my-network
    volumes:
      - /root/.n8n
    restart: always

networks:
  my-network:
    external: true

volumes:
  postgres_data:
    external: false 
 ````
para conseguir pegar o link do webwook nao pode ser locahost tem que passar o ip da maquina como podemos observa ali  - N8N_HOST=192.168.56.1  # Use o IP da sua máquina, se necessário

para conectar o n8n no postgres voce deve seguir os passo, ir no conaniner ir em  inspect > networks e pega o "IPAddress": "172.18.0.8",

![image](https://github.com/user-attachments/assets/109ed4e8-3bd3-46d9-a37f-eeac04dac968)

