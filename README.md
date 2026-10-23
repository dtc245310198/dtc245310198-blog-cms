# Blog/CMS - WordPress + MariaDB (DTC245310198)

Hệ thống Blog/CMS chạy bằng Docker Compose: WordPress, MariaDB, phpMyAdmin,
Nginx (HTTPS tự ký), Prometheus, Grafana, Loki, Promtail.

## Chạy hệ thống
1. `cp .env.example .env` rồi điền mật khẩu của bạn.
2. Tạo chứng chỉ tự ký:
   `openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout nginx/certs/blog.key -out nginx/certs/blog.crt -subj "/CN=localhost"`
3. `docker compose up -d` rồi `docker compose ps`.

## Truy cập
- Website: https://<IP-server>:8443 (HTTP 8083 tự chuyển sang HTTPS)
- Grafana: http://<IP-server>:3002
- Prometheus: http://<IP-server>:9092
- phpMyAdmin: chỉ qua 127.0.0.1:8084 (dùng SSH tunnel)

## Lưu ý
File `.env`, khóa riêng và chứng chỉ không được đưa lên GitHub.
