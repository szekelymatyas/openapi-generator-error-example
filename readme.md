# How to run

openapi-generator-cli generate -i --generator-key angular-client

# Schema definition

```

#./swagger.json
"schemas": {
"Example": {
"type": "object",
"required": ["value"],
"properties": {
"value": {
"type": "string",
"nullable": true
}
}
},
"Example2": {
"type": "object",
"required": ["value2"],
"properties": {
"value2": {
"$ref": "#/components/schemas/Example",
"nullable": true
}
}
}
```

# Results

```
#./generated-angular-client/model.example.ts
export interface Example {
    value: string | null;
}


#./generated-angular-client/model.example2.ts
export interface Example2 {
    value2: Example;
}

```

# My expectation

```
#./generated-angular-client/model.example.ts
export interface Example {
    value: string | null;
}


#./generated-angular-client/model.example2.ts
export interface Example2 {
    value2: Example | null; <=== null here
}

```
