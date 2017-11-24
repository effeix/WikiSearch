# WikiSearch

WikiSearch is a simple search engine for Wikipedia articles

## Project Details
### Why?
The goal of this project is to provide a simple and powerful way to search for Wikipedia articles across the web, while also helping us to learn about the basics and strategies used by the biggest search engines.

### Technologies
To build a fast and resilient search engine we used a modern concept of distributed computing: [Apache Spark](https://spark.apache.org/). Along with Spark we used [MongoDB](https://www.mongodb.com/) as our storage service, simply because it provides the possibility of distributed storage and we prefer working with a [NoSQL](https://aws.amazon.com/nosql/?nc1=h_ls) database. Apache Zeppelin (https://zeppelin.apache.org/) was used as our main development tool, since it provides a spark-ready environment and an interative notebook as soon as it is downloaded. [Python3](https://www.python.org/) was used as the backend language, with [PySpark](https://pypi.python.org/pypi/pyspark), a python module for working with Spark.

To deploy our search engine as a service, we used [AWS (Amazon Web Services)](https://aws.amazon.com/) and [MongoDB Atlas](https://www.mongodb.com/cloud/atlas), a tool to create MongoDB-ready clusters inside AWS without worrying about configuration.

- Images (apache spark, mongodb, zeppelin, python3, aws)

### Project Schematic

- Add schematic

### Using WikiSearch
##### Currently, WikiSearch only works in Linux operating system. The instructions below are specific to Ubuntu/Debian Linux.

##### Setup Python
1. Install Python 3 if not already installed: ```$ sudo apt install python3.6``` (16.10+).
2. Install [PIP](https://pypi.python.org/pypi/pip) for Python 3 if not already installed: ```$ sudo apt install python3-pip```. 
3. Install PySpark: ```$ sudo pip3 install pyspark```.

##### Setup MongoDB
```
$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6

$ echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list

$ sudo apt update

$ sudo apt install -y mongodb-org
```

##### Setup Apache Zeppelin
1. Download [Apache Zeppelin 0.7.3](http://www.apache.org/dyn/closer.cgi/zeppelin/zeppelin-0.7.3/zeppelin-0.7.3-bin-all.tgz) and extract it to the desired folder using ```$ tar -xzvf <file>```. Zeppelin will be ready to use.
2. Go to the newly created directory (after extraction) using ```$ cd <directory>```.
3. Extract the necessary environment variables: ```$ extract PYSPARK_PYTHON=python3``` and ```$ extract PYSPARK_DRIVER_PYTHON=python3```. If you want to make this permanent, add the two lines to ```~/.bashrc```.
4. Start Apache Zeppelin: ```$ bin/zeppelin-daemon.sh start```. Zeppelin will be running under http://localhost:8080. To stop the server use ```$ bin/zeppelin-daemon.sh stop```.

##### Usage
Start the Zeppelin server and go to http://localhost:8080. Click on _**Import note**_ and select the Notebook in this git (WikiSearch.json). Open the Notebook and type the query in the first cell, replacing "big data". Run all cells. The result is a ranked list of the most relevant documents.
