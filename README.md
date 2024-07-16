# Kafka on Windows 🎉

This guide will walk you through setting up Apache Kafka on a Windows machine. 

**Prerequisites:**

- Windows 10 or later
- Java 8 or later


## Steps

1. **Download Kafka** 📥
   - Download the binary file from [Apache Kafka Downloads](https://kafka.apache.org/downloads).

2. **Setup Kafka Directory** 🗂️
   - Create a folder named `Kafka` in your C drive.
   - Unzip the downloaded Kafka binary file into this folder.

3. **Configure Kafka** ⚙️
   - Navigate to the `kafka/config` folder and make the following changes:
     - **server.properties**: Update the `log.dirs` property to `log.dirs=kafka-logs`.
     - **zookeeper.properties**: Update the `dataDir` property to `dataDir=zookeeper_data`.

4. **Start Zookeeper** 🦓
   - Open Command Prompt and navigate to `C:\Kafka`.
   - Run the following command to start Zookeeper:
     ```sh
     .\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
     ```

5. **Start Kafka Server** 🚀
   - Open a new Command Prompt and navigate to `C:\Kafka`., run the following command to start the Kafka server:
     ```sh
     .\bin\windows\kafka-server-start.bat .\config\server.properties
     ```

6. **Create a Kafka Topic** 📝
   - Open a new Command Prompt window and navigate to `C:\Kafka\bin\windows`.
   - Run the following command to create a topic named `test_topic`:
     ```sh
     kafka-topics.bat --create --bootstrap-server localhost:9092 --topic test_topic
     ```

7. **Start Kafka Producer** 🖋️
   - In the same Command Prompt window, run the following command to start the Kafka producer:
     ```sh
     kafka-console-producer.bat --broker-list localhost:9092 --topic test_topic
     ```

8. **Start Kafka Consumer** 📦
   - Open another new Command Prompt window and navigate to `C:\Kafka\bin\windows`.
   - Run the following command to start the Kafka consumer:
     ```sh
     kafka-console-consumer.bat --topic test_topic --bootstrap-server localhost:9092 --from-beginning
     ```

9. **Send and Receive Messages** 💬
   - In the producer Command Prompt window (step 7), start publishing messages.
   - You will see these messages being consumed in the consumer Command Prompt window (step 8).

That's it! You now have Kafka running on your Windows machine, and you can start sending and receiving messages using Kafka topics. 🎊
