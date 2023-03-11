---
title: Java Networking Programming
date: 2023-03-11 11:39:08 -0500
categories: [java, networking programming]
tags: [java network] # TAG names should always be lowercase
---

## What is Socket (Transport Layer)

A socket is a **communication endpoint** that allows two computers to communicate with each other over a network. It is an abstraction provided by the operating system to represent a **network connection**.

Sockets can be used to communicate **between different processes running on the same computer, or between processes running on different computers over a network**. The socket provides a reliable, **bi-directional** communication channel for exchanging data between the two endpoints.

The socket interface is typically provided by the operating system as a set of system calls that allow applications to **create, connect, send, and receive data** over a network. There are different **types of sockets**, such as **TCP** (Transmission Control Protocol) sockets, which provide a reliable, ordered, and error-checked stream of data, and **UDP** (User Datagram Protocol) sockets, which provide an unreliable, unordered, and faster way to send and receive data.

Sockets are used extensively in network programming for implementing **client-server architectures**, where one computer (the server) provides services to other computers (the clients) over a network. Sockets are also used in **peer-to-peer networks and other distributed systems**.

## UDP Communication

### Send Data

```java
public class SendDemo {
    public static void main(String[] args) {
        // 創建發送端的socket對象
        // DatagramSocket()構造數據報套接字並將其綁定到主機上的任何可用端口
        DatagramSocket ds = new DatagramSocket();
        // 創建數據包，並打包
        byte[] bys = "Hello, world!".getBytes();
        DatagramPacket packet = new DatagramPacket(bys, bys.length, InetAddress.getByName("192.168.1.66",10086));
        // send data
        ds.send(packet);
        ds.close();
    }
}
```

### Receive Data

```java
public class ReceiveDemo {
    pubic static void main(String[] args) {
        // 創建接收端Socket對象，並綁定主機指定端口
        DatagramSocket ds = new DatagramSocket(10086);
        // receive data
        byte[] bys = new byte[1024];
        DatagramPacket dp = new DatagramPacket(bys, bys.length);
        ds.receive(dp);
        // output data
        System.out.println("Data: " + new String(dp.getData(), 0, dp.getLength()));
        // 釋放資源
        ds.close();
    }
}
```

## TCP Communication

### Send Data

```java
public class ClientDemo {
    public static void main(String[] args){
        // create client-side Socket object
        Socket clientSocket = new Socket(InetAddress.getByName("127.0.0.1"),10086)
        // 獲取輸出流，寫數據
        OutputStream os = clientSocket.getOutputStream();
        os.write("Hello World".getBytes());
        // 釋放資源
        os.close();
    }
}
```

### Receive Data

```java
public class ServerDemo {
    public static void main(String[] args){
        // create server-side Socket object
        ServerSocket ss = new ServerSocket(10086);
        // detect and get the client-side Socket object
        Socket s = ss.accept();
        // get inputstream and read data
        InputStream is = s.getInputStream();
        byte[] bys = new byte[1024];
        int len = is.read(bys);
        String data = new String(bys, 0, len);
        System.out.println(data);

        // 釋放資源
        s.close();
        ss.close();
    }
}
```
