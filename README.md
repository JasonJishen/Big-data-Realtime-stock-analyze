#a full-stack real time stock analyzer web app

Techniques used:
Apache Zookeeper,
Apache Cassandra,
Apache Kakfa,
Apache Mesos,
Redis,
Docker,
NodeJS

project description

for this project, I developed a big data platform to process stock data in real time.Stock data is a time serious data. So I grabed the data from google finance.every record have a last trading time last trading price and last trading currency , and stock simbol for exampleapple. So because time seriers data I have to quickly consume the data, I need to pull it to my system really fast, that's why I choose Apache kafka which is a high performance messaging system. I was able to achieve 200 thousands messages per second. If you count the message and the size of the data it's about 2Tb per day. To store the data, in my use case I choose Apache cassandra which is a highlyscalable peer to peer data storage system. The way I choose cassandra peer to peer failure and has no single point  failure, if one node is dead, I can bring out a new one without hassel. Thirdly we have to process data in real time so we chose apache spark, so I use spark streaming API to wrote a simple algorithm to process data in real time. All those helped me to process data in the data store. Now I need a way to visualize the data. Then we worked on the way how data can present the data to people. So I developed a simple web app using redis, NodeJS, and sockey.io, to render the process result to the web UI. We use NodeJS because it's a very easy to use app. We use socketIO to keep a web socket connection between the client and the server. So I can get the server push the data to client in real time. So you can see the price change in the UI in real time. Lastly, for all the code in my project I packaged them in the docker container and deployed them using Apache Mesos to achieve highly scalable deployment.
