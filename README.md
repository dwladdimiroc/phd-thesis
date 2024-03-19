# Dynamic adaptation in Stream Processing Systems

Thèse présentée pour l’obtention du grade de Docteur de Sorbonne Université

## Abstract

The amount of data produced by today's web-based systems and applications increases rapidly, due to the many interactions with users (e.g. real-time stock market transactions, multiplayer games, streaming data produced by Twitter, etc.). As a result, there is a growing demand, particularly in the fields of commerce, security and research, for systems capable of processing this data in real time and providing useful information in a short space of time. Stream processing systems (SPS) meet these needs and have been widely used for this purpose. The aim of SPSs is to process large volumes of data in real time by housing a set of operators in applications based on Directed acyclic graphs (DAG).

Most existing SPSs, such as Flink or Storm, are configured prior to deployment, usually defining the DAG and the number of operator replicas in advance. Overestimating the number of replicas can lead to a waste of allocated resources. On the other hand, depending on interaction with the environment, the rate of input data can fluctuate dynamically and, as a result, operators can become overloaded, leading to a degradation in system performance. These SPSs are not capable of dynamically adapting to operator workload and input rate variations.
One solution to this problem is to dynamically increase the number of resources, physical or logical, allocated to the SPS when the processing demand of one or more operators increases.

This thesis presents two SPSs, RA-SPS and PA-SPS, reactive and predictive approach respectively, for dynamically modifying the number of operator replicas. The reactive approach relies on the current state of operators computed on multiple metrics, while the predictive model is based on input rate variation, operator execution time, and queued events. 
The two SPSs extend Storm SPS to dynamically reconfigure the number of copies without having to downtime the application. They also implement a load balancer that distributes incoming events fairly among operator replicas.

Experiments on the Google Cloud Platform (GCP) were carried out with applications that process Twitter data, DNS traffic, or logs traces. Performance was evaluated with different configurations and the results were compared with those of running the same applications on the original Storm as well as with state-of-the-art work such as SPS DABS-Storm, which also adapt the number of replicas. The comparison shows that both RA-SPS and PA-SPS can significantly improve the number of events processed, while reducing costs.