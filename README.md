# single-spa_Angular_React_Vue
Example of single-spa with implementation in Angular, React &amp; Vue

Before start, please execute the following commands in CMD:
mkdir single-spa-example
cd single-spa-example

**Step 1**: Create single-spa root-config\
Open a new CMD terminal and run **npx create-single-spa**. This command will ask following further details:\
? Directory for new project **main**\
? Select type to generate single-spa root **config**\
? Which package manager do you want to use? **npm**\
? Will this project use Typescript? **Yes**\
? Would you like to use single-spa Layout Engine **Yes**\
? Organization name (can use letters, numbers, dash or underscore) **neworg**

Thats all for creating the initial files for root-config.

**Step 2**: Create 1st Angular Application - navbar\
Open a new CMD terminal and run **ng new navbar  --routing --prefix navbar --style css & cd navbar & ng add single-spa-angular & cd ..** (Refer link: https://single-spa.js.org/docs/ecosystem-angular#installation). This command will ask following further details:\
? Would you like to share pseudonymous usage data about this project with the Angular Team at Google under Google's Privacy Policy at https://policies.google.com/privacy. For more details and how to change this setting, see https://angular.io/analytics. **No**\
The package single-spa-angular@7.1.0 will be installed and executed.\
Would you like to proceed? **Yes**\
√ Packages successfully installed.\
? Does your application use Angular routing? **Yes**\
? What port should your project run on? **4200**

Thats all for creating the initial files for app-parcel - navbar.

**Step 3**: Create 2nd Angular Application - default\
Open a new CMD terminal and run **ng new default  --routing --prefix default --style css & cd default & ng add single-spa-angular & cd ..** with providing same input mentioned in step 2 except following one:\
? What port should your project run on? **4300**

Thats all for creating the initial files for app-parcel - default.

**Step 4**: Create 3rd Angular Application - module01\
Open a new CMD terminal and run **ng new module01  --routing --prefix module01 --style css & cd module01 & ng add single-spa-angular & cd ..** with providing same input mentioned in step 2 except following one:\
? What port should your project run on? **4400**

Thats all for creating the initial files for app-parcel - module01.

**Step 5**: Create 1st React Application - module02\
Open a new CMD terminal and run **create-single-spa --framework react**. This command will ask following further details:\
? Directory for new project **module02**\
? Which package manager do you want to use? **npm**\
? Will this project use Typescript? **Yes**\
? Organization name (can use letters, numbers, dash or underscore) **neworg**\
? Project name (can use letters, numbers, dash or underscore) **module02**

Thats all for creating the initial files for app-parcel - module02.

**Step 6**: Create 1st Vue Application - module03\
Open a new CMD terminal and run **create-single-spa --framework vue**. This command will ask following further details:\
? Directory for new project **module03**\
? Organization name (can use letters, numbers, dash or underscore) **neworg**

Thats all for creating the initial files for app-parcel - module03.

**Step 7**: Update **app-routing.module.ts** and **app.module.ts** for angular projects - navbar, default and module01 (Refer link: https://single-spa.js.org/docs/ecosystem-angular/#routing)\
Open app-routing.module.ts and add providers: **[{ provide: APP_BASE_HREF, useValue: '/' }]** to the NgModule.\
Then, locate the route-Array at the top of the file and add **{ path: '\*\*', component: EmptyRouteComponent }** to the array.\
Now, open app.module.ts and add **EmptyRouteComponent** to the declarations-Array in the NgModule.
