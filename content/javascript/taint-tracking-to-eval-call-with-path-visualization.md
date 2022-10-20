{
    "id": "taint-tracking-to-eval-call-with-path-visualization",
    "name": "Taint-tracking to eval call (with path visualization)",
    "date": "{{ .Date }}",
    "language": "javascript",
    "description": "Tracks user-controlled values into 'eval' calls (special case of js/code-injection), and generates a visualizable path from the source to the sink.",
    "author": "LGTM",
    "tags": ["expert", "taint-tracking","javascript"],
    "categories": [],
    "code": "import javascript\nimport DataFlow\nimport DataFlow::PathGraph\nclass EvalTaint extends TaintTracking::Configuration {\n  EvalTaint() { this = \"EvalTaint\" }\n  override predicate isSource(Node node) { node instanceof RemoteFlowSource }\n  override predicate isSink(Node node) { node = globalVarRef(\"eval\").getACall().getArgument(0) }\n}\nfrom EvalTaint cfg, PathNode source, PathNode sink\nwhere cfg.hasFlowPath(source, sink)\nselect sink.getNode(), source, sink, \"Eval with user-controlled input from $@.\", source.getNode(),\n  \"here\"",
    "complexity": "expert"
}