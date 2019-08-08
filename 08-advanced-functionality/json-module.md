<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# JSON Module

JSON = JavaScript Object Notation. It's a series of key-value pairs. The key-value pairs may be nested.

* A data encoding commonly used on the web when interacting with Javascript 
* Sometime preferred over XML because it's less verbose and faster to parse 
* Syntax is almost identical to a Python dict

```text
{
"recipe" : 
    {

    "title" : "Famous Guacomole",

    "description" : "A southwest favorite!",

    "ingredients" : \[

        {"num": "2", "item":"Large avocados, chopped"},

        {"num": "1/2", "units":"C", "item":"White onion, chopped"},

        {"num": "1", "units":"tbl", "item":"Fresh squeezed lemon juice"},

        {"num": "1", "item":"Jalapeno pepper, diced"},

        {"num": "1", "units":"tbl", "item":"Fresh cilantro, minced"}, 

        {"num": "3", "units":"tsp", "item":"Sea Salt"}, 

        {"num": "6", "units":"bottles","item":"Ice-cold beer"} 

    \],      

    "directions" : "Combine all ingredients and hand whisk to desired consistency. Serve and enjoy with ice-cold beers."  

    } 
}
```

* **Parsing a JSON document:**

`import json`

`doc = json.load(open("recipe.json"))`

* **Result is a collection of nested dict/lists:**

`ingredients = doc['recipe']['ingredients']`

`for item in ingredients:`

`# Process item`

`...`

* **Dumping a dictionary as JSON:**

`f = open("file.json","w")`

`json.dump(doc,f)`

**json.dumps\(\) creates a JSON string from the data passed in. It looks like a Python dictionary with quotes around it.**

`>>> import json`

`>>> data = {'foo':1, 'bar':'qwerty'}`

`>>>json.dumps(data)`

`'{"foo": 1, "bar": "qwerty"}'`

`>>> data`

`{'foo': 1, 'bar': 'qwerty'}`

`>>>`

**json.loads\(\) takes a JSON String and makes it onto a dictionary.**

`>>>jsonstr = json.dumps(data)`

`>>> type(json.loads(jsonstr))`

`<type 'dict'>`

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/08-advanced-functionality/struct-module.md" > Continue to Next Topic </a>
