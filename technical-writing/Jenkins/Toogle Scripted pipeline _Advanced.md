## Toogle Scripted pipeline (Advanced)
1. Pipeline is Declarative Pipeline-specific syntax that defines a "block" containing all content and instructions for executing the entire Pipeline.
2. Agent is Declarative Pipeline-specific syntax that instructs Jenkins to allocate an executor (on a node) and workspace for the entire Pipeline.
3. Stage is a syntax block that describes a stage of this Pipeline. Read more about stage blocks in Declarative Pipeline syntax on the Pipeline syntax page. As mentioned above, stage blocks are optional in Scripted Pipeline syntax.
4. Steps is Declarative Pipeline-specific syntax that describes the steps to be run in this stage.
5. Sh is a Pipeline step (provided by the Pipeline: Nodes and Processes plugin) that executes the given shell command.
6. Junit is another Pipeline step (provided by the JUnit plugin) for aggregating test reports.