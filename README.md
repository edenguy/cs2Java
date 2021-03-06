# cs2Java
This project ports a C# (CSharp) cs data model (all classes from any given assembly), to a Java package, using YAML as a bridge.

CSharp => YAML => .java

As this process is reflection based, it's automated, and thus minimizes the chance for typos and bugs in the process of porting of the code from one framework to another.


The project contains three solutions:


1. Reflector2YAML
The intention is to take a cs data model (schema) (CS classes) that are used as a data model for serializing JSON.
This tool can work on any assembly.  Whether we have the source code for this assembly or not.
The data model is analyzed via reflection, analyzing class names, inheritence, JsonProperties.
Generating YAML representing the cs schema, as the json serializer sees it.
This cs solution comes with a SampleAssembly.
INPUT:  Any CS assembly (to be analyzed/reflected)
OUTPUT: cs2Java/YAMLParser/dataModel.yaml

2. YAMLParser
Java code that uses the YAML file (output of Reflector2YAML) as input, and spits out java code corresponding to the C# reflected tyeps
INPUT: cs2Java/YAMLParser/dataModel.yaml
OUTPUT: Model/src/main/java/Model/Autogenerated/


3. Model
Auto generated JAVA code from the YAMLParser output.
This is the final java artifact, which represents the C# data model.
It contains a couple of custom date serializers, and once YAMLParser runs, it will get populated with the auto generated model in Model/src/main/java/Model/Autogenerated/
