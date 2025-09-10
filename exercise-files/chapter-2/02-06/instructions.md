# Demo: Refactor Java code with OpenRewrite using the Maven

Quick reference: https://docs.openrewrite.org/reference/rewrite-maven-plugin

## Setting up the `rewrite.yml` file

1. Create file `rewrite.yml` in the project root directory
2. In a browser, show the [code snippet](https://docs.openrewrite.org/recipes/java/addlicenseheader#usage) needed for the recipe
3. Explain that you need it because there’s no CLI option to pass a recipe option value
4. Copy [contents into file](./rewrite.yml)
5. Save file

## Running the `dryRun` command

1. Run the command to execute the recipe: `mvn org.openrewrite.maven:rewrite-maven-plugin:dryRun -Drewrite.activeRecipes=com.bmuschko.AddLicenseHeader`
2. Show the patch file, by default under `target/rewrite/rewrite.patch`
3. Render the files to be changed: `git apply --stat target/rewrite/rewrite.patch`

## Show data tables

1. Generate the data tables: `mvn org.openrewrite.maven:rewrite-maven-plugin:dryRun -Drewrite.activeRecipes=com.bmuschko.AddLicenseHeader -Drewrite.exportDatatables=true`
2. Inspect the data tables in the directory: `tree target/rewrite/datatables`
3. Open `SourcesFileResults.csv`, e.g. via `open target/rewrite/datatables/2025-09-02_18-42-01-057/org.openrewrite.table.SourcesFileResults.csv`

## Apply the changes, open a pull request

1. Apply the patch: `mvn org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.activeRecipes=com.bmuschko.AddLicenseHeader`
2. Create a new branch: `git branch bm/license`
3. Checkout the branch: `git checkout bm/license`
4. Commit changes: `git commit . -m "Add license header"`
5. Push the changes to the branch: `git push origin bm/license`
6. Show how to create a pull request for the changes
