XiVO dird plugin Odoo
======================

[![Build Status](https://travis-ci.org/alexis-via/xivo-dird-plugin-backend-odoo.png?branch=master)](https://travis-ci.org/alexis-via/xivo-dird-plugin-backend-odoo)


## Info

This plugin gets contacts from Odoo v7 or v8.

## How to use

On the Odoo side, you need to install the *base_phone* module, which is a module of the [Odoo Community Association](https://odoo-community.org/) available on the [connector-telephony](https://github.com/OCA/connector-telephony) github project. When you install this module, a wizard will propose you to reformat the phone numbers in E.164 format ; you should follow the instructions of the wizard.

On the Xivo side, in the config file */etc/xivo-dird/config.yml*, enable the odoo plugin:

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

To benefit from the contacts of Odoo in the Xivo Client, you need to update the configuration of the profile of the Xivo Client. For that, in the Web administration interface of Xivo, go to the menu *Services > CTI Server > General Settings > Profiles* and edit your profile (*Client* by default): in the *Xlet* tab, add the *People* Xlet (or replace the *Remote directory* Xlet by the *People* Xlet).
