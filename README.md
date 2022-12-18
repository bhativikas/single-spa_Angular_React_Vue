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

Thats all for creating the initial files for root-config and run the command **npm i & npm start**.

**Step 2**: Create 1st Angular Application - navbar\
Open a new CMD terminal and run **ng new navbar  --routing --prefix navbar --style css & cd navbar & ng add single-spa-angular & cd ..** (Refer link: https://single-spa.js.org/docs/ecosystem-angular#installation). This command will ask following further details:\
? Would you like to share pseudonymous usage data about this project with the Angular Team at Google under Google's Privacy Policy at https://policies.google.com/privacy. For more details and how to change this setting, see https://angular.io/analytics. **No**\
The package single-spa-angular@7.1.0 will be installed and executed.\
Would you like to proceed? **Yes**\
√ Packages successfully installed.\
? Does your application use Angular routing? **Yes**\
? What port should your project run on? **4200**

Thats all for creating the initial files for app-parcel - navbar and run the command **npm i & npm run serve:single-spa:navbar**.

**Step 3**: Create 2nd Angular Application - default\
Open a new CMD terminal and run **ng new default  --routing --prefix default --style css & cd default & ng add single-spa-angular & cd ..** with providing same input mentioned in step 2 except following one:\
? What port should your project run on? **4300**

Thats all for creating the initial files for app-parcel - default and run the command **npm i & npm run serve:single-spa:default**.

**Step 4**: Create 3rd Angular Application - module01\
Open a new CMD terminal and run **ng new module01  --routing --prefix module01 --style css & cd module01 & ng add single-spa-angular & cd ..** with providing same input mentioned in step 2 except following one:\
? What port should your project run on? **4400**

Thats all for creating the initial files for app-parcel - module01 and run the command **npm i & npm run serve:single-spa:module01**.

**Step 5**: Create 1st React Application - module02\
Open a new CMD terminal and run **create-single-spa --framework react**. This command will ask following further details:\
? Directory for new project **module02**\
? Which package manager do you want to use? **npm**\
? Will this project use Typescript? **Yes**\
? Organization name (can use letters, numbers, dash or underscore) **neworg**\
? Project name (can use letters, numbers, dash or underscore) **module02**

Thats all for creating the initial files for app-parcel - module02 and run the command **npm i & npm start -- --port 8500**.

**Step 6**: Create 1st Vue Application - module03\
Open a new CMD terminal and run **create-single-spa --framework vue**. This command will ask following further details:\
? Directory for new project **module03**\
? Organization name (can use letters, numbers, dash or underscore) **neworg**

Thats all for creating the initial files for app-parcel - module03 and run the command **npm i & npm run serve**.

**Step 7**: Update **app-routing.module.ts** and **app.module.ts** for angular projects - **navbar**, **default** and **module01** (Refer link: https://single-spa.js.org/docs/ecosystem-angular/#routing) \
Open app-routing.module.ts and add providers: **[{ provide: APP_BASE_HREF, useValue: '/' }]** to the NgModule.\
Then, locate the route-Array at the top of the file and add **{ path: '\*\*', component: EmptyRouteComponent }** to the array.\
Now, open app.module.ts and add **EmptyRouteComponent** to the declarations-Array in the NgModule.

**Step 8**: Update **index.ejs** and **microfrontend-layout.html** for root-config - **main** to register angular applications\
Open **index.ejs** and uncomment the line that imports zone.js\
Then, remove following line under imports of systemjs-importmap\
**"@single-spa/welcome": "https://unpkg.com/single-spa-welcome/dist/single-spa-welcome.js"** \
Then, add following lines under imports of systemjs-importmap\
**"@neworg/navbar": "http://localhost:4200/main.js", \
"@neworg/default": "http://localhost:4300/main.js", \
"@neworg/module01": "http://localhost:4400/main.js"**

Now, open **microfrontend-layout.html** and add the following line before main tag\
`<nav>` \
`<application name="@neworg/navbar"></application>` \
`</nav>` \
Then, **update the name of default route** as mentioned below\
`<route default>` \
`<application name="@neworg/default"></application>` \
`</route>` \
Then, **add following route** as well\
`<route path="/module01">` \
`<application name="@neworg/module01"></application>` \
`</route>`

_I noticed one warning in console of Developer Tools - **Content Security Policy: The page's settings blocked the loading of a resource at data:image/svg+xml;base64,PHN2ZyB4bWxucz… ("default-src").**\
To resolve this, add **data: to default-src in Content-Security-Policy (meta http-equiv)**_

**Step 9**: Update **index.ejs** and **microfrontend-layout.html** for root-config - **main** to register react application\
Open **index.ejs** and search for following line: "single-spa": "https://cdn.jsdelivr.net/npm/single-spa@5.9.0/lib/system/single-spa.min.js" \
Then, add following lines after above line mentioned for search\
**"react": "https://cdn.jsdelivr.net/npm/react@16.13.1/umd/react.production.min.js", \
"react-dom": "https://cdn.jsdelivr.net/npm/react-dom@16.13.1/umd/react-dom.production.min.js"** \
Then, add following lines under imports of systemjs-importmap\
**"@neworg/module02": "http://localhost:8500/neworg-module02.js"**

Now, open **microfrontend-layout.html** and **add following route** as well\
`<route path="/module02">` \
`<application name="@neworg/module02"></application>` \
`</route>`

**Step 10**: Update **index.ejs** and **microfrontend-layout.html** for root-config - **main** to register vue application\
Open **index.ejs** and search for following line: "single-spa": "https://cdn.jsdelivr.net/npm/single-spa@5.9.0/lib/system/single-spa.min.js" \
Then, add following lines after above line mentioned for search\
**"vue": "https://cdn.jsdelivr.net/npm/vue@3.2.45/dist/vue.global.min.js", \
"vue-router": "https://cdn.jsdelivr.net/npm/vue-router@4.1.6/dist/vue-router.global.min.js"** \
Then, add following lines under imports of systemjs-importmap\
**"@neworg/module03": "http://localhost:8080/js/app.js"**

Now, open **microfrontend-layout.html** and **add following route** as well\
`<route path="/module03">` \
`<application name="@neworg/module03"></application>` \
`</route>`

_I noticed one warning in console of Developer Tools - **Content Security Policy: The page's settings blocked the loading of a resource at ws://IP_ADDRESS:8080/ws ("connect-src").**\
To resolve this, add **ws://IP_ADDRESS:\* to connect-src in Content-Security-Policy (meta http-equiv)**_

Also, please update module03\vue.config.js with following content after transpileDependencies property and ***restart the server***
configureWebpack: { \
output: { \
libraryTarget: "system", \
filename: "js/app.js" \
} \
} 

**Step 11**: Update navbar\src\app\app.component.html with following contents before `<router-outlet></router-outlet>` \
`<div>` \
` <a routerLink="/module01">Module 01 (Angular)</a>` \
` |<a routerLink="/module02">Module 02 (React)</a>` \
` |<a routerLink="/module03">Module 03 (Vue)</a>` \
`</div>`
