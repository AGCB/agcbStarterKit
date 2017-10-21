# agcbStarterKit
my helloWorld with webPack and Babel....

I learned this from Chris Hawkes Youtube [vid](https://www.youtube.com/watch?v=X5wTsHRsbIA) on this subject. 

I saw his video as 7 steps.

Before step 1 you have make a folder and be navigated inside it from a terminal.

1-- npm init
2--
	npm install --save babel-loader babel-preset-env babel-core webpack
	they will also be added to the package.json file that got made on step1

	A real piece of power there is that if you move the project to another computer,
	the package.json lets you npm install and get all of the dependencies with the 
  proper versions.

3-- make a webpack.config.js file
  We need an entry point.
	Then the output ends up going to bundle.js
  then watch:true is to watch the files and make a new bundle.js everytime something changes.
  then modules is an object....
    which takes loaders which is an array of objects.
    the first is loader babel-loader
    then query is an object 
       presets is babel-preset-env
  	WOW!!!

 

module.exports = {
	entry: './app.js',
	output: {
		path: __dirname,
		filename: 'bundle.js'
	},
	watch: true,
	module: {
		loaders: [
		{
			loader: 'babel-loader',
			query: {
				presets: ['babel-preset-env']
			}
		}
		]
	}
}



4-- now we create app.js
   const test = () => {
	alert('hello world')
}

const test2 = () => {
	alert('hello twice')
}
test()

We use 2 newer JS features, Const and fat arrow syntax..

5. back in the package.json we need to add a script.
   "webpack: "webpack"
	this will use the locally installed webpack that we have.

6. npm run webpack
   This uses step5 .. it will make a bundle.js from the app.js.
   Notice at the very bottom of the bundle.js that the test and test2 functions got transpiled to older JS automatically!
   If we now make any changes to our app.js, we will automatically see our updated bundle.js in the terminal
   Note that if we want to do anything else in the terminal, that we have to open a new terminal window.
   Our first terminal window wont respond to any commands as it is being used to "watch" our project now.

7. make an index.html
   in the head, add...
    <script src="./bundle.js"></script>

Now you are good to go.
At this stage in the project the only benefit that I see is that we have babel transpiling our code for 
older browsers.         



