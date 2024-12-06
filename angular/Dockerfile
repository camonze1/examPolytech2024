# FROM node:10 as builder

# LABEL maintainer="camillelaunois"

# WORKDIR /app

# COPY . .

# RUN npm install
# RUN npm run build

# FROM nginx:1.27-alpine

# COPY --from=builder /app/dist /usr/share/nginx/html


FROM node:10 as builder

WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

FROM nginx:1.27-alpine

LABEL maintainer="camillelaunois"

COPY nginx/ /etc/nginx/
COPY --from=builder /app/dist/ /usr/share/nginx/html
COPY entrypoint.sh /docker-entrypoint.d/entrypoint.sh
RUN chmod +x /docker-entrypoint.d/entrypoint.sh
