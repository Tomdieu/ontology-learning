
# Sparql query for the foodHealth.owl

- This SPARQL query is designed to retrieve the names of foods and the names of health problems associated with those foods, based on the consumption habits and experiences of individuals defined in an ontology. Here's a step-by-step explanation:

    ```sparql
    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX fa: <http://www.semanticweb.org/ivantom/ontologies/2024/6/untitled-ontology-3#>

    SELECT ?foodName ?healthProblemName
    WHERE
    {
    ?person rdf:type fa:Person ;
            fa:personName ?personName ;
            fa:experience ?healthProblem ;
            fa:eats ?food .

    ?food rdf:type fa:Food ;
            fa:foodName ?foodName .

    ?healthProblem rdf:type fa:HealthProblem ;
                    fa:healthProblem ?healthProblemName .
    }
    ```

- This sparql query seach or all foods ,the health problems associated ordered by the food name in descending order and the limit the results to the first 10 starting the list at position 10

    ```sparql
    PREFIX rdf:<http://www.w3.org/1999/02/22-rdf-syntax-ns#>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    PREFIX fa: <http://www.semanticweb.org/ivantom/ontologies/2024/6/untitled-ontology-3#>

    SELECT ?foodName ?healthProblemName
    WHERE {
        ?person rdf:type fa:Person;
                fa:eats ?food;
                fa:experience ?healthProblem .
        ?food rdf:type fa:Food;
                fa:foodName ?foodName .
        ?healthProblem rdf:type fa:HealthProblem ;
                fa:healthProblem ?healthProblemName .
    }
    LIMIT 10
    OFFSET 9
    ```
