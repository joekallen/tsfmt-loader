# Webpack TypeScript Formatter (tsfmt-loader)

A Webpack Preloader that uses the typescript-formatter library  [typescript-formatter](https://www.npmjs.com/package/typescript-formatter).

## Installation

```npm install tsfmt-loader --save-dev```

## Usage

### Preloader configuration

```
module: {
  preLoaders:[
    {
      test: /\.ts$/,
      loader: 'tsfmt-loader',
      query: {
        replace: true
      }
    }
  ]
}
```

## Options
#### All options have a default and can be overwritten in the query object of your preloader configuration.
 ```bash
 [baseDir]              The base directory for your configuration files
 [verbose=false]       makes output more verbose
 [replace=true]        replace .ts file
 [tsconfig=true]       Reads your tsconfig.json for formatting rules
 [tslint=true]         Reads your tslint.js for formatting rules
 [editorconfig=true]   Reads your .editorconfig for formatting rules
 [tsfmt=true]          Reads your tsfmt.json for formatting rules


 ```

## Note
If you are using other preloaders it is suggested you list this one last.  Webpack executes preloaders in reverse order and this will allow the formatter to execute before other tasks like linters.

## Read Settings From Files.  Reference [typescript-formatter npm listing](https://www.npmjs.com/package/typescript-formatter) for more information.

1st. Read settings from tsfmt.json. Bellow are the example with [default values](https://github.com/vvakame/typescript-formatter/blob/master/lib/utils.ts):

```json
{
  "indentSize": 4,
  "tabSize": 4,
  "newLineCharacter": "\r\n",
  "convertTabsToSpaces": true,
  "insertSpaceAfterCommaDelimiter": true,
  "insertSpaceAfterSemicolonInForStatements": true,
  "insertSpaceBeforeAndAfterBinaryOperators": true,
  "insertSpaceAfterKeywordsInControlFlowStatements": true,
  "insertSpaceAfterFunctionKeywordForAnonymousFunctions": false,
  "insertSpaceAfterOpeningAndBeforeClosingNonemptyParenthesis": false,
  "insertSpaceAfterOpeningAndBeforeClosingNonemptyBrackets": false,
  "insertSpaceAfterOpeningAndBeforeClosingTemplateStringBraces": false,
  "placeOpenBraceOnNewLineForFunctions": false,
  "placeOpenBraceOnNewLineForControlBlocks": false
}

```

2nd. Read settings from .editorconfig ([editorconfig](http://editorconfig.org/))

```text
# EditorConfig is awesome: http://EditorConfig.org

# top-most EditorConfig file
root = true

# Unix-style newlines with a newline ending every file
[*]
indent_style = tab
tab_width = 2
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
```

3rd. Read settings from tslint.json ([tslint](https://www.npmjs.org/package/tslint))

```json
{
  "rules": {
    "indent": [true, 4],
    "whitespace": [true,
      "check-branch",
      "check-operator",
      "check-separator"
    ]
  }
}
```