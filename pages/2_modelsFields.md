## Creating custom Module

- In the `custom_addons` directory create your own module ex.`real_estate` known as technical name. In this module minimum two file is mandatory, one is `__init__.py` and the other is `__manifest__.py`.

- A demo template for `__manifest__.py`:

  ```py
  {
      'name': "Real Estate",
      'sequence': 10,
      'summary': """
          A real estate module where one can add properties info
          for advertising purposes""",

      'description': """
          A real estate module where one can add properties info
          for advertising purposes""",

      'author': "Kamrul",
      'website': "http://www.yourcompany.com",
      'category': 'Uncategorized',
      'version': '0.1',
      'license': 'LGPL-3',
      'depends': ['base'],
      'data': [],
      'demo': [],
      'installable' : True,
      'application' : True,
      'auto_install' : False,
  }
  ```

  Look up the code: [`__manifest__.py`](https://github.com/KamrulSh/real_estate/blob/main/__manifest__.py)

- Run the odoo server using this command:
  ```sh
  /opt/odoo/odoo14/./odoo-bin --addons-path=/opt/odoo/odoo14/addons,/opt/odoo/odoo14/custom_addons --xmlrpc-port=8014
  ```
- In the odoo app list search module name `real_estate` and you will find the app. In the `Module Info` you will find all the information given in the `__manifest__.py` file. You can also install and upgrade the app.

  ![module1](../images/module1.png)
  ![module2](../images/module2.png)
