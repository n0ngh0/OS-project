# IPC Chatroom System (Functional Programming + Docker)

ระบบแชตแบบกระจาย (Distributed Chatroom) ที่ใช้กลไก Inter-Process Communication (IPC)
ผ่าน Message Queue บน Linux โดยใช้หลัก Functional Programming และสามารถรันบน Docker ได้

รองรับ:
- การสร้างห้อง (JOIN)
- การส่งข้อความสาธารณะ (SAY)
- การส่งข้อความส่วนตัว (DM)
- การดูรายชื่อสมาชิกในห้อง (WHO)

## Project Structure
├── Dockerfile
├── docker-compose.yml
├── Makefile
├── server.cpp
├── router.cpp
├── broadcaster.cpp
├── client.cpp
├── registry.hpp
├── demo_tmux.sh
└── spawn_clients.sh

## Run on Docker
# 1. แตกไฟล์โปรเจกต์
unzip ipc_chat_dockerized.zip
cd ipc_chat_dockerized

# 2. Build image
docker build -t ipc-chat:latest .

# 3. รัน container
docker run --rm -it --name ipc-chat ipc-chat:latest /bin/bash

# 4. ภายใน container พิมพ์
chmod +x demo_tmux.sh (ให้สิทธิ์รันคพสั่ง )
./demo_tmux.sh

# ความหมายของแต่ละช่อง
ขวาบน => Client 1
ขวาล่าง => Client 2
ซ้าย => Server

## Main Commands 
JOIN < room >
เข้าห้องแชต
SAY < room > < message >
ส่งข้อความในห้อง
WHO < room >
ดูรายชื่อในห้อง
DM < client_id > < message >
ส่งข้อความส่วนตัว
