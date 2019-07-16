# Personal-Log-Error

* When first trying to insert into database

  * Error: `INSERT INTO "Users" ("id","name","email","password_hash","created_at","updated_at") VALUES (DEFAULT,$1,$2,$3,$4,$5) RETURNING *`
  * Description:
    The insertion was trying to insert into the table `Users`, when it should insert into `users`

  * FIX:
    on the database config file

        module.exports = {
        dialect: 'postgres',
        host: 'localhost',
        username: 'postgres',
        password: 'docker',
        database: 'gobarber',
        define: {
          timestamps: true,
          underscored: true,          --> These were written wrong, 'underscore' ***
          underscoredAll: true,       --> These were written wrong, 'underscoreAll' ***
        },

    So I changed `underscore` to `underscored` and `underscoreAll` to `underscoredAll` and it worked



  