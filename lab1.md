# Лабораторная работа №1
Тема: Утилиты для разработки проектов (Unix tools).  
ОС: Debian GNU/Linux  
Цель: освоить базовые команды shell, работу с переменными среды, архивами, поиском/фильтрацией файлов, а также сборку библиотеки Boost.

---

## 1. Подготовка рабочего пространства

### 1.1 Переменные среды и alias
```bash
export GITHUB_USERNAME=<ваш_github_username>
export GIST_TOKEN=<ваш_gist_token>
alias edit=nano

### 1.2 Создание структуры каталогов
mkdir -p ${GITHUB_USERNAME}/workspace
cd ${GITHUB_USERNAME}/workspace

mkdir -p workspace/tasks
mkdir -p workspace/projects
mkdir -p workspace/reports
cd workspace
pwd

## 2. Установка Node.js (по туториалу) и работа с PATH
### 2.1 Скачивание и распаковка
wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
tar -xf node-v6.11.5-linux-x64.tar.xz
rm -rf node-v6.11.5-linux-x64.tar.xz
mv node-v6.11.5-linux-x64 node
### 2.2 Добавление в PATH
ls node/bin
echo ${PATH}
export PATH=${PATH}:pwd/node/bin
echo ${PATH}

Вывод ls node/bin:
node  npm
## 3. Установка утилиты gist и настройка токена
### 3.1 (Было выполнено в лабораторной работе 00)
Вывод ls -lah ~/.gist:
-rw------- 1 kgu kgu 94 Feb 27 12:19 /home/kgu/.gist

## 4. Homework: Boost 1.69.0
### 4.1 Скачивание Boost

Надёжный вариант скачивания на Debian:
wget -O boost_1_69_0.tar.gz "https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download"
file boost_1_69_0.tar.gz

Вывод file boost_1_69_0.tar.gz:
boost_1_69_0.tar.gz: gzip compressed data, last modified: Wed Dec  5 20:37:57 2018, max compression, from Unix, original size modulo 2^32 635781120


## 5. Поиск и подсчёт файлов
### 5.1 Количество файлов в ~/boost_1_69_0 без вложенных директорий
cd ~/boost_1_69_0
find . -maxdepth 1 -type f | wc -l

Результат:
16
### 5.2 Количество файлов включая вложенные директории
find . -type f | wc -l

Результат:

61838
### 5.3 Количество заголовочных .h, .cpp и остальных файлов
find . -type f -name "*.h"   | wc -l
find . -type f -name "*.cpp" | wc -l
find . -type f ! -name "*.h" ! -name "*.cpp" | wc -l

Результаты:

.h: 296
.cpp: 13789
other: 47753

## 6. Поиск файла any.hpp
find . -name "any.hpp"

Найденные пути:

./boost/proto/detail/any.hpp
./boost/type_erasure/any.hpp
./boost/xpressive/detail/utility/any.hpp
./boost/spirit/home/support/algorithm/any.hpp
./boost/any.hpp
./boost/hana/fwd/any.hpp
./boost/hana/any.hpp
./boost/fusion/include/any.hpp
./boost/fusion/algorithm/query/any.hpp
./boost/fusion/algorithm/query/detail/any.hpp

## 7. Поиск упоминаний boost::asio
grep -RIl "boost::asio" .

Файлы, содержащие boost::asio:

./doc/html/boost_asio/reference/basic_socket_acceptor/basic_socket_acceptor.html
./doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload5.html
./doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload3.html
./doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload6.html
./doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload4.html
./doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload1.html
./doc/html/boost_asio/reference/basic_socket_acceptor/async_accept/overload2.html
./doc/html/boost_asio/reference/basic_socket_acceptor/receive_low_watermark.html
./doc/html/boost_asio/reference/basic_socket_acceptor/reuse_address.html
./doc/html/boost_asio/reference/basic_socket_acceptor/accept.html
./doc/html/boost_asio/reference/transfer_exactly.html
./doc/html/boost_asio/reference/io_service.html
./doc/html/boost_asio/reference/basic_socket_acceptor.html
./doc/html/boost_asio/reference/basic_streambuf.html
./doc/html/boost_asio/reference/null_buffers/value_type.html
./doc/html/boost_asio/reference/is_error_code_enum_lt__netdb_errors__gt_.html
./doc/html/boost_asio/reference/ip__multicast__leave_group.html
./doc/html/boost_asio/reference/basic_deadline_timer.html
./doc/html/boost_asio/reference/use_future_t.html
./doc/html/boost_asio/reference/spawn.html
./doc/html/boost_asio/reference/posix__stream_descriptor/async_wait.html
./doc/html/boost_asio/reference/posix__stream_descriptor/wait/overload1.html
./doc/html/boost_asio/reference/posix__stream_descriptor/wait/overload2.html
./doc/html/boost_asio/reference/posix__stream_descriptor/bytes_readable.html
./doc/html/boost_asio/reference/posix__stream_descriptor/write_some/overload1.html
./doc/html/boost_asio/reference/posix__stream_descriptor/async_write_some.html
./doc/html/boost_asio/reference/posix__stream_descriptor/io_control/overload1.html
./doc/html/boost_asio/reference/posix__stream_descriptor/io_control/overload2.html
./doc/html/boost_asio/reference/posix__stream_descriptor/get_io_service.html
./doc/html/boost_asio/reference/posix__stream_descriptor/stream_descriptor/overload1.html
./doc/html/boost_asio/reference/posix__stream_descriptor/stream_descriptor/overload2.html
./doc/html/boost_asio/reference/posix__stream_descriptor/get_io_context.html
./doc/html/boost_asio/reference/posix__stream_descriptor/release.html
./doc/html/boost_asio/reference/posix__stream_descriptor/async_read_some.html
./doc/html/boost_asio/reference/posix__stream_descriptor/native_non_blocking/overload3.html
./doc/html/boost_asio/reference/posix__stream_descriptor/native_non_blocking/overload1.html
./doc/html/boost_asio/reference/posix__stream_descriptor/native_non_blocking/overload2.html
./doc/html/boost_asio/reference/posix__stream_descriptor/non_blocking/overload3.html
./doc/html/boost_asio/reference/posix__stream_descriptor/non_blocking/overload1.html
./doc/html/boost_asio/reference/posix__stream_descriptor/non_blocking/overload2.html
./doc/html/boost_asio/reference/posix__stream_descriptor/cancel/overload1.html
./doc/html/boost_asio/reference/posix__stream_descriptor/cancel/overload2.html
./doc/html/boost_asio/reference/posix__stream_descriptor/close/overload1.html
./doc/html/boost_asio/reference/posix__stream_descriptor/close/overload2.html
./doc/html/boost_asio/reference/posix__stream_descriptor/stream_descriptor.html
./doc/html/boost_asio/reference/posix__stream_descriptor/read_some/overload1.html
./doc/html/boost_asio/reference/async_completion/completion_handler_type.html
./doc/html/boost_asio/reference/yield_context.html
./doc/html/boost_asio/reference/basic_deadline_timer/async_wait.html
./doc/html/boost_asio/reference/basic_deadline_timer/expires_at/overload3.html
./doc/html/boost_asio/reference/basic_deadline_timer/expires_at/overload2.html
./doc/html/boost_asio/reference/basic_deadline_timer/get_io_service.html
./doc/html/boost_asio/reference/basic_deadline_timer/get_io_context.html
./doc/html/boost_asio/reference/basic_deadline_timer/expires_from_now/overload3.html
./doc/html/boost_asio/reference/basic_deadline_timer/expires_from_now/overload2.html
./doc/html/boost_asio/reference/basic_deadline_timer/cancel_one/overload1.html
./doc/html/boost_asio/reference/basic_deadline_timer/cancel_one/overload2.html
./doc/html/boost_asio/reference/basic_deadline_timer/cancel/overload1.html
./doc/html/boost_asio/reference/basic_deadline_timer/cancel/overload2.html
./doc/html/boost_asio/reference/basic_deadline_timer/basic_deadline_timer.html
./doc/html/boost_asio/reference/basic_deadline_timer/basic_deadline_timer/overload3.html
./doc/html/boost_asio/reference/basic_deadline_timer/basic_deadline_timer/overload1.html
./doc/html/boost_asio/reference/basic_deadline_timer/basic_deadline_timer/overload2.html
./doc/html/boost_asio/reference/transfer_at_least.html
./doc/html/boost_asio/reference/SignalHandler.html
./doc/html/boost_asio/reference/windows__object_handle/async_wait.html
./doc/html/boost_asio/reference/windows__object_handle/get_io_service.html
./doc/html/boost_asio/reference/windows__object_handle/get_io_context.html
./doc/html/boost_asio/reference/windows__object_handle/object_handle/overload1.html
./doc/html/boost_asio/reference/windows__object_handle/object_handle/overload2.html
./doc/html/boost_asio/reference/windows__object_handle/object_handle.html
./doc/html/boost_asio/reference/windows__object_handle/cancel/overload1.html
./doc/html/boost_asio/reference/windows__object_handle/cancel/overload2.html
./doc/html/boost_asio/reference/windows__object_handle/close/overload1.html
./doc/html/boost_asio/reference/windows__object_handle/close/overload2.html
./doc/html/boost_asio/reference/is_error_code_enum_lt__ssl_errors__gt_/value.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/async_receive/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/async_receive/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/connect/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/connect/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/async_wait.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/do_not_route.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/wait/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/wait/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/bytes_readable.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/send_low_watermark.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/release/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/release/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/local_endpoint/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/local_endpoint/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/out_of_band_inline.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/send_buffer_size.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/send/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/broadcast.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/io_control/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/io_control/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/set_option/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/set_option/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/get_option/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/get_option/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/get_io_service.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/get_io_context.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/debug.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/receive_buffer_size.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/async_send.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/bind/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/bind/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/native_non_blocking/overload3.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/native_non_blocking/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/native_non_blocking/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/enable_connection_aborted.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/non_blocking/overload3.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/non_blocking/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/non_blocking/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/cancel/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/cancel/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/linger.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/receive/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/receive/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/close/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/close/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/open/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/open/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/keep_alive.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/shutdown/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/shutdown/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/basic_seq_packet_socket.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/remote_endpoint/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/remote_endpoint/overload2.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/async_connect.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/receive_low_watermark.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/reuse_address.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/basic_seq_packet_socket/overload3.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/basic_seq_packet_socket/overload4.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/basic_seq_packet_socket/overload1.html
./doc/html/boost_asio/reference/basic_seq_packet_socket/basic_seq_packet_socket/overload2.html
./doc/html/boost_asio/reference/is_error_code_enum_lt__basic_errors__gt_.html
./doc/html/boost_asio/reference/ShutdownHandler.html
./doc/html/boost_asio/reference/is_error_code_enum_lt__addrinfo_errors__gt_.html
./doc/html/boost_asio/reference/error__addrinfo_category.html
./doc/html/boost_asio/reference/async_write_at/overload3.html
./doc/html/boost_asio/reference/async_write_at/overload4.html
./doc/html/boost_asio/reference/async_write_at/overload1.html
./doc/html/boost_asio/reference/async_write_at/overload2.html
./doc/html/boost_asio/reference/async_connect/overload5.html
./doc/html/boost_asio/reference/async_connect/overload3.html
./doc/html/boost_asio/reference/async_connect/overload6.html
./doc/html/boost_asio/reference/async_connect/overload4.html
./doc/html/boost_asio/reference/async_connect/overload1.html
./doc/html/boost_asio/reference/async_connect/overload2.html
./doc/html/boost/process/async_pipe.html
./doc/html/boost/process/std_in.html
./doc/html/boost/process/std_out.html
./doc/html/boost/process/on_exit.html
./doc/html/boost/process/spawn.html
./doc/html/process/reference.html
./libs/beast/CHANGELOG.md
./libs/beast/doc/docca/include/docca/doxygen.xsl
./libs/beast/doc/qbk/08_design/3_websocket_zaphoyd.qbk
./libs/beast/doc/qbk/08_design/4_faq.qbk
./libs/beast/doc/qbk/03_core/1_asio.qbk
./libs/beast/doc/qbk/07_concepts/DynamicBuffer.qbk
./libs/beast/doc/qbk/07_concepts/Streams.qbk
./libs/beast/doc/qbk/00_main.qbk
./libs/beast/doc/qbk/reference.qbk
./libs/beast/doc/html/beast/more_examples/expect_100_continue_server.html
./libs/beast/doc/html/beast/ref/boost__beast__websocket__async_teardown/overload3.html
./libs/beast/doc/html/beast/ref/boost__beast__websocket__async_teardown/overload1.html
./libs/beast/doc/html/beast/ref/boost__beast__websocket__async_teardown/overload2.html
./libs/beast/doc/html/beast/ref/boost__beast__http__error.html
./libs/beast/doc/html/beast/ref/boost__beast__basic_timeout_socket/async_write_some.html
./libs/beast/doc/html/beast/ref/boost__beast__basic_timeout_socket/async_read_some.html
./libs/beast/doc/html/beast/using_io/example_detect_ssl.html
./libs/beast/doc/html/beast/using_io/writing_composed_operations.html
./libs/beast/test/beast/http/chunk_encode.cpp
./libs/beast/test/beast/http/file_body.cpp
./libs/beast/test/beast/http/read.cpp
./libs/beast/test/beast/http/basic_parser.cpp
./libs/beast/test/beast/http/span_body.cpp
./libs/beast/test/beast/http/message_fuzz.hpp
./libs/beast/test/beast/http/parser.cpp
./libs/beast/test/beast/http/dynamic_body.cpp
./libs/beast/test/beast/http/write.cpp
./libs/beast/test/beast/http/serializer.cpp
./libs/beast/test/beast/http/test_parser.hpp
./libs/beast/test/beast/core/multi_buffer.cpp
./libs/beast/test/beast/core/buffers_cat.cpp
./libs/beast/test/beast/core/buffers_suffix.cpp
./libs/beast/test/beast/core/buffers_prefix.cpp
./libs/beast/test/beast/core/read_size.cpp
./libs/beast/test/beast/core/buffer.cpp
./libs/beast/test/beast/core/buffers_adapter.cpp
./libs/beast/test/beast/core/buffered_read_stream.cpp
./libs/beast/test/beast/core/flat_buffer.cpp
./libs/beast/test/beast/core/bind_handler.cpp
./libs/beast/test/beast/core/buffer_test.hpp
./libs/beast/test/beast/core/static_buffer.cpp
./libs/beast/test/beast/core/flat_static_buffer.cpp
./libs/beast/test/beast/core/type_traits.cpp
./libs/beast/test/beast/websocket/test.hpp
./libs/beast/test/beast/websocket/close.cpp
./libs/beast/test/beast/websocket/read2.cpp
./libs/beast/test/beast/websocket/stream.cpp
./libs/beast/test/beast/websocket/utf8_checker.cpp
./libs/beast/test/beast/websocket/doc_snippets.cpp
./libs/beast/test/beast/websocket/read1.cpp
./libs/beast/test/beast/websocket/handshake.cpp
./libs/beast/test/beast/websocket/ping.cpp
./libs/beast/test/beast/websocket/write.cpp
./libs/beast/test/beast/websocket/accept.cpp
./libs/beast/test/beast/experimental/timeout_socket.cpp
./libs/beast/test/beast/experimental/timeout_service.cpp
./libs/beast/test/beast/experimental/flat_stream.cpp
./libs/beast/test/beast/experimental/icy_stream.cpp
./libs/beast/test/bench/buffers/bench_buffers.cpp
./libs/beast/test/bench/wsload/wsload.cpp
./libs/beast/test/bench/parser/bench_parser.cpp
./libs/beast/test/bench/parser/nodejs_parser.hpp
./libs/beast/test/doc/http_snippets.cpp
./libs/beast/test/doc/http_examples.cpp
./libs/beast/test/doc/websocket_snippets.cpp
./libs/beast/test/doc/core_examples.cpp
./libs/beast/test/doc/core_snippets.cpp
./libs/beast/test/doc/exemplars.cpp
./libs/beast/test/extras/include/boost/beast/test/yield_to.hpp
./libs/beast/test/extras/include/boost/beast/test/websocket.hpp
./libs/beast/test/extras/include/boost/beast/test/sig_wait.hpp
./libs/beast/example/advanced/server-flex/advanced_server_flex.cpp
./libs/beast/example/advanced/server/advanced_server.cpp
./libs/beast/example/common/server_certificate.hpp
./libs/beast/example/common/root_certificates.hpp
./libs/beast/example/common/session_alloc.hpp
./libs/beast/example/common/detect_ssl.hpp
./libs/beast/example/http/client/crawl/http_crawl.cpp
./libs/beast/example/http/client/coro-ssl/http_client_coro_ssl.cpp
./libs/beast/example/http/client/async/http_client_async.cpp
./libs/beast/example/http/client/async-ssl/http_client_async_ssl.cpp
./libs/beast/example/http/client/coro/http_client_coro.cpp
./libs/beast/example/http/client/sync/http_client_sync.cpp
./libs/beast/example/http/client/sync-ssl/http_client_sync_ssl.cpp
./libs/beast/example/http/server/small/http_server_small.cpp
./libs/beast/example/http/server/coro-ssl/http_server_coro_ssl.cpp
./libs/beast/example/http/server/async/http_server_async.cpp
./libs/beast/example/http/server/stackless-ssl/http_server_stackless_ssl.cpp
./libs/beast/example/http/server/fast/http_server_fast.cpp
./libs/beast/example/http/server/async-ssl/http_server_async_ssl.cpp
./libs/beast/example/http/server/coro/http_server_coro.cpp
./libs/beast/example/http/server/sync/http_server_sync.cpp
./libs/beast/example/http/server/flex/http_server_flex.cpp
./libs/beast/example/http/server/stackless/http_server_stackless.cpp
./libs/beast/example/http/server/sync-ssl/http_server_sync_ssl.cpp
./libs/beast/example/doc/http_examples.hpp
./libs/beast/example/websocket/client/coro-ssl/websocket_client_coro_ssl.cpp
./libs/beast/example/websocket/client/async/websocket_client_async.cpp
./libs/beast/example/websocket/client/async-ssl/websocket_client_async_ssl.cpp
./libs/beast/example/websocket/client/coro/websocket_client_coro.cpp
./libs/beast/example/websocket/client/sync/websocket_client_sync.cpp
./libs/beast/example/websocket/client/sync-ssl/websocket_client_sync_ssl.cpp
./libs/beast/example/websocket/server/coro-ssl/websocket_server_coro_ssl.cpp
./libs/beast/example/websocket/server/async/websocket_server_async.cpp
./libs/beast/example/websocket/server/stackless-ssl/websocket_server_stackless_ssl.cpp
./libs/beast/example/websocket/server/fast/websocket_server_fast.cpp
./libs/beast/example/websocket/server/async-ssl/websocket_server_async_ssl.cpp
./libs/beast/example/websocket/server/coro/websocket_server_coro.cpp
./libs/beast/example/websocket/server/sync/websocket_server_sync.cpp
./libs/beast/example/websocket/server/stackless/websocket_server_stackless.cpp
./libs/beast/example/websocket/server/sync-ssl/websocket_server_sync_ssl.cpp
./libs/beast/example/echo-op/echo_op.cpp
./libs/beast/example/cppcon2018/net.hpp
./libs/asio/doc/overview/buffers.qbk
./libs/asio/doc/overview/ssl.qbk
./libs/asio/doc/overview/strands.qbk
./libs/asio/doc/overview/spawn.qbk
./libs/asio/doc/overview/line_based.qbk
./libs/asio/doc/overview/basics.qbk
./libs/asio/doc/overview/signals.qbk
./libs/asio/doc/overview/coroutines_ts.qbk
./libs/asio/doc/overview/posix.qbk
./libs/asio/doc/overview/allocation.qbk
./libs/asio/doc/overview/cpp2011.qbk
./libs/asio/doc/overview/protocols.qbk
./libs/asio/doc/overview/coroutine.qbk
./libs/asio/doc/overview/other_protocols.qbk
./libs/asio/doc/using.qbk
./libs/asio/doc/reference.xsl
./libs/asio/doc/examples.qbk
./libs/asio/doc/reference.qbk
./libs/asio/doc/tutorial.qbk
./libs/asio/doc/requirements/WaitHandler.qbk
./libs/asio/doc/requirements/ResolveHandler.qbk
./libs/asio/doc/requirements/ConnectHandler.qbk
./libs/asio/doc/requirements/MoveAcceptHandler.qbk
./libs/asio/doc/requirements/RangeConnectHandler.qbk
./libs/asio/doc/requirements/MutableBufferSequence.qbk
./libs/asio/doc/requirements/WriteHandler.qbk
./libs/asio/doc/requirements/ConstBufferSequence.qbk
./libs/asio/doc/requirements/SignalHandler.qbk
./libs/asio/doc/requirements/IteratorConnectHandler.qbk
./libs/asio/doc/requirements/ShutdownHandler.qbk
./libs/asio/doc/requirements/BufferedHandshakeHandler.qbk
./libs/asio/doc/requirements/HandshakeHandler.qbk
./libs/asio/doc/requirements/Handler.qbk
./libs/asio/doc/requirements/ReadHandler.qbk
./libs/asio/doc/requirements/AcceptHandler.qbk
./libs/asio/test/unit_test.hpp
./libs/asio/test/buffered_stream.cpp
./libs/asio/test/generic/raw_protocol.cpp
./libs/asio/test/generic/stream_protocol.cpp
./libs/asio/test/generic/datagram_protocol.cpp
./libs/asio/test/generic/seq_packet_protocol.cpp
./libs/asio/test/streambuf.cpp
./libs/asio/test/read_until.cpp
./libs/asio/test/use_future.cpp
./libs/asio/test/strand.cpp
./libs/asio/test/io_context.cpp
./libs/asio/test/read_at.cpp
./libs/asio/test/coroutine.cpp
./libs/asio/test/ssl/stream.cpp
./libs/asio/test/read.cpp
./libs/asio/test/is_write_buffered.cpp
./libs/asio/test/buffer.cpp
./libs/asio/test/system_timer.cpp
./libs/asio/test/serial_port.cpp
./libs/asio/test/latency/tcp_server.cpp
./libs/asio/test/latency/udp_server.cpp
./libs/asio/test/latency/udp_client.cpp
./libs/asio/test/latency/tcp_client.cpp
./libs/asio/test/buffered_read_stream.cpp
./libs/asio/test/archetypes/async_ops.hpp
./libs/asio/test/archetypes/deprecated_async_ops.hpp
./libs/asio/test/ip/host_name.cpp
./libs/asio/test/ip/udp.cpp
./libs/asio/test/ip/network_v6.cpp
./libs/asio/test/ip/address.cpp
./libs/asio/test/ip/tcp.cpp
./libs/asio/test/ip/address_v6.cpp
./libs/asio/test/ip/multicast.cpp
./libs/asio/test/ip/icmp.cpp
./libs/asio/test/ip/address_v4.cpp
./libs/asio/test/ip/unicast.cpp
./libs/asio/test/ip/network_v4.cpp
./libs/asio/test/ip/v6_only.cpp
./libs/asio/test/error.cpp
./libs/asio/test/buffered_write_stream.cpp
./libs/asio/test/posix/stream_descriptor.cpp
./libs/asio/test/deadline_timer.cpp
./libs/asio/test/socket_base.cpp
./libs/asio/test/signal_set.cpp
./libs/asio/test/serial_port_base.cpp
./libs/asio/test/write.cpp
./libs/asio/test/windows/stream_handle.cpp
./libs/asio/test/windows/object_handle.cpp
./libs/asio/test/windows/overlapped_ptr.cpp
./libs/asio/test/windows/random_access_handle.cpp
./libs/asio/test/connect.cpp
./libs/asio/test/is_read_buffered.cpp
./libs/asio/test/buffers_iterator.cpp
./libs/asio/test/local/stream_protocol.cpp
./libs/asio/test/local/datagram_protocol.cpp
./libs/asio/test/local/connect_pair.cpp
./libs/asio/test/write_at.cpp
./libs/asio/example/cpp17/coroutines_ts/refactored_echo_server.cpp
./libs/asio/example/cpp17/coroutines_ts/double_buffered_echo_server.cpp
./libs/asio/example/cpp17/coroutines_ts/chat_server.cpp
./libs/asio/example/cpp17/coroutines_ts/echo_server.cpp
./libs/asio/example/cpp17/coroutines_ts/range_based_for.cpp
./libs/asio/example/cpp03/invocation/prioritised_handlers.cpp
./libs/asio/example/cpp03/echo/blocking_udp_echo_server.cpp
./libs/asio/example/cpp03/echo/blocking_tcp_echo_client.cpp
./libs/asio/example/cpp03/echo/async_tcp_echo_server.cpp
./libs/asio/example/cpp03/echo/async_udp_echo_server.cpp
./libs/asio/example/cpp03/echo/blocking_tcp_echo_server.cpp
./libs/asio/example/cpp03/echo/blocking_udp_echo_client.cpp
./libs/asio/example/cpp03/iostreams/http_client.cpp
./libs/asio/example/cpp03/iostreams/daytime_client.cpp
./libs/asio/example/cpp03/iostreams/daytime_server.cpp
./libs/asio/example/cpp03/http/server3/reply.hpp
./libs/asio/example/cpp03/http/server3/connection.cpp
./libs/asio/example/cpp03/http/server3/server.cpp
./libs/asio/example/cpp03/http/server3/connection.hpp
./libs/asio/example/cpp03/http/server3/reply.cpp
./libs/asio/example/cpp03/http/server3/server.hpp
./libs/asio/example/cpp03/http/server2/reply.hpp
./libs/asio/example/cpp03/http/server2/io_context_pool.cpp
./libs/asio/example/cpp03/http/server2/connection.cpp
./libs/asio/example/cpp03/http/server2/server.cpp
./libs/asio/example/cpp03/http/server2/io_context_pool.hpp
./libs/asio/example/cpp03/http/server2/connection.hpp
./libs/asio/example/cpp03/http/server2/reply.cpp
./libs/asio/example/cpp03/http/server2/server.hpp
./libs/asio/example/cpp03/http/client/async_client.cpp
./libs/asio/example/cpp03/http/client/sync_client.cpp
./libs/asio/example/cpp03/http/server4/reply.hpp
./libs/asio/example/cpp03/http/server4/server.cpp
./libs/asio/example/cpp03/http/server4/reply.cpp
./libs/asio/example/cpp03/http/server4/request_parser.hpp
./libs/asio/example/cpp03/http/server4/server.hpp
./libs/asio/example/cpp03/http/server4/main.cpp
./libs/asio/example/cpp03/http/server/reply.hpp
./libs/asio/example/cpp03/http/server/connection.cpp
./libs/asio/example/cpp03/http/server/server.cpp
./libs/asio/example/cpp03/http/server/connection.hpp
./libs/asio/example/cpp03/http/server/reply.cpp
./libs/asio/example/cpp03/http/server/server.hpp
./libs/asio/example/cpp03/spawn/echo_server.cpp
./libs/asio/example/cpp03/spawn/parallel_grep.cpp
./libs/asio/example/cpp03/buffers/reference_counted.cpp
./libs/asio/example/cpp03/timeouts/async_tcp_client.cpp
./libs/asio/example/cpp03/timeouts/server.cpp
./libs/asio/example/cpp03/timeouts/blocking_token_tcp_client.cpp
./libs/asio/example/cpp03/timeouts/blocking_udp_client.cpp
./libs/asio/example/cpp03/timeouts/blocking_tcp_client.cpp
./libs/asio/example/cpp03/nonblocking/third_party_lib.cpp
./libs/asio/example/cpp03/ssl/client.cpp
./libs/asio/example/cpp03/ssl/server.cpp
./libs/asio/example/cpp03/serialization/client.cpp
./libs/asio/example/cpp03/serialization/server.cpp
./libs/asio/example/cpp03/serialization/connection.hpp
./libs/asio/example/cpp03/icmp/ping.cpp
./libs/asio/example/cpp03/icmp/ipv4_header.hpp
./libs/asio/example/cpp03/multicast/sender.cpp
./libs/asio/example/cpp03/multicast/receiver.cpp
./libs/asio/example/cpp03/timers/time_t_timer.cpp
./libs/asio/example/cpp03/tutorial/daytime1/client.cpp
./libs/asio/example/cpp03/tutorial/daytime5/server.cpp
./libs/asio/example/cpp03/tutorial/timer2/timer.cpp
./libs/asio/example/cpp03/tutorial/daytime_dox.txt
./libs/asio/example/cpp03/tutorial/timer_dox.txt
./libs/asio/example/cpp03/tutorial/daytime4/client.cpp
./libs/asio/example/cpp03/tutorial/timer5/timer.cpp
./libs/asio/example/cpp03/tutorial/daytime6/server.cpp
./libs/asio/example/cpp03/tutorial/timer1/timer.cpp
./libs/asio/example/cpp03/tutorial/timer3/timer.cpp
./libs/asio/example/cpp03/tutorial/daytime2/server.cpp
./libs/asio/example/cpp03/tutorial/daytime7/server.cpp
./libs/asio/example/cpp03/tutorial/timer4/timer.cpp
./libs/asio/example/cpp03/tutorial/daytime3/server.cpp
./libs/asio/example/cpp03/chat/chat_server.cpp
./libs/asio/example/cpp03/chat/posix_chat_client.cpp
./libs/asio/example/cpp03/chat/chat_client.cpp
./libs/asio/example/cpp03/allocation/server.cpp
./libs/asio/example/cpp03/porthopper/protocol.hpp
./libs/asio/example/cpp03/porthopper/client.cpp
./libs/asio/example/cpp03/porthopper/server.cpp
./libs/asio/example/cpp03/socks4/socks4.hpp
./libs/asio/example/cpp03/socks4/sync_client.cpp
./libs/asio/example/cpp03/services/basic_logger.hpp
./libs/asio/example/cpp03/services/daytime_client.cpp
./libs/asio/example/cpp03/services/logger_service.hpp
./libs/asio/example/cpp03/services/logger_service.cpp
./libs/asio/example/cpp03/windows/transmit_file.cpp
./libs/asio/example/cpp03/local/stream_client.cpp
./libs/asio/example/cpp03/local/iostream_client.cpp
./libs/asio/example/cpp03/local/stream_server.cpp
./libs/asio/example/cpp03/local/connect_pair.cpp
./libs/asio/example/cpp03/fork/daemon.cpp
./libs/asio/example/cpp03/fork/process_per_connection.cpp
./libs/asio/example/cpp11/invocation/prioritised_handlers.cpp
./libs/asio/example/cpp11/operations/composed_5.cpp
./libs/asio/example/cpp11/operations/composed_1.cpp
./libs/asio/example/cpp11/operations/composed_3.cpp
./libs/asio/example/cpp11/operations/composed_4.cpp
./libs/asio/example/cpp11/operations/composed_2.cpp
./libs/asio/example/cpp11/echo/blocking_udp_echo_server.cpp
./libs/asio/example/cpp11/echo/blocking_tcp_echo_client.cpp
./libs/asio/example/cpp11/echo/async_tcp_echo_server.cpp
./libs/asio/example/cpp11/echo/async_udp_echo_server.cpp
./libs/asio/example/cpp11/echo/blocking_tcp_echo_server.cpp
./libs/asio/example/cpp11/echo/blocking_udp_echo_client.cpp
./libs/asio/example/cpp11/iostreams/http_client.cpp
./libs/asio/example/cpp11/http/server/reply.hpp
./libs/asio/example/cpp11/http/server/connection.cpp
./libs/asio/example/cpp11/http/server/server.cpp
./libs/asio/example/cpp11/http/server/connection.hpp
./libs/asio/example/cpp11/http/server/reply.cpp
./libs/asio/example/cpp11/http/server/server.hpp
./libs/asio/example/cpp11/spawn/echo_server.cpp
./libs/asio/example/cpp11/spawn/parallel_grep.cpp
./libs/asio/example/cpp11/buffers/reference_counted.cpp
./libs/asio/example/cpp11/timeouts/async_tcp_client.cpp
./libs/asio/example/cpp11/timeouts/server.cpp
./libs/asio/example/cpp11/timeouts/blocking_token_tcp_client.cpp
./libs/asio/example/cpp11/timeouts/blocking_udp_client.cpp
./libs/asio/example/cpp11/timeouts/blocking_tcp_client.cpp
./libs/asio/example/cpp11/futures/daytime_client.cpp
./libs/asio/example/cpp11/nonblocking/third_party_lib.cpp
./libs/asio/example/cpp11/ssl/client.cpp
./libs/asio/example/cpp11/ssl/server.cpp
./libs/asio/example/cpp11/handler_tracking/async_tcp_echo_server.cpp
./libs/asio/example/cpp11/handler_tracking/custom_tracking.hpp
./libs/asio/example/cpp11/multicast/sender.cpp
./libs/asio/example/cpp11/multicast/receiver.cpp
./libs/asio/example/cpp11/timers/time_t_timer.cpp
./libs/asio/example/cpp11/chat/chat_server.cpp
./libs/asio/example/cpp11/chat/chat_client.cpp
./libs/asio/example/cpp11/allocation/server.cpp
./libs/asio/example/cpp11/socks4/socks4.hpp
./libs/asio/example/cpp11/socks4/sync_client.cpp
./libs/asio/example/cpp11/executors/bank_account_1.cpp
./libs/asio/example/cpp11/executors/priority_scheduler.cpp
./libs/asio/example/cpp11/executors/pipeline.cpp
./libs/asio/example/cpp11/executors/actor.cpp
./libs/asio/example/cpp11/executors/fork_join.cpp
./libs/asio/example/cpp11/executors/bank_account_2.cpp
./libs/asio/example/cpp11/local/stream_client.cpp
./libs/asio/example/cpp11/local/iostream_client.cpp
./libs/asio/example/cpp11/local/stream_server.cpp
./libs/asio/example/cpp11/local/connect_pair.cpp
./libs/asio/example/cpp11/fork/daemon.cpp
./libs/asio/example/cpp11/fork/process_per_connection.cpp
./libs/phoenix/example/adapted_echo_server.cpp
./libs/coroutine/doc/motivation.qbk
./libs/coroutine/doc/html/coroutine/motivation.html
./libs/coroutine/doc/coro.qbk
./libs/fiber/doc/asio.qbk
./libs/fiber/doc/integration.qbk
./libs/fiber/doc/fibers.qbk
./libs/fiber/doc/callbacks.qbk
./libs/fiber/examples/asio/autoecho.cpp
./libs/fiber/examples/asio/round_robin.hpp
./libs/fiber/examples/asio/ps/server.cpp
./libs/fiber/examples/asio/ps/publisher.cpp
./libs/fiber/examples/asio/ps/subscriber.cpp
./libs/fiber/examples/asio/exchange.cpp
./libs/thread/test/test_9303.cpp
./libs/process/doc/extend.qbk
./libs/process/doc/tutorial.qbk
./libs/process/doc/autodoc.xml
./libs/process/test/bind_stdout_stderr.cpp
./libs/process/test/spawn.cpp
./libs/process/test/async_system_stackful_except.cpp
./libs/process/test/async_system_stackful.cpp
./libs/process/test/bind_stderr.cpp
./libs/process/test/async_system_future.cpp
./libs/process/test/spawn_fail.cpp
./libs/process/test/async_system_fail.cpp
./libs/process/test/on_exit2.cpp
./libs/process/test/system_test1.cpp
./libs/process/test/async_fut.cpp
./libs/process/test/async_system_stackful_error.cpp
./libs/process/test/system_test2.cpp
./libs/process/test/async_pipe.cpp
./libs/process/test/bind_stdin.cpp
./libs/process/test/bind_stdout.cpp
./libs/process/test/exit_code.cpp
./libs/process/test/async.cpp
./libs/process/test/on_exit.cpp
./libs/process/test/on_exit3.cpp
./libs/process/test/wait.cpp
./libs/process/test/async_system_stackless.cpp
./libs/process/example/io.cpp
./libs/process/example/async_io.cpp
./libs/process/example/wait.cpp
./libs/log/doc/tmp/sinks_reference.xml
./libs/log/src/syslog_backend.cpp
./libs/coroutine2/doc/motivation.qbk
./libs/coroutine2/doc/coro.qbk
./boost/beast/http/span_body.hpp
./boost/beast/http/basic_file_body.hpp
./boost/beast/http/basic_parser.hpp
./boost/beast/http/vector_body.hpp
./boost/beast/http/impl/write.ipp
./boost/beast/http/impl/basic_parser.ipp
./boost/beast/http/impl/fields.ipp
./boost/beast/http/impl/chunk_encode.ipp
./boost/beast/http/impl/serializer.ipp
./boost/beast/http/impl/file_body_win32.ipp
./boost/beast/http/impl/read.ipp
./boost/beast/http/detail/chunk_encode.hpp
./boost/beast/http/buffer_body.hpp
./boost/beast/http/write.hpp
./boost/beast/http/fields.hpp
./boost/beast/http/parser.hpp
./boost/beast/http/basic_dynamic_body.hpp
./boost/beast/http/error.hpp
./boost/beast/http/string_body.hpp
./boost/beast/http/chunk_encode.hpp
./boost/beast/http/serializer.hpp
./boost/beast/http/empty_body.hpp
./boost/beast/http/type_traits.hpp
./boost/beast/http/read.hpp
./boost/beast/core/static_buffer.hpp
./boost/beast/core/buffers_suffix.hpp
./boost/beast/core/buffers_adapter.hpp
./boost/beast/core/impl/flat_buffer.ipp
./boost/beast/core/impl/buffers_adapter.ipp
./boost/beast/core/impl/static_buffer.ipp
./boost/beast/core/impl/read_size.ipp
./boost/beast/core/impl/flat_static_buffer.ipp
./boost/beast/core/impl/buffers_prefix.ipp
./boost/beast/core/impl/multi_buffer.ipp
./boost/beast/core/impl/handler_ptr.ipp
./boost/beast/core/impl/buffered_read_stream.ipp
./boost/beast/core/impl/buffers_suffix.ipp
./boost/beast/core/impl/buffers_cat.ipp
./boost/beast/core/detail/buffers_ref.hpp
./boost/beast/core/detail/bind_handler.hpp
./boost/beast/core/detail/type_traits.hpp
./boost/beast/core/flat_buffer.hpp
./boost/beast/core/bind_handler.hpp
./boost/beast/core/buffers_prefix.hpp
./boost/beast/core/buffers_cat.hpp
./boost/beast/core/buffers_to_string.hpp
./boost/beast/core/type_traits.hpp
./boost/beast/core/buffered_read_stream.hpp
./boost/beast/core/ostream.hpp
./boost/beast/core/flat_static_buffer.hpp
./boost/beast/core/multi_buffer.hpp
./boost/beast/websocket/rfc6455.hpp
./boost/beast/websocket/teardown.hpp
./boost/beast/websocket/impl/write.ipp
./boost/beast/websocket/impl/teardown.ipp
./boost/beast/websocket/impl/ssl.ipp
./boost/beast/websocket/impl/handshake.ipp
./boost/beast/websocket/impl/ping.ipp
./boost/beast/websocket/impl/close.ipp
./boost/beast/websocket/impl/stream.ipp
./boost/beast/websocket/impl/read.ipp
./boost/beast/websocket/impl/accept.ipp
./boost/beast/websocket/detail/mask.hpp
./boost/beast/websocket/detail/pausation.hpp
./boost/beast/websocket/detail/frame.hpp
./boost/beast/websocket/detail/utf8_checker.hpp
./boost/beast/websocket/detail/stream_base.hpp
./boost/beast/websocket/role.hpp
./boost/beast/websocket/stream.hpp
./boost/beast/websocket/ssl.hpp
./boost/beast/experimental/http/icy_stream.hpp
./boost/beast/experimental/http/impl/icy_stream.ipp
./boost/beast/experimental/core/timeout_socket.hpp
./boost/beast/experimental/core/ssl_stream.hpp
./boost/beast/experimental/core/timeout_service.hpp
./boost/beast/experimental/core/impl/timeout_socket.hpp
./boost/beast/experimental/core/impl/timeout_service.ipp
./boost/beast/experimental/core/impl/flat_stream.ipp
./boost/beast/experimental/core/detail/timeout_service.hpp
./boost/beast/experimental/core/detail/impl/timeout_service.ipp
./boost/beast/experimental/core/detail/service_base.hpp
./boost/beast/experimental/core/detail/flat_stream.hpp
./boost/beast/experimental/core/flat_stream.hpp
./boost/beast/experimental/test/impl/stream.ipp
./boost/beast/experimental/test/stream.hpp
./boost/asio/basic_signal_set.hpp
./boost/asio/generic/basic_endpoint.hpp
./boost/asio/generic/seq_packet_protocol.hpp
./boost/asio/generic/raw_protocol.hpp
./boost/asio/generic/detail/impl/endpoint.ipp
./boost/asio/generic/detail/endpoint.hpp
./boost/asio/generic/stream_protocol.hpp
./boost/asio/generic/datagram_protocol.hpp
./boost/asio/io_context_strand.hpp
./boost/asio/buffers_iterator.hpp
./boost/asio/coroutine.hpp
./boost/asio/socket_base.hpp
./boost/asio/signal_set_service.hpp
./boost/asio/basic_raw_socket.hpp
./boost/asio/serial_port_service.hpp
./boost/asio/placeholders.hpp
./boost/asio/completion_condition.hpp
./boost/asio/spawn.hpp
./boost/asio/impl/io_context.ipp
./boost/asio/impl/spawn.hpp
./boost/asio/impl/write.hpp
./boost/asio/impl/buffered_write_stream.hpp
./boost/asio/impl/connect.hpp
./boost/asio/impl/io_context.hpp
./boost/asio/impl/write_at.hpp
./boost/asio/impl/read_until.hpp
./boost/asio/impl/serial_port_base.ipp
./boost/asio/impl/execution_context.ipp
./boost/asio/impl/read_at.hpp
./boost/asio/impl/buffered_read_stream.hpp
./boost/asio/impl/read.hpp
./boost/asio/ts/netfwd.hpp
./boost/asio/use_future.hpp
./boost/asio/basic_serial_port.hpp
./boost/asio/basic_io_object.hpp
./boost/asio/stream_socket_service.hpp
./boost/asio/uses_executor.hpp
./boost/asio/ssl/rfc2818_verification.hpp
./boost/asio/ssl/impl/context.ipp
./boost/asio/ssl/impl/error.ipp
./boost/asio/ssl/impl/context.hpp
./boost/asio/ssl/detail/buffered_handshake_op.hpp
./boost/asio/ssl/detail/impl/engine.ipp
./boost/asio/ssl/detail/impl/openssl_init.ipp
./boost/asio/ssl/detail/engine.hpp
./boost/asio/ssl/detail/stream_core.hpp
./boost/asio/ssl/detail/read_op.hpp
./boost/asio/ssl/detail/write_op.hpp
./boost/asio/ssl/detail/io.hpp
./boost/asio/ssl/detail/openssl_init.hpp
./boost/asio/ssl/context.hpp
./boost/asio/ssl/error.hpp
./boost/asio/ssl/context_base.hpp
./boost/asio/ssl/stream.hpp
./boost/asio/ssl/stream_base.hpp
./boost/asio/datagram_socket_service.hpp
./boost/asio/detail/posix_mutex.hpp
./boost/asio/detail/reactive_socket_service.hpp
./boost/asio/detail/win_static_mutex.hpp
./boost/asio/detail/null_thread.hpp
./boost/asio/detail/buffered_stream_storage.hpp
./boost/asio/detail/null_static_mutex.hpp
./boost/asio/detail/std_static_mutex.hpp
./boost/asio/detail/signal_set_service.hpp
./boost/asio/detail/reactive_wait_op.hpp
./boost/asio/detail/winrt_ssocket_service_base.hpp
./boost/asio/detail/win_iocp_handle_read_op.hpp
./boost/asio/detail/socket_option.hpp
./boost/asio/detail/win_iocp_socket_service_base.hpp
./boost/asio/detail/descriptor_write_op.hpp
./boost/asio/detail/epoll_reactor.hpp
./boost/asio/detail/reactive_socket_recv_op.hpp
./boost/asio/detail/impl/win_iocp_socket_service_base.ipp
./boost/asio/detail/impl/win_event.ipp
./boost/asio/detail/impl/reactive_serial_port_service.ipp
./boost/asio/detail/impl/winrt_timer_scheduler.ipp
./boost/asio/detail/impl/strand_executor_service.ipp
./boost/asio/detail/impl/winrt_ssocket_service_base.ipp
./boost/asio/detail/impl/resolver_service_base.ipp
./boost/asio/detail/impl/win_iocp_serial_port_service.ipp
./boost/asio/detail/impl/win_thread.ipp
./boost/asio/detail/impl/posix_thread.ipp
./boost/asio/detail/impl/scheduler.ipp
./boost/asio/detail/impl/descriptor_ops.ipp
./boost/asio/detail/impl/posix_tss_ptr.ipp
./boost/asio/detail/impl/win_iocp_io_context.ipp
./boost/asio/detail/impl/dev_poll_reactor.hpp
./boost/asio/detail/impl/socket_ops.ipp
./boost/asio/detail/impl/socket_select_interrupter.ipp
./boost/asio/detail/impl/handler_tracking.ipp
./boost/asio/detail/impl/reactive_descriptor_service.ipp
./boost/asio/detail/impl/win_object_handle_service.ipp
./boost/asio/detail/impl/reactive_socket_service_base.ipp
./boost/asio/detail/impl/signal_set_service.ipp
./boost/asio/detail/impl/win_mutex.ipp
./boost/asio/detail/impl/service_registry.ipp
./boost/asio/detail/impl/win_iocp_io_context.hpp
./boost/asio/detail/impl/posix_mutex.ipp
./boost/asio/detail/impl/win_static_mutex.ipp
./boost/asio/detail/impl/win_tss_ptr.ipp
./boost/asio/detail/impl/pipe_select_interrupter.ipp
./boost/asio/detail/impl/select_reactor.ipp
./boost/asio/detail/impl/epoll_reactor.ipp
./boost/asio/detail/impl/strand_service.hpp
./boost/asio/detail/impl/dev_poll_reactor.ipp
./boost/asio/detail/impl/throw_error.ipp
./boost/asio/detail/impl/select_reactor.hpp
./boost/asio/detail/impl/eventfd_select_interrupter.ipp
./boost/asio/detail/impl/win_iocp_handle_service.ipp
./boost/asio/detail/impl/buffer_sequence_adapter.ipp
./boost/asio/detail/impl/winrt_timer_scheduler.hpp
./boost/asio/detail/impl/winsock_init.ipp
./boost/asio/detail/impl/strand_service.ipp
./boost/asio/detail/impl/kqueue_reactor.ipp
./boost/asio/detail/impl/posix_event.ipp
./boost/asio/detail/noncopyable.hpp
./boost/asio/detail/win_iocp_handle_write_op.hpp
./boost/asio/detail/dev_poll_reactor.hpp
./boost/asio/detail/winrt_async_manager.hpp
./boost/asio/detail/handler_invoke_helpers.hpp
./boost/asio/detail/descriptor_ops.hpp
./boost/asio/detail/reactive_socket_send_op.hpp
./boost/asio/detail/win_iocp_socket_accept_op.hpp
./boost/asio/detail/winapp_thread.hpp
./boost/asio/detail/reactive_socket_sendto_op.hpp
./boost/asio/detail/service_registry.hpp
./boost/asio/detail/reactive_socket_service_base.hpp
./boost/asio/detail/winrt_socket_recv_op.hpp
./boost/asio/detail/win_iocp_wait_op.hpp
./boost/asio/detail/posix_static_mutex.hpp
./boost/asio/detail/reactor_op_queue.hpp
./boost/asio/detail/wait_handler.hpp
./boost/asio/detail/winsock_init.hpp
./boost/asio/detail/timer_queue.hpp
./boost/asio/detail/winrt_resolve_op.hpp
./boost/asio/detail/wince_thread.hpp
./boost/asio/detail/conditionally_enabled_mutex.hpp
./boost/asio/detail/descriptor_read_op.hpp
./boost/asio/detail/win_iocp_overlapped_ptr.hpp
./boost/asio/detail/reactive_serial_port_service.hpp
./boost/asio/detail/winrt_ssocket_service.hpp
./boost/asio/detail/handler_alloc_helpers.hpp
./boost/asio/detail/winrt_resolver_service.hpp
./boost/asio/detail/win_iocp_socket_connect_op.hpp
./boost/asio/detail/handler_cont_helpers.hpp
./boost/asio/detail/win_iocp_io_context.hpp
./boost/asio/detail/handler_type_requirements.hpp
./boost/asio/detail/std_mutex.hpp
./boost/asio/detail/win_iocp_socket_recv_op.hpp
./boost/asio/detail/buffer_sequence_adapter.hpp
./boost/asio/detail/string_view.hpp
./boost/asio/detail/resolver_service_base.hpp
./boost/asio/detail/win_iocp_overlapped_op.hpp
./boost/asio/detail/consuming_buffers.hpp
./boost/asio/detail/completion_handler.hpp
./boost/asio/detail/conditionally_enabled_event.hpp
./boost/asio/detail/win_iocp_socket_send_op.hpp
./boost/asio/detail/winrt_utils.hpp
./boost/asio/detail/win_iocp_null_buffers_op.hpp
./boost/asio/detail/reactive_null_buffers_op.hpp
./boost/asio/detail/reactive_socket_accept_op.hpp
./boost/asio/detail/resolve_query_op.hpp
./boost/asio/detail/null_socket_service.hpp
./boost/asio/detail/reactive_descriptor_service.hpp
./boost/asio/detail/win_iocp_handle_service.hpp
./boost/asio/detail/thread_group.hpp
./boost/asio/detail/signal_handler.hpp
./boost/asio/detail/resolver_service.hpp
./boost/asio/detail/reactive_socket_recvmsg_op.hpp
./boost/asio/detail/strand_service.hpp
./boost/asio/detail/is_buffer_sequence.hpp
./boost/asio/detail/win_mutex.hpp
./boost/asio/detail/reactive_socket_connect_op.hpp
./boost/asio/detail/win_iocp_socket_recvmsg_op.hpp
./boost/asio/detail/select_reactor.hpp
./boost/asio/detail/winrt_timer_scheduler.hpp
./boost/asio/detail/win_object_handle_service.hpp
./boost/asio/detail/win_iocp_socket_service.hpp
./boost/asio/detail/scheduler.hpp
./boost/asio/detail/winrt_socket_send_op.hpp
./boost/asio/detail/kqueue_reactor.hpp
./boost/asio/detail/deadline_timer_service.hpp
./boost/asio/detail/null_mutex.hpp
./boost/asio/detail/resolve_endpoint_op.hpp
./boost/asio/detail/handler_tracking.hpp
./boost/asio/detail/win_iocp_socket_recvfrom_op.hpp
./boost/asio/detail/win_iocp_serial_port_service.hpp
./boost/asio/detail/null_reactor.hpp
./boost/asio/detail/winrt_socket_connect_op.hpp
./boost/asio/detail/reactive_socket_recvfrom_op.hpp
./boost/asio/waitable_timer_service.hpp
./boost/asio/write.hpp
./boost/asio/socket_acceptor_service.hpp
./boost/asio/buffered_stream.hpp
./boost/asio/seq_packet_socket_service.hpp
./boost/asio/buffered_write_stream.hpp
./boost/asio/basic_stream_socket.hpp
./boost/asio/connect.hpp
./boost/asio/io_context.hpp
./boost/asio/write_at.hpp
./boost/asio/basic_socket_streambuf.hpp
./boost/asio/buffer.hpp
./boost/asio/basic_seq_packet_socket.hpp
./boost/asio/basic_streambuf.hpp
./boost/asio/async_result.hpp
./boost/asio/ip/basic_endpoint.hpp
./boost/asio/ip/icmp.hpp
./boost/asio/ip/basic_resolver_iterator.hpp
./boost/asio/ip/network_v4.hpp
./boost/asio/ip/impl/basic_endpoint.hpp
./boost/asio/ip/impl/host_name.ipp
./boost/asio/ip/impl/network_v4.hpp
./boost/asio/ip/impl/address_v6.ipp
./boost/asio/ip/impl/address.ipp
./boost/asio/ip/impl/network_v6.ipp
./boost/asio/ip/impl/address_v4.hpp
./boost/asio/ip/impl/address_v4.ipp
./boost/asio/ip/impl/network_v6.hpp
./boost/asio/ip/impl/address.hpp
./boost/asio/ip/impl/network_v4.ipp
./boost/asio/ip/impl/address_v6.hpp
./boost/asio/ip/basic_resolver.hpp
./boost/asio/ip/detail/socket_option.hpp
./boost/asio/ip/detail/impl/endpoint.ipp
./boost/asio/ip/detail/endpoint.hpp
./boost/asio/ip/multicast.hpp
./boost/asio/ip/unicast.hpp
./boost/asio/ip/address_v4.hpp
./boost/asio/ip/udp.hpp
./boost/asio/ip/network_v6.hpp
./boost/asio/ip/basic_resolver_query.hpp
./boost/asio/ip/v6_only.hpp
./boost/asio/ip/address.hpp
./boost/asio/ip/resolver_service.hpp
./boost/asio/ip/tcp.hpp
./boost/asio/ip/basic_resolver_entry.hpp
./boost/asio/ip/basic_resolver_results.hpp
./boost/asio/ip/address_v6.hpp
./boost/asio/posix/stream_descriptor_service.hpp
./boost/asio/posix/descriptor_base.hpp
./boost/asio/posix/stream_descriptor.hpp
./boost/asio/posix/descriptor.hpp
./boost/asio/posix/basic_descriptor.hpp
./boost/asio/posix/basic_stream_descriptor.hpp
./boost/asio/read_until.hpp
./boost/asio/basic_socket_acceptor.hpp
./boost/asio/executor.hpp
./boost/asio/serial_port.hpp
./boost/asio/error.hpp
./boost/asio/basic_datagram_socket.hpp
./boost/asio/read_at.hpp
./boost/asio/thread_pool.hpp
./boost/asio/signal_set.hpp
./boost/asio/windows/stream_handle.hpp
./boost/asio/windows/stream_handle_service.hpp
./boost/asio/windows/basic_handle.hpp
./boost/asio/windows/object_handle_service.hpp
./boost/asio/windows/basic_random_access_handle.hpp
./boost/asio/windows/overlapped_ptr.hpp
./boost/asio/windows/random_access_handle_service.hpp
./boost/asio/windows/random_access_handle.hpp
./boost/asio/windows/overlapped_handle.hpp
./boost/asio/windows/object_handle.hpp
./boost/asio/windows/basic_object_handle.hpp
./boost/asio/windows/basic_stream_handle.hpp
./boost/asio/handler_invoke_hook.hpp
./boost/asio/raw_socket_service.hpp
./boost/asio/experimental/impl/co_spawn.hpp
./boost/asio/experimental/impl/detached.hpp
./boost/asio/experimental/detached.hpp
./boost/asio/basic_deadline_timer.hpp
./boost/asio/execution_context.hpp
./boost/asio/buffered_read_stream.hpp
./boost/asio/basic_socket_iostream.hpp
./boost/asio/is_executor.hpp
./boost/asio/basic_waitable_timer.hpp
./boost/asio/basic_socket.hpp
./boost/asio/deadline_timer_service.hpp
./boost/asio/local/basic_endpoint.hpp
./boost/asio/local/detail/impl/endpoint.ipp
./boost/asio/local/detail/endpoint.hpp
./boost/asio/local/stream_protocol.hpp
./boost/asio/local/datagram_protocol.hpp
./boost/asio/local/connect_pair.hpp
./boost/asio/read.hpp
./boost/process/async.hpp
./boost/process/async_system.hpp
./boost/process/spawn.hpp
./boost/process/detail/async_handler.hpp
./boost/process/detail/posix/sigchld_service.hpp
./boost/process/detail/posix/async_out.hpp
./boost/process/detail/posix/async_pipe.hpp
./boost/process/detail/posix/async_in.hpp
./boost/process/detail/posix/io_context_ref.hpp
./boost/process/detail/traits/async.hpp
./boost/process/detail/windows/async_out.hpp
./boost/process/detail/windows/async_pipe.hpp
./boost/process/detail/windows/async_in.hpp
./boost/process/detail/windows/io_context_ref.hpp
./boost/process/async_pipe.hpp
./boost/process/system.hpp
./boost/process/io.hpp
./boost/log/sinks/syslog_backend.hpp

## 8. Сборка Boost
cd ~/boost_1_69_0
./bootstrap.sh
./b2


## 9. Копирование статических библиотек (*.a) в ~/boost-libs

Надёжный способ (не зависит от ограничения длины командной строки):

mkdir -p ~/boost-libs
cd ~/boost_1_69_0
find . -name "*.a" -type f -exec cp -t ~/boost-libs {} +

## 10. Подсчёт занимаемого места каждым файлом в ~/boost-libs
cd ~/boost-libs
find . -maxdepth 1 -type f -exec du -h {} +

Вывод:

164K    ./libboost_iostreams.a
4.0K    ./libboost_exception.a
4.0K    ./libboost_system.a
52K     ./libboost_timer.a
36K     ./libboost_stacktrace_addr2line.a
208K    ./libboost_prg_exec_monitor.a
1.2M    ./libboost_serialization.a
80K     ./libboost_random.a
776K    ./libboost_wserialization.a
2.2M    ./libboost_test_exec_monitor.a
152K    ./libboost_date_time.a
2.7M    ./libboost_regex.a
16K     ./libboost_stacktrace_basic.a
1.5M    ./libboost_program_options.a
2.0M    ./libboost_locale.a
4.0K    ./libboost_atomic.a
232K    ./libboost_chrono.a
4.5M    ./libboost_wave.a
320K    ./libboost_contract.a
400K    ./libboost_filesystem.a
20K     ./libboost_stacktrace_backtrace.a
232K    ./libboost_fiber.a
824K    ./libboost_graph.a
2.2M    ./libboost_unit_test_framework.a
4.0K    ./libboost_stacktrace_noop.a
20K     ./libboost_context.a
152K    ./libboost_container.a

## 11. Топ-10 самых “тяжёлых” файлов

Корректная сортировка по числам (в килобайтах):

cd ~/boost-libs
find . -maxdepth 1 -type f -exec du -k {} + | sort -rn | head -n 10

Топ-10:

824K	./libboost_graph.a
776K	./libboost_wserialization.a
400K	./libboost_filesystem.a
320K	./libboost_contract.a
232K	./libboost_fiber.a
232K	./libboost_chrono.a
208K	./libboost_prg_exec_monitor.a
164K	./libboost_iostreams.a
152K	./libboost_date_time.a
152K	./libboost_container.a

## Вывод

В ходе лабораторной работы были освоены:

создание и организация каталогов (mkdir, cd, pwd, ls);

работа с переменными среды и PATH (export, echo, source, alias);

скачивание и распаковка архивов (wget, tar, rm, mv);

поиск и подсчёт файлов (find, wc);

поиск по содержимому файлов (grep);

сборка Boost (bootstrap.sh, b2);

анализ размеров файлов (du, sort, head);

публикация отчёта через gist.
