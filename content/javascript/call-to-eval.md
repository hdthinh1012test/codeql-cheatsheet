{
"id": "call-to-eval",
"name": "Call to Eval",
"date": "2022-10-20T13:10:11+07:00",
"language": "javascript",
"description": "Finds function calls of the form `eval(...)`",
"author": "LGTM",
"tags": ["pattern","javascript","basic"],
"categories": [],
"code": "import javascript\nfrom CallExpr c\nwhere c.getCalleeName() = \"eval\"\nselect c",
"complexity": "basic"
}