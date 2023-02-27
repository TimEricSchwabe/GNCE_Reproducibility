# Reproducibility for "Cardinality Estimation over Knowledge Graphs with Embeddings and Graph Neural Networks"

This repository contains the raw data-files(graphs and queries) used for training and evaluating the different
methods in the paper "Cardinality Estimation over Knowledge Graphs with Embeddings and Graph Neural Networks".

The raw data can be found under https://drive.google.com/drive/folders/1figNweDOki9oGwVPZFu9GzrVjUlC1hrz?usp=sharing

The implementation of GNCE can be found under: https://github.com/TimEricSchwabe/GNCE <br>
<br>
The structure is as follows:
```
/Data
    /<dataset_name>
        /graph  
            /<graph_name>.ttl # The graph in .nt ot .tt. format
        /star
            /Joined_Queries.json # The used star queries
        /path
            /Joined_Queries.json  # The used path queries
        stastics.zip # Compressed folder contating the embeddings for the entities in the queries
        /Results
             /path
                 /Joint_Model # predicted and true cardinality for path queries
                 execution_time # Execution Times for the learned methods
                 /g-care # The raw results obtained by g-care
             /star
                /Joint_Model # predicted and true cardinality for star queries
                execution_time # Execution Times for the learned methods
                /g-care # The raw results obtained by g-care
```

The queries are in the following format:
```
{"x": ["http://example.org/entity1", ...], "y":4, 
"query": ["SELECT * WHERE..."], 
"triples": [["http://example.org/entity1", "http://example.org/predicate1", "http://example.org/entity2"], ...]}
```
}
<br>
Here, "x" is the list of entities that are part of the query, "y" is the cardinality of the query,
"query" is the SPARQL query, and "triples" is the list of triples that are part of the query.<br>


In order to convert the .ttl files into the format required by G-Care and LSS, we create
the vertices from all entities in the .ttl file, and add types according to the 
rdf:type edges. We add all triples in the graph as edges to the G-Care file. That can be
found in ``RDF_to_Gcare.ipynb``.




## Bar- and Boxplots

The bar- and boxplots from the paper can be reproduced with the Notebook ```Statistics and Plotting.ipynb```.
Inside, the dataset and query_type can be set accordingly.

## Scatterplots

The scatterplots can be reproduced using ```Scatterplot.ipynb```.

## Execution Times

The plots for the execution times can be reproduced using ```Evaluation Times.ipynb```.
