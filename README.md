# Code Critic

This is a very simple implementation of Javascript code quality analysis. Code critic uses various open source libraries to find vulnerabilities in code and reports then to the user.

* [Getting Sarted](#getting-started)
    * [Dependencies](#dependencies)
    *  [Setting up the app](#setting-up-the-app)
    *  [Running the tests](#running-the-tests)
    *  [Starting the website](#starting-the-website)
* [Libaries used](#libaries-used)
* [How it works](#understanding-the-application)
    *  [Scoring](#scoring)
* [License](#license)

## Getting Started
### Dependencies

1. NodeJS 10.0+
2. Ruby 2.0+
3. NPM 1.4+

### Setting up the app
Run the following:

```
bundle install
npm install
```

### Running the tests

```
npm test
```

### Starting the website

```
npm start
```

The application will be available at http://localhost:3000/


## Libaries used:

1. [JSHint](http://jshint.com): JSHint reviews the code for styling and common problems.
2. [ScanJS](https://github.com/mozilla/scanjs): A Security scanner that reviews the code for major vulnerabilities.
3. [David](https://github.com/alanshaw/david): Checks each dependency in package.json and validates whether there is a newer version available.
4. [Complexity-Report](https://www.npmjs.com/package/complexity-report): Generates a complex mathematical analysis of the source code trying to identify the maintainability effort.
5. [Flay-JS](https://github.com/UncleGene/flay-js): Reviews the code for structural similarities and copy pasted snippets and helps keep the code DRY.

In addition to code quality analysis, there are various open source libraries that are used here for software development. Please refer to the same in `package.json`.

Finally, we use [SyntaxHighlighter](http://alexgorbatchev.com/SyntaxHighlighter/) to display source code on the UI.

## Understanding the application

The application uses preconfigured rules for JSHint and Complexity analysis and the same can be found under `./config/`. Please note that these rules are only indicative and you should feel free to change any if you do not agree with them.

### Scoring
Code Critic uses a simple algorithm for rating files and generating a roll up score for each code base.

Total # of Issues in the file | Rating 
-------------------------------| ------------
 > 10 | 1 
 > 5 && <= 10 | 2 
 > 2 && <= 5 | 3 
 > 0 && <= 2 | 4 
 0 | 5 

Once all files have been rated, all ratings are added and divided by the total number of files to get a total score.

## License
The tool is available under MIT License. Please review the `LICENSE` file under the repository.
