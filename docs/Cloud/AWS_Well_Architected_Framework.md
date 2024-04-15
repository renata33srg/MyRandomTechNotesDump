# AWS Well-architected Framework

Document was based on 4 main areas: Security, Performance, Reliability and Cost Efectiveness   
Main purposes of the framework is to help customers to:  
- Make informed decisions about the architecture  
- Think in cloud natively way  
- Understand potential impact of design decisions  
		
Furthermore, the framework increases the awareness (consciencia) of general architectural best practices, addresses foundational areas that are often neglected and provides consistent approach to evaluating workload architectures.  

All of that is made based on a set of questions accross five pillars with design principles  


> ## General design principles  
>  
> In a traditional environment there is:
>   - A need to guess how much infrastructure is needed based on high level business requirements and demand (often before a line of code is written)  
>   - Difficulty of reproducing a test environment with the production scale, so new issues can come when systems go to high scale production environment   
>   - Fear of making significant architectural change due to the impossibility of testing and, in case of problems, would stop the delivering of another features because the environments are a single pipeline  
>   - Discouraging of experimentation due to the effort of getting resources to try different things out (manually built and customized are hard to reproduce)  
>  

## 5 Pillars of Well-Architected  
	- [Operational Excellence](#operational)  
	- [Security](#security)  
	- [Reliability](#reliability)  
	- [Performance Efficiency](#performance)  
	- [Cost Optimization](#cost)  



<details>
<summary>Operational Excellence <a name="operational"></a></summary> 

Focuses on:   
- How organization supports the business objectives  
- The ability to run/monitor systems to deliver business value  
- To continually improve supporting processes and procedures  

The focus areas of this pillar are:  
- Organization  
    - Understanding of the organization's priorities, organizational structure and how the organization supports team members (so that team members can support outcomes)  
- Preparation  
    - Designing of the architecture for operations: review of the readiness of workloads and teams (so informed decisions can be made in order to go live or to implement significant change)  
- Operation  
    - Knowledge about the *modus operandi* and the health of the workloads and operation activities: have ability to identify when organizational/business outcomes are at risk and respond appropriately  
- Evolution  
    - Manage processes for continuous improvement of workloads and operation activities: implementing feedback loops, learning from experience, making improvements and sharing what is learned to benefit the entire organization  

</details>

<details>
<summary>Security <a name="security"></a></summary> 

Focuses on:   
- The ability to protect information and systems  

The focus areas of this pillar are:  
- Identity and access management to define **who** can do **what**  
- Detective controls to detect security events  
- Infrastructure proctection to protect systems  
- Data protection to ensure **confidentiality** and **integrity** of data   
- Incident response to respond to security events  

</details>

<details>
<summary>Reliability <a name="reliability"></a></summary> 

Focuses on:  
- The ability to recover from failures  

The focus areas of this pillar are:  
- Meet demand of foundational elements that are around setup/cross-project requirements  
- Workload architecture choices at distributed systems designing process  
- Change management/handling  
- Failure management and recovery strategies  

</details>

<details>
<summary>Performance Efficiency <a name="performance"></a></summary> 

Focuses on:   
- The ability to use IT resources efficiently to meet systems requirements   
- To maintain the efficiency as demand changes and tecnologies evolve

The focus areas of this pillar are:  
- Selection of the right resource types for computing, network, database, storage etc.  
- Review of selection considering that AWS keep innovating with new resource types and features  
- Awareness of resources performance through monitoring  
- Architectural trade-offs to maximize performance efficiency  

</details>

<details>
<summary>Cost Optimization <a name="cost"></a></summary> 

Focuses on: 
- The ability to achieve business outcomes with lowest price point

The focus areas of this pillar are:
- Realizing business value and financial success as optimizing cost and usage with Cloud financial management   
- Controlling and understanding of where the money is being spent with Expenditure and usage awareness
- Selection of cost-effective resources (such spot or reserved instances)  
- Managing demand and supplying resources with autoscaling, caching, queuing etc.  
- Optimizing costs over time by taking advantage of new services and features  

</details>

## Common uses of the framework

- Learn how to build cloud-native architectures  
- Build a backlog  
- As a gating mechanism before production launch  
- Compare maturity of different teams  
- Perform due dilligence (processo aprofundado de estudo, análise e avaliação de informações) for acquisitions   

## Key points

- Make informed decisions about architecture in the cloud and understand the potential impact of those decisions  
- Understand what a cloud-native architecture would look like by leveraging (aproveitando) design principles  
- Questions are the starting point -> Think actively about "what if" and failure scenarios  