# sequelize-slugify

[![npm](https://img.shields.io/npm/v/sequelize-slugify.svg)]() [![Dependency Status](https://david-dm.org/jarrodconnolly/sequelize-slugify.svg)](https://david-dm.org/jarrodconnolly/sequelize-slugify)

sequelize-slugify is a model plugin for Sequelize that automatically creates and updates unique slugs for your models.


## Installation

`npm install sequelize-slugify`

## Usage Example

```javascript

var SequalizeSlugify = require('sequelize-slugify');

module.exports = function(sequelize, DataTypes) {
    var User = sequelize.define('User', {
            slug: {
                type: DataTypes.STRING,
                unique: true
            },
            emailAddress: {
                type: DataTypes.STRING,
                allowNull: false,
                unique: true
            },
            givenName: {
                type: DataTypes.STRING,
                allowNull: false
            },
            familyName: {
                type: DataTypes.STRING,
                allowNull: false
            }
        });

    SequalizeSlugify.slugifyModel(User, {
            source: ['givenName', 'familyName']
        });

    return User;
};

```