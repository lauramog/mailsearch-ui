## Frontend: email searching engine 

tool to search and visualize Enron email data set using Vue.js and tailwind CSS. you can enter a word and the tool will display a table containing the emails where the word appears, you will see: From, To and Subject for each email. 
The Vite tool was used to build the vue project allowing to work with modules natively.

:wrench:## Installation

Ensure the following is installed:

* [Node.js and npm are installed locally](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

you can install vue locally following those steps: 
```shell
npm install -g @vue/cli@next 
vue upgrade next
```

Then clone the repo locally: `git clone https://github.com/lauramog/mailsearch-ui.git`

this tool  works togeter with  the api and the indexer built in go. you can find it (here)[https://github.com/lauramog/mailsearch-api] 


## Run

```shell
npm run dev
```

if you want to make  changes in the html files
```shell
npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch
```

run the Dev server at the URL given.


