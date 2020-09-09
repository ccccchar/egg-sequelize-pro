# egg-sequelize-pro

## Install

```bash
$ npm i --save egg-sequelize-pro
$ npm install --save mysql2 # For both mysql and mariadb dialects

# Or use other database backend.
$ npm install --save pg pg-hstore # PostgreSQL
$ npm install --save tedious # MSSQL
```

## Usage & configuration

- Enable plugin in `config/plugin.js`

``` js
exports.sequelize = {
  enable: true,
  package: 'egg-sequelize-pro'
}
```

- Edit your own configurations in `conif/config.{env}.js`

```js
exports.sequelize = {
  dialect: 'mysql', // support: mysql, mariadb, postgres, mssql
  database: 'test',
  host: 'localhost',
  port: 3306,
  username: 'root',
  password: '',
};
```

You can also use the `connection uri` to configure the connection:

```js
exports.sequelize = {
  dialect: 'mysql', // support: mysql, mariadb, postgres, mssql
  connectionUri: 'mysql://root:@127.0.0.1:3306/test',
  // delegate: 'myModel', // load all models to `app[delegate]` and `ctx[delegate]`, default to `model`
  // baseDir: 'my_model', // load all files in `app/${baseDir}` as models, default to `model`
  // exclude: 'index.js', // ignore `app/${baseDir}/index.js` when load models, support glob and array
  // more sequelize options
};
```

egg-sequelize has a default sequelize options below

```js
{
    delegate: 'model',
    baseDir: 'model',
    logging(...args) {
      // if benchmark enabled, log used
      const used = typeof args[1] === 'number' ? `[${args[1]}ms]` : '';
      app.logger.info('[egg-sequelize]%s %s', used, args[0]);
    },
    host: 'localhost',
    port: 3306,
    username: 'root',
    benchmark: true,
    define: {
      freezeTableName: false,
      underscored: true,
    },
  };
```

More documents please refer to [Sequelize.js](http://docs.sequelizejs.com/manual/installation/usage.html)


