# Session 10 — Exercise 01: Kafka và Topic dược phẩm

Repo khởi tạo một Kafka broker ở KRaft mode và tự tạo ba topic theo yêu cầu. Broker dùng một node nên replication factor là 1; `medicine-price-updates` giữ thứ tự trong một partition.

## Chạy và kiểm tra

```bash
docker compose up -d
docker compose ps
docker compose exec kafka /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:29092 --list
docker compose exec kafka /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:29092 --describe --topic medicine-stock-events
docker compose exec kafka /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:29092 --describe --topic medicine-price-updates
docker compose exec kafka /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:29092 --describe --topic pharmacy-notifications
```

Ứng dụng chạy trên máy host kết nối `localhost:9092`; container trong Compose dùng `kafka:29092`.

```bash
docker compose down
```

Dùng `docker compose down -v` khi muốn xóa cả dữ liệu broker.
