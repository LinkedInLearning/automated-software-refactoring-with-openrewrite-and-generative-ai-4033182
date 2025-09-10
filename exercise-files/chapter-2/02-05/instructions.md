# Demo: Applying OpenRewrite to refactor Java code using the CLI

Quick reference: https://docs.moderne.io/user-documentation/moderne-cli/cli-reference/

## Introduction to the functionality of the recipe

1. Open the recipe documentation in browser: ["Add license header"](https://docs.openrewrite.org/recipes/java/addlicenseheader)
2. Inspect the functionality
3. Look through the options

## Short rundown of example GitHub repository

1. Open example Git repositories in the browser
    - [https://github.com/bmuschko/camel-spring-boot-examples](https://github.com/bmuschko/camel-spring-boot-examples)
    - [https://github.com/bmuschko/spring-boot-web-thymeleaf](https://github.com/2019SP93022/spring-boot-web-thymeleaf)
2. Show different modules
3. Show one source file with a license header ([AmqpConfig.java](https://github.com/bmuschko/camel-spring-boot-examples/blob/main/amqp/src/main/java/sample/camel/AmqpConfig.java))
4. Show one source file with a missing license header ([DataSourcesConfig.java](https://github.com/bmuschko/camel-spring-boot-examples/blob/main/multi-datasource-2pc/src/main/java/sample/camel/DataSourcesConfig.java))

## Show operations from the Moderne CLI

1. Clone the GitHub repository
    - `git clone git@github.com:bmuschko/camel-spring-boot-examples.git`
    - `git clone git@github.com:bmuschko/spring-boot-web-thymeleaf.git`
2. Build the LST: `mod build .`
3. Install the recipe JAR: `mod config recipes jar install org.openrewrite:rewrite-java:latest`
4. Run the recipe: `mod run . --recipe AddLicenseHeader --recipe-option "licenseText=Copyright ${CURRENT_YEAR} the original author or authors..."`

## Show data tables

1. Inspect the recipe run stats: `mod study . --last-recipe-run --data-table RecipeRunStats`
2. Inspect the source file results data table: `mod study . --last-recipe-run --data-table SourcesFileResults`

## Apply the changes, open a pull request

1. Apply the patch: `mod git apply . --last-recipe-run`
2. Create a new branch: `git branch bm/license`
3. Checkout the branch: `git checkout bm/license`
4. Commit changes: `git commit . -m "Add license header"`
5. Push the changes to the branch: `git push origin bm/license`
6. Show how to create a pull request for the changes.
