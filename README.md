# AutonomicSemanticManagingTool

Autonomic Semantic Managing Tool is a tool that sup

[Autonomic Orchestration](https://github.com/anlam/AutonomicOrchestration/tree/java-spring-version) is a supporting core system for [Arrowhead Framework](https://github.com/eclipse-arrowhead/core-java-spring). The core system creates a control loop that enables local clouds to adapt with dynamicity at run-time. The control loop constantly monitors the local clouds via data retrieved from other core systems. It then does reasoning based on information from its knowledge based to decide which adaptation policy should be deployed. 
![alt text](https://github.com/hoanguyen81190/AutonomicSemanticManagingTool/blob/main/figures/semantic extraction.PNG)
Knowledge based contains semantic information of the local clouds and is hand-crafted by experts of the local clouds, thus it becomes the bottleneck of the systems. The role of this tool is to automate semantic extraction from system specifications.
![alt text](https://github.com/hoanguyen81190/AutonomicSemanticManagingTool/blob/main/figures/overal.PNG)

The tool is under research and development process. The two proposal approaches are shown in the Figure below

![alt text](https://github.com/hoanguyen81190/AutonomicSemanticManagingTool/blob/main/figures/approaches.PNG)

## Generate Knowledge graph from UML models
The first approach is to generate knowledge graph from UML models of the systems. There are several available existing tools that support the process. The downside of this approach is that it relies on the UML models of the systems which need to be hand-crafted, which adds an extra step before knowledge graph is generated. Moreover, UML models often do not capture all the semantic meaning, knowledge graph thus needs to be editted post-processing. 

## Generate Knowledge graph from natural language using Neural Machine Translation
The tool takes input a as a text specifications of the system written in natural language. Example 
> The towers shall be equipped with an overflow alarm to prevent overflow of the sump in case of makeup water valve failure.
and output a knowledge graph representation of the text
![alt text](https://github.com/hoanguyen81190/AutonomicSemanticManagingTool/blob/main/figures/example_knowledge_graph.PNG)

Specifications are first handled by an NLP model to extract Entities. The output of the Entity Detection model is combined with the original text as input for the second NLP model to extract Relations between Entities. 
![alt text](https://github.com/hoanguyen81190/AutonomicSemanticManagingTool/blob/main/figures/pipeline.PNG)

The NLP models are two [BERT](https://arxiv.org/abs/1810.04805) model which are fine tuned to detect Entities and Relations. BERT is the state-of-the-art of Neural Machine Translation models. It includes the encoder block of the Transformer model and has been pretrained on a large corpus of text. For different purpose, the pre-trained BERT is fine-tuned by training with a small dataset represent the specific problem. 
For the first proof-of-concept, the tool will be applicable on systems of sensors and actuators. The ontology schemes in used are [https://www.w3.org/TR/rdf-schema/](https://www.w3.org/TR/vocab-ssn/#SSNStimulus) and [SOSA](https://www.w3.org/TR/vocab-ssn/#SSNStimulus). We will use a subset of SOSA ontology. The Entity class that can be detected by BERT are:
> 
> I-SEN #sosa:Sensor
> 
| Entity class      | Ontology Mapping |
| ----------- | ----------- |
| B-SEN |sosa:Sensor      |
| B-STI |ssn:Stimulus
> I-STI |ssn:Stimulus
> B-ACT |sosa:Actuator
> I-ACT |sosa:Actuator
> B-ACTPROB |sosa:ActuatableProperty
> I-ACTPROB |sosa:ActuatableProperty
> B-PLAT |#sosa:Platform
> I-PLAT |sosa:Platform
> O        | None
The tokenization of the examble for the Entity Detection mode is:
> O B-Plat  O O O O O B-Prop B-Sen O O O O O O O O O O B-Prop B-Act O

Dataset is collected from the internet with the keywords: smart-house
