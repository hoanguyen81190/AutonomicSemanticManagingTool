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
