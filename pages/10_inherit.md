### Inherit employee module and add some fields

- For this we are creating a new module named `employee_custom` for better understanding.
- To inherit an existing table in the `hr.employee` model we have to add module name in `depends` in the manifest file. Here we are inheriting the employee module which name is `hr`.
  ```py
  'depends': ['base', 'hr']
  ```
- Then create a python model to inherit the employee module and add some fields to it. Don't forget to import the python file in `models` > `__init__.py`.

  ```py
  class InheritCertification(models.Model):
      _inherit = "hr.employee"

      skype_name = fields.Char("Skype name")
      joining_date = fields.Date("Joining Date")
  ```

  - [Check out the code](https://github.com/KamrulSh/employee_custom/blob/c22d32fe198d76bb4c47bd641be13eaeb583ce1f/models/certificate.py#L5-L9)

- Then create an `xml` file named `inherit_certificate_views.xml` and copy this code below. Here `name` will be `hr.view_employee_form`, `model` will be `hr.employee` and `inherit_id` > `ref` will be `hr.view_employee_form` as we are inheriting the from view of `hr.employee`.
- Go to `Bug icon > Edit View: Form` to find the required fields.

  ![inherit1](../images/inherit1.png)

  ```xml
  <record id="employee_inherit_id" model="ir.ui.view">
      <field name="name">hr.view_employee_form</field>
      <field name="model">hr.employee</field>
      <field name="inherit_id" ref="hr.view_employee_form"/>
      <field name="arch" type="xml">
          <xpath expr="//field[@name='work_email']" position="after">
              <field name="skype_name"/>
          </xpath>

          <xpath expr="//field[@name='resource_calendar_id']" position="before">
              <field name="joining_date"/>
          </xpath>
      </field>
  </record>
  ```

  - [Check out the code](https://github.com/KamrulSh/employee_custom/blob/c22d32fe198d76bb4c47bd641be13eaeb583ce1f/views/inherit_certificate_views.xml#L9-L15)

- Add the xml file to the `__manifest__.py`. Install the `employee_custom` module and go to the `hr.employee` model and you will get the added field like below.

  ![inherit2](../images/inherit2.png)

## 🚀 Happy Coding ! 🔥
