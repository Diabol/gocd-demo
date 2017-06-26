GoCD Demo
========================

This projects contains a self-contained demo environment for [GoCD](https://www.gocd.org/). It uses Docker to bring up a GoCD server and one GoCD build agent.

Requirements
---
Docker (tested with version 17.03.1-ce, build c6d412e)

Start
---
    docker-compose up

Usage
---
Browse to http://localhost

![alt tag](https://raw.githubusercontent.com/Diabol/gocd-demo/master/docs/gocd_1_startup.png)

Use the wizard to create an example pipeline. You could for instance use Git as the version control system and use this repository to checkout. As build task you can select "custom command" and just use "echo" as the command with "an arbitrary string" as argument just to create something simple to run.

![alt tag](https://raw.githubusercontent.com/Diabol/gocd-demo/master/docs/gocd_2_pipeline_setup.png)

To enable the agent, browse to http://localhost/go/agents, check the checkbox next to the agent and select "Enable".

Go to the pipeline view at http://localhost/go/pipelines and make sure the pipeline is enabled (unpaused). Click the play button to run the pipeline!

![alt tag](https://raw.githubusercontent.com/Diabol/gocd-demo/master/docs/gocd_3_green_pipeline.png)

You can also programmatically add pipeline configurations, e.g.

    curl -X POST http://localhost/go/api/admin/pipelines -H 'Accept: application/vnd.go.cd.v4+json' -H 'Content-Type: application/json' -d @example-pipeline.json
