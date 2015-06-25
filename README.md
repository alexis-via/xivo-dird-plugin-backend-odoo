XiVO dird plugin Odoo
======================

[![Build Status](https://travis-ci.org/alexis-via/xivo-dird-plugin-backend-odoo.png?branch=master)](https://travis-ci.org/alexis-via/xivo-dird-plugin-backend-odoo)


## Info

This plugin gets contacts from Odoo v7 or v8.

## How to use

In the config file */etc/xivo-dird/config.yml*, enable the odoo plugin:

    enabled_plugins:
        backends:
            - odoo

The possible fields with this plugin are :

    views:
        displays:
            default_display:
            -
                title: Name
                field: lastname
                type: name
            -
                title: Entity
                field: entity
                type: name
            -
                title: Job
                field: job
                type: name
            -
                title: Phone
                field: phone
                type: number
            -
                title: Mobile
                field: mobile
                type: number
            -
                title: Email
                field: email
            -
                title: Fax
                field: fax
                type: ???

You should add the source like this:

    services:
        lookup:
            default:
                sources:
                    - my_odoo

Eventually, add a configuration file *my\_odoo.yml* in the *sources.d* subdirectory:

    type: odoo
    name: my_odoo
    odoo_config:
        userid: 1
        password: adminpwd
        database: prod
        port: 8069
        server: 192.168.12.42
