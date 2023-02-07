## Frontend: email searching engine 

tool to search and visualize Enron email data set using Vue.js and tailwind CSS. You can enter a word and the tool will display a table containing the emails where the word appears, you will see: From, To and Subject for each email. 
The Vite tool was used to build the vue project allowing to work with modules natively.

## :wrench: Installation

Ensure the following is installed:

* [Node.js and npm are installed locally](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

You can install vue locally following those steps: 
```shell
npm install -g @vue/cli@next 
vue upgrade next
```

Then clone the repo locally: `git clone https://github.com/lauramog/mailsearch-ui.git`

This tool  works togeter with  the web server and the indexer both  built in go. you can find it [here](https://github.com/lauramog/mailsearch-api)


## Run

```shell
npm run dev
```

If you want to make  changes in the html files
```shell
npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch
```

Run the Dev server at the URL given.


