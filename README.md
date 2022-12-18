# single-spa_Angular_React_Vue
Example of single-spa with implementation in Angular, React &amp; Vue

Before start, please execute the following commands in CMD:
mkdir single-spa-example
cd single-spa-example

Step 1: Create single-spa root-config\
Open a new CMD terminal and run **npx create-single-spa**. This command will ask following further details:\
? Directory for new project **main**\
? Select type to generate single-spa root **config**\
? Which package manager do you want to use? **npm**\
? Will this project use Typescript? **Yes**\
? Would you like to use single-spa Layout Engine **Yes**\
? Organization name (can use letters, numbers, dash or underscore) **neworg**

Thats all for creating the initial files for root-config.

Step 2: Create 1st Angular Application - navbar\
Open a new CMD terminal and run **ng new navbar  --routing --prefix navbar --style css & cd navbar & ng add single-spa-angular & cd ..** (Refer Link: https://single-spa.js.org/docs/ecosystem-angular#installation). This command will ask following further details:\
? Would you like to share pseudonymous usage data about this project with the Angular Team at Google under Google's Privacy Policy at https://policies.google.com/privacy. For more details and how to change this setting, see https://angular.io/analytics. **No**\
The package single-spa-angular@7.1.0 will be installed and executed.\
Would you like to proceed? **Yes**\
√ Packages successfully installed.\
? Does your application use Angular routing? **Yes**\
? What port should your project run on? **4200**\
