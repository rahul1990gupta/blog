Title: The rise of micro-tools
Date: 2024-10-20 10:20
Category: Software Engineering
Slug: micro-tools
Authors: Rahul Gupta
Summary: Last decade has been a time where “big data“ tools came out every day. benchmarks were released boasting of throughputs and low latency numbers. Little attention was paid to operating costs to run these systems and expertise required to operate these systems. Running these systems was tricky with no tools to manage these systems effectively. Our spark cluster will go down with no warning. Every morning we will come to office to find that spark cluster was dead and no jobs were run last night. SaaS and hyperscaler came to rescue. Don’t worry about operating costs and maintenance costs, but don’t you dare to leave us. :) Often these services come with vendor lock-in.

Last decade has been a time where “big data“ tools came out every day. benchmarks were released boasting of throughputs and low latency numbers. Little attention was paid to operating costs to run these systems and expertise required to operate these systems. Running these systems was tricky with no tools to manage these systems effectively. Our spark cluster will go down with no warning. Every morning we will come to office to find that spark cluster was dead and no jobs were run last night. SaaS and hyperscaler came to rescue. Don’t worry about operating costs and maintenance costs, but don’t you dare to leave us. :) Often these services come with vendor lock-in.

Now, we are seeing some good tools being developed to “Big Data“ right from your good old laptop. Here we are going to take a look at some of these tools

DuckDB: Sqlite’s OLAP cousin

Duckdb has everything that made sqlite most used database in the world.

- Embeddable: no need for data to leave the process. it can perform zero-copy query on data stored in pandas Dataframe. No more writing obscure apply commands on Dataframe. You can write plain SQL to run on Dataframe. It has also been used as a plugin to postgresql to run OLAP queries. Written in plain C++ with no dependencies, it compiles to two file: .h interface file and .cpp containing and functions. Very lightweight. Also database lives in a single file just like sqlite DB. Since it can also run in browser with wasm, it will be an intetgral piece of software powering interactive analytics. No roundtrip to servers.

- Scalability: SSDs are getting cheaper and faster. 1 TB SSD drive costs 50 USD. With few thousand dollars, you could easily store 100TB of data. This is more data than most enterprises have barring google. Many major publicly traded companies have less tabular structured data than this. DuckDB has been tested to work well with 20-30 TB of data.

- No Lock-in. This Netherlands government university funded project and maintainers have indicated that they want to keep it this way. Nonetheless, project is open-source with a permissive MIT license.

<p align="center">
<img src="{static}/images/OSS_Stars.png">
</p>

GGML: Run LLM model locally

After SSD paper and model were released, YOLO model was released and became instant hit among computer vision enthusiasts. While SSD could only run with large deep learning frameworks(TF, Pytorch), darknet YOLO came with no dependecies and could be compiled with a plan C++ compiler and could run on CPU machine.

Same thing happened when whisper and llamm model weights were released by OpenAI and Meta. A little know developer(Georgi Gergano) from Bulgaria released llama.cpp and whisper.cpp . Since then they have written wrapper around many other models such as BioGPT, Yolo. This lower level C++ lib serves as a foundation for Ollama.

Kùzu: graph database Cousin of sqlite

Developed and maintained by Semih Salihoğlu, a professor at University of Waterloo. They have now incorporated a company KuzuDB inc with his students. Their team is powering its development. It uses cypher(same language used by Neo4J) to query the database. This db is embeddable and can be used in a process. See the video below to get an overview what Kuzu has to offer.

<p>
<iframe width="560" height="315" src="https://www.youtube.com/embed/BksVyv5864k?si=1IEa5-tCll9bRafq" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</p>
