---
categories: development
date: '2020-05-17T09:00:00Z'
draft: true
keywords: react vscode vs code vs-code snippet templates componenets
tags: react vscode web-development
title: VSCode Snippets For React
---
As of the last several years I have done a lot of my work in React using VS Code. When first starting out, I tried to find or make a templating engine for React so that I could quickly create Component templates. Eventually I realized VSCode has a pretty in depth templating engine built in with [Snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets) and that I could easily create what I wanted to use with a little bit of effort.

If this is your first experience with Snippets I definitely recommend reading the [linked](https://code.visualstudio.com/docs/editor/userdefinedsnippets) page first and brushing up on the syntax, although it is pretty simple.

First I am going to simply share my snippets, so that if you found this page and are just looking to get functional snippet code you can copy paste and quit, and then maybe I'll explain a bit of how this fits into my workflow.

# The Snippets
I use four total snippets spread across two syntaxes, `javascriptreact` and `javascript` 

In `javascriptreact` I house my two component snippets. The distinction between the two being whether I want to connect the component to my redux state or not.
```json
{
	"Basic React Component" :{
		"prefix": "cc",
		"body": [
			"import React from 'react';",
			"import PropTypes from 'prop-types';",
			"",
			"import styles from './${1:filename}.module.scss';",
			"",
			"class ${1:filename} extends React.Component {",
			"",
			"	render() {",
			"		return (",
			"			<div>${1:filename}</div>",
			"		);",
			"	}",
			"}",
			"",
			"${1:filename}.propTypes = {",
			"};",
			"",
			"export default ${1:filelname};",
		],
		"description": "Creates a basic react component not connected to state"
	},
	"React Component With State" :{
		"prefix": "ccs",
		"body": [
			"import React from 'react';",
			"import PropTypes from 'prop-types';",
			"import { connect } from 'react-redux';",
			"",
			"import styles from './${1:filename}.module.scss';",
			"",
			"class ${1:filename} extends React.Component {",
			"",
			"	render() {",
			"		return (",
			"			<div>${1:filename}</div>",
			"		);",
			"	}",
			"}",
			"",
			"${1:filename}.propTypes = {",
			"};",
			"",
			"function mapStateToProps(state) {",
			"  return {};",
			"}",
			"",
			"function mapDispatchToProps(dispatch) {",
			"  return {};",
			"}",
			"",
			"export default connect(mapStateToProps, mapDispatchToProps)(${1:filelname});",
		],
		"description": "Creates a basic react component connected to state"
  }
}
```

And for the last two snippets in `javascript` I have my index.js.
```json
{
	"Index page" :{
		"prefix": "index",
		"body": [
			"import ${1:filename} from './${1:filename}';",
			"export default ${1:filename};"
		],
		"description": "For creating index.js"
	},
	"Action Constants" :{
		"prefix": "action",
		"body": [
			"export const ${1:action}_REQUEST = '${1:action}_REQUEST';",
			"export const ${1:action}_SUCCESS = '${1:action}_SUCCESS';",
			"export const ${1:action}_FAILURE = '${1:action}_FAILURE';",
		]
	}
}
```