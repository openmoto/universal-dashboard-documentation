## Custom Components

Required Version: 1.4.0

The New-UDElement enables you to create custom components for Universal Dashboard. Components can be created with PowerShell or with JavaScript. Custom Components can ship as modules or simple PS1 scripts. 

### PowerShell-Based Components 

The New-UDElement cmdlet can be used to create HTML tags that define the markdown for a custom component. New-UDElements can be nested and attributes can be added. 

A simple custom component may be defined such as this.

```
New-UDElement -Tag "a" -Attributes @{
    href = "https://www.poshud.com"
    target = "_self"
} -Content "Poshud"
```

This custom component would define a React class in JavaScript that would eventually translate into an HTML link with the following markup. 

```
<a href="https://www.poshud.com" target="_self">Poshud</a>
```

The `Content` parameter can define text as well as nested elements. For example, if you wanted to define a [Materialize Preloader](http://materializecss.com/preloader.html), you would need to define the following HTMl.

```
<div class="progress">
   <div class="determinate" style="width: 70%"></div>
</div>
```

To define the same component using `New-UDElement`, you could use the following script. 

```
New-UDElement -Tag "div" -Attributes @{ className = "progress" } -Content {
   New-UDElement -Attributes @{ className = "determinate"; style=@{width = "70%"}
}
```

For some examples of custom components, visit [GitHub](https://github.com/ironmansoftware/ud-material-design/blob/master/UniversalDashboard.MaterialDesign.psm1).

### JavaScript-based Components 

New-UDElement can also define JavaScript-based components. These components should define a React component that is capable of loading into a React single page application. 

Universal Dashboard uses several web development technologies that may be helpful when developing your own JavaScript-based elements. 

- Webpack
- Babel
- React
- NPM

For this example, we will be using the [UDSparklines](https://github.com/ironmansoftware/ud-sparklines) project. 

To get started, you will need to define a NPM package.json file. This final defines the package's dependencies and any tooling that is required to bundle the package into a final JS file. UDSparklines uses react-sparklines.

The `main` setting defines the JS file to compile. The `build` and `dev` tasks define how the JS file is compiled. In this case, we are using webpack.

```
{
  "name": "ud-sparklines",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack -p --env production",
    "dev": "webpack -p --env development"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
      "react":"16.2.0",
      "react-sparklines":"1.7.0"
  },
  "devDependencies": {
    "babel-core": "^6.26.0",
    "babel-loader": "^7.1.2",
    "babel-preset-es2015": "^6.24.1",
    "babel-preset-react": "^6.24.1",
    "uglifyjs-webpack-plugin": "0.4.6",
    "webpack": "^3.6.0"
  }
}
```
