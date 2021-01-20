# The Build, Test, Nuke Pattern
> A Tutorial on Testing Etiquette in the Age of Ephemeral Computing

Nothing lasts forever in the world of ephemeral computing. It’s the nature of the beast. Today, more companies are maximizing their IT budgets by practicing the principles of infrastructure as code (IaC). They’re creating and destroying virtual assets on demand in order to meet the needs of the moment.
Paying only for what you use makes sense technically and financially. IaC offers a lot of benefits, but it does take some getting used to, particularly with regard to resource management.

There’s a certain etiquette involved when a lot of people are using a common set of resources. In a way, being part of an IaC environment is similar to using the laundry room in an apartment building. You need to be aware that other people are using the washers, dryers and folding tables. Thus, you need to keep moving your clothes along from washer to dryer in a timely manner, and you need to clean up after yourself, always.

The same is true in ephemeral computing. There is nothing more irritating than testing on a virtual machine that is all clogged up with useless applications and components left behind from previous tests. Not only do such remnants take up valuable computing resources, but they might also compromise the outcome of your testing. 

When running tests in an ephemeral, IaC environment, a good pattern to follow is one that I call the Build, Test, Nuke pattern. Let’s explore the pattern using an example from a set of unit tests I created in my [Deno demonstration project](https://github.com/reselbob/denodemo) and ran on Travis CI.


## Understanding Build, Test, Nuke

The structure of the Build, Test, Nuke pattern is to divide the testing event into three stages. In the first stage, Build, your testing script gets the source code from a source control management service, such as GitHub, and builds the required dependencies into a deployment unit, such as a Docker container. In the second stage, Test, the script tests the artifact. Then, in the third stage, Nuke, your script destroys the deployment artifacts used in the testing, removing them from both memory and disk. (See figure 1 below.)
