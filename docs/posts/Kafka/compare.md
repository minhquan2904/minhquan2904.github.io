---
title: Kafka vs RabbitMQ
nav_tile: kafka_vs_rabbitmq
draft: true 
date: 2023-04-10
categories:
  - Kafka
  - RabbitMQ
---

# Phân tích RabbitMQ vs Kafka - Chọn hệ thống tin nhắn phù hợp cho nhu cầu của bạn

![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-000?style=for-the-badge&logo=apachekafka) ![RabbitMQ](https://img.shields.io/badge/Rabbitmq-FF6600?style=for-the-badge&logo=rabbitmq&logoColor=white)

> Bài viết được dịch từ [intellisoft.io](https://intellisoft.io/rabbitmq-vs-kafka-choosing-the-right-messaging-system-for-your-needs/)

Hãy tưởng tượng một không gian trò chuyện sôi động, nơi hàng ngàn người dùng trao đổi thông tin, chia sẻ tin tức và tương tác với sự kiện. Trong môi trường năng động này, hệ thống tin nhắn đóng vai trò như một người điều hành vô hình, đảm bảo mỗi tin nhắn đều đến được người nhận dự định mà không bị trễ hoặc gián đoạn. Tương tự, các ứng dụng phần mềm hiện đại cần có hệ thống tin nhắn mạnh mẽ để xử lý sự giao tiếp phức tạp giữa các thành phần của chúng

RabbitMQ và Apache Kafka là các hệ thống tin nhắn hàng đầu giúp tạo ra sự trao đổi dữ liệu và sự kiện quan trọng trong ngành công nghiệp phát triển phần mềm. Chúng đóng một vai trò quan trọng trong việc phát triển các ứng dụng có khả năng mở rộng và hiệu quả bằng cách cho phép giao tiếp mượt mà giữa các thành phần phần mềm và giúp quản lý các luồng dữ liệu phức tạp. Vậy làm thế nào để bạn quyết định “người chỉ huy” nào phù hợp với ứng dụng của bạn?

Đội ngũ intellisoft có kinh nghiệm rộng lớn trong việc tích hợp các hệ thống tin nhắn vào các kiến trúc ứng dụng phức tạp, chẳng hạn như dự án ZyLAB. Bài viết này sẽ khám phá sự khác biệt giữa Kafka và RabbitMQ, cấu trúc của chúng, các trường hợp sử dụng, và điểm mạnh và yếu. Chúng tôi cũng sẽ cung cấp hướng dẫn về việc chọn hệ thống tin nhắn Kafka hay RabbitMQ dựa trên yêu cầu của ứng dụng của bạn.

## Giải thích các khái niệm về Hệ thống tin nhắn Publish/Subscribe (Pub/Sub) và Message Broker

Trước khi đi sâu vào các chi tiết cụ thể của RabbitMQ và Kafka, điều quan trọng là phải hiểu rõ sự khác biệt cơ bản giữa một hệ thống tin nhắn publish/subscribe (pub/sub) và một message broker.

### Định nghĩa về Message Broker

Message broker là một trung gian giữa các thành phần ứng dụng, tạo điều kiện cho việc giao tiếp bằng cách chuyển dữ liệu. Chức năng chính của message broker là định tuyến thông tin từ các nhà sản xuất (người gửi tin nhắn) đến các người tiêu dùng (người nhận tin nhắn) dựa trên các quy tắc và logic được định trước. Bằng cách sử dụng một message broker, các ứng dụng có thể tập trung vào các chức năng cốt lõi của chúng trong khi broker xử lý việc giao hàng và định tuyến tin nhắn.

### Định nghĩa về Hệ thống tin nhắn Pub/Sub

Mặt khác, một hệ thống tin nhắn publish/subscribe là một mô hình tin nhắn nơi các producers (publishers) gửi tin nhắn mà không chỉ định người nhận. Thay vào đó, họ phân loại tin nhắn vào các topics hoặc channels. Sau đó, consumers (subscribers) biểu thị sự quan tâm đối với các vấn đề cụ thể và nhận thông báo phù hợp với đăng ký của họ. Mô hình tin nhắn này cho phép tách rời giữa producers và consumers, tạo ra sự linh hoạt và khả năng mở rộng hơn trong kiến trúc ứng dụng.

![producers-and-topics](https://intellisoft.io/wp-content/uploads/2023/04/1-producers-and-topics.png.webp)

### So sánh Message Brokers và Hệ thống tin nhắn Pub/Sub

Cả message brokers và hệ thống tin nhắn pub/sub đều quan trọng trong việc tạo điều kiện cho việc giao tiếp giữa các thành phần ứng dụng. Tuy nhiên, chúng khác nhau về cách định tuyến tin nhắn và xử lý mối quan hệ giữa producers và consumers.

Một message broker tập trung vào việc định tuyến tin nhắn dựa trên các quy tắc được định trước, đảm bảo rằng thông tin đến được consumers phù hợp. Nó có thể hỗ trợ nhiều kiểu nhắn tin khác nhau, chẳng hạn như:
- Request/Reply
- Point-to-Point
- Pub/Sub

Mặt khác, hệ thống tin nhắn “pub/sub” nhấn mạnh việc tách rời giữa các producers và consumers. Nó cho phép nhiều consumers nhận tin nhắn từ một producers duy nhất bằng cách đăng ký cùng một chủ đề hoặc kênh.

Các message broker cung cấp việc giao hàng thông tin đáng tin cậy và đảm bảo các tin nhắn đến được người nhận dự định. Họ cũng có thể cung cấp các tùy chọn duy trì tin nhắn, biến đổi và định tuyến. Tuy nhiên, chúng có thể tạo ra một điểm hỏng duy nhất và có thể trở thành nút thắt hiệu suất nếu không được quản lý đúng cách.

Hệ thống tin nhắn pub/sub cho phép linh hoạt và khả năng mở rộng lớn hơn, cho phép các ứng dụng phát triển mà không ảnh hưởng đến việc giao tiếp giữa các producers và consumers. Tuy nhiên, chúng có thể không cung cấp việc chuyển tiếp tin nhắn đảm bảo hoặc các tính năng định tuyến nâng cao.

Bây giờ chúng ta đã tìm hiểu về sự khác biệt giữa các message broker và hệ thống tin nhắn pub/sub, hãy khám phá RabbitMQ và Kafka một cách chi tiết hơn. 

## Kafka là gì?

![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-000?style=for-the-badge&logo=apachekafka)

[Apache Kafka](https://kafka.apache.org/) là một nền tảng streaming với kiến trúc phân tán được thiết kế cho các ứng dụng streaming dữ liệu có khả năng xử lý lớn, chịu lỗi và mở rộng. Ban đầu, nó được phát triển tại [LinkedIn](https://www.linkedin.com/pulse/kafkas-origin-story-linkedin-tanvir-ahmed) và sau đó được mở mã nguồn vào năm 2011. Nhiều tổ chức đã áp dụng rộng rãi Kafka để xây dựng các pipeline dữ liệu thời gian thực, các ứng dụng streaming và kiến trúc dựa trên sự kiện.

### Nguồn gốc và lịch sử của Kafka

Jay Kreps, Neha Narkhede và Jun Rao đã tạo ra Kafka để đáp ứng nhu cầu ngày càng tăng về một hệ thống tin nhắn phân tán hiệu suất cao để xử lý lượng dữ liệu lớn được tạo ra bởi cơ sở hạ tầng của LinkedIn. Các phương pháp tin nhắn truyền thống không thể quản lý hiệu quả các luồng dữ liệu thời gian thực, vì vậy họ đã bắt đầu dự án Kafka để cung cấp một nền tảng thống nhất, có khả năng xử lý lớn và độ trễ thấp


### Kiến trúc của Kafka

Các nhà phát triển đã xây dựng kiến trúc của Kafka xung quanh một dịch vụ log commit phân tán và được sao chép, đây là lõi của chức năng tin nhắn của nó. Các thành phần cơ bản của kiến trúc Kafka bao gồm:

- **Producers**: Các thực thể gửi tin nhắn đến Kafka.

- **Máy chủ (Brokers)**: Đây là các nút Kafka lưu trữ và quản lý các tin nhắn đã được xuất bản.

- **Chủ đề (Topics)**: Các danh mục hoặc kênh mà nhà sản xuất xuất bản tin nhắn.

- **Phân vùng (Partitions)**: Kafka chia các Topics thành nhiều chuỗi hồ sơ có thứ tự và không thể thay đổi được biết đến là các phân vùng, cho phép song song hóa và tăng khả năng xử lý.

- **Consumers**: Các thực thể đọc và xử lý tin nhắn từ Kafka.

- **Cụm (Clusters)**: Các tập hợp của các máy chủ Kafka làm việc cùng nhau để quản lý và phân phối dữ liệu trên nhiều nút.

- **Consumer Groups**: Các tập hợp của Consumer trong Kafka hợp tác để tiêu thụ dữ liệu từ một hoặc nhiều chủ đề.

- **Replicas**: Các bản sao của một phân vùng Kafka được phân phối trên nhiều máy chủ.

- **Leaders**: Các máy chủ được chỉ định trong một cụm Kafka chịu trách nhiệm xử lý tất cả các yêu cầu đọc và ghi cho một phân vùng cụ thể.

- **Followers**: Các máy chủ trong một cụm Kafka sao chép một cách thụ động dữ liệu của người dẫn đầu cho một phân vùng nhất định, sẵn sàng thay thế làm người dẫn đầu mới nếu người dẫn đầu hiện tại gặp sự cố. 

![kafka-architecture](https://intellisoft.io/wp-content/uploads/2023/04/2-kafka-architecture-4.png.webp)

*Kafka cung cấp một sự cam kết về độ bền mạnh mẽ vì các tin nhắn được lưu trữ trên đĩa và được sao chép trên nhiều brokers. Cách tiếp cận này đảm bảo khả năng chịu lỗi cao và giảm thiểu việc mất mát dũ liệu khi 1 node chết.*

## RabbitMQ là gì?

![RabbitMQ](https://img.shields.io/badge/Rabbitmq-FF6600?style=for-the-badge&logo=rabbitmq&logoColor=white)

[RabbitMQ](https://www.rabbitmq.com/) là một message broker mã nguồn mở, sử dụng [Advance Message Queue Tool Protocol](https://www.amqp.org/) (AMQP). Được phát hành vào năm 2007, RabbitMQ đã được phổ biến rộng rãi nhờ sự linh hoạt, độ tin cậy và dễ sử dụng. Bằng cách hoạt động như một message broker and queueing server, RabbitMQ cho phép các ứng dụng đa dạng trao đổi dữ liệu thông qua giao thức chuẩn hoặc các tác vụ xếp hàng để xử lý bởi người tiêu dùng phân tán. Hàng chờ của RabbitMQ có thể lưu trữ task, cho phép broker có thể cân bằng tải và phân phối task.

### Nguồn gốc và lịch sử của RabbitMQ

Rabbit Technologies Ltd, một công ty được thành lập bởi Alexis Richardson và Matthias Radestock, đã phát triển RabbitMQ để tạo ra 1 broker hiệu năng cao, có thể mở rộng và dễ sử dụng, đồng thời có thể hỗ trợ nhiều kiểu tin nhắn khác nhau, và tích hợp đa nền tảng, đa ngôn ngữ.

### Kiến trúc của RabbitMQ

Kiến trúc của RabbitMQ bao gồm một số thành phần chính hỗ trợ việc gửi và định tuyến tin nhắn:

- **Producers**: các đối tượng gửi tin nhắn đến RabbitMQ.
- **Exchanges**: Các thành phần này chịu trách nhiệm nhận tin nhắn từ Producers và định tuyến chúng đến hàng đợi thích hợp dựa trên các quy tắc được xác định trước.
- **Queues**: Bộ đệm lưu trữ tin nhắn cho đến khi người tiêu dùng sử dụng chúng.
- **Bindings**: Các quy tắc xác định mối quan hệ giữa các trao đổi và hàng đợi, xác định việc định tuyến các tin nhắn.
- **Consumers**: Các đối tượng nhận và xử lý tin nhắn từ RabbitMQ

![RabbitMQ](https://intellisoft.io/wp-content/uploads/2023/04/3-rabbitmq-architecture.png.webp)

>RabbitMQ được biết đến với khả năng định tuyến linh hoạt, dễ sử dụng và hỗ trợ nhiều giao thức như: AMQP, MQTT, và STOMP.

## Kafka được sử dụng để làm gì?

Kafka có nhiều trường hợp sử dụng khác nhau, khiến nó trở thành lựa chọn phổ biến cho nhiều loại ứng dụng khác nhau. Một số trường hợp sử dụng Kafka phổ biến bao gồm:

- Data Streaming

- Phân tích dữ liệu thời gian thực

- Hệ thống phân tán

### Kafka trong Data Streaming và phân tích thời gian thực

**Data Streaming** là một trong những trường hợp sử dụng chính của Kafka, trong đó nó hoạt động như một hệ thống nhắn tin có khả năng mở rộng cao và có khả năng chịu lỗi cho phép xử lý dữ liệu theo thời gian thực. Khả năng xử lý các luồng dữ liệu thông lượng cao của Kafka khiến nó trở nên lý tưởng cho việc nhập và xử lý khối lượng dữ liệu lớn theo thời gian thực. Do tính năng này, Kafka rất phù hợp cho các ứng dụng tổng hợp nhật ký, phân tích thời gian thực và lưu trữ dữ liệu.

### Kafka trong hệ thống phân tán

Bạn cũng có thể sử dụng Kafka trong các hệ thống phân tán làm backbone để liên lạc giữa các dịch vụ và thành phần. Kafka đảm bảo rằng các hệ thống phân tán có thể hoạt động hiệu quả và đáng tin cậy bằng cách cung cấp nền tảng nhắn tin có tính sẵn sàng cao, có khả năng chịu lỗi và có khả năng mở rộng. Nó hoạt động để xây dựng kiến trúc microservices, phương pháp tiếp cận hướng sự kiện và các ứng dụng phân tán quy mô lớn khác.