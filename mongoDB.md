# MongoDB

## Instalation:
<strong>This mongoDB will be set using docker</strong>

to install the container, run: 
  `docker run --name mongobarber -p 27017:27017 -d -t mongo`

and to add mongoose to your project:
  `yarn add mongoose`

## Code

Inside your migrations index, start your mongo connection using mongoose:

<pre><code>
mongo() {
  this.mongoConnection = mongoose.connect(
    'mongodb://localhost:[port]/[database name]'
  );
}
</code></pre>

make sure to run this function on your Database constructor:

<pre><code>
class Database {
  constructor() {
    this.init();
    this.mongo();
  }
  .
  .
  .
</code></pre>


## Management tool for mongo

[MongoDB compass download center](https://www.mongodb.com/download-center/compass)

