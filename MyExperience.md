#My experience and further notes

Put here general information about the steps you took, what you liked, disliked, why did you do X instead of Y and so on.

## Azure Storage Account

I haven't worked a lot with storage, but the questions I would send back would be;

- What should be the storage name? It has to have an unique name;

- Does it need to have new RG or should be used in existing one? Microsoft advises to use seperate RG for storage.

- What kind of data is it? This is important to decide what type of storage is necessery for the data.
If its general data Standard storage is enough. Premium storage is more focused on VM workloads with high IO. Think about big data and data warehousing. This is also important for the price indication. 

- Next question would be how the data should be accessed? Only by specific IP range of for everyone / by HTTP or HTTPS? This is important so you know how to secure it. This can be done within storage account with Access key, SAS, AAD(Rbac) and firewall.

- How quick should data be accessed? This question is also important for replication of storage. Which brings me to next question; How should the data be replicated? 

For his logging problem I would suggest him to use diagnostic logging within Azure App service. Here he can enable logging for the .Net application on filesystem or blob. Or even both.



## VNet-to-VNet

For setting up the 2 vNETS I would ask the architects for the following information;

- What names should the vNETs have?
- In what Resource Group should they be manifested? 
- What should the address space be? 
- What subnets should they have?
- In what location should the vNETS be created?
- What DNS servers do they need to use?
- ddos protection plan? 
- Eventual tags what needs to be created?


For connecting 2 vnets we need to give them both unique public IP adres. This can be done by searching Azure Marktplace for "public IP address". Then after configuring them, we also need to create VN Gateways. Also these can be found in azure marketplace. After configuring and selecting the Virtual Networks + Public IP's, we only need to make connection.

This can be made by searching the azure marketplace for Networking and then selecting "Connection". Here you can select different connections, in this case its vNET to vNET. Give it a name and select 1st and 2nd vnet that need to communicate with eachother. After that you need to give it shared key(used when connecting vnets with eachother), select the Resource Group(or make new one) and click on create to establish the connection.



### Application Gateway

I have not worked with Application Gateway yet, so I realy would not know what the best cases would be. Of course I would be happy to develop myself in this part if necessary. 

