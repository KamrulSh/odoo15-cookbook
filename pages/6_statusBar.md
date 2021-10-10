## Adding Status and Status Bar

- For creating a status bar we have to create a selection field in python file. Here, a selection field `status` is created in `appointment.py` file.

  ```py
  status = fields.Selection([
        ('draft', 'Draft'),
        ('confirmed', 'Confirmed'),
        ('done', 'Done'),
        ('cancel', 'Canceled')
  ], default='draft', required=True)
  ```

- In the `appointment_view.xml`, we have to add a `header` with `status` field to show and change the status inside the form view and before the `sheet` tag.
  ```xml
  <header>
      <field name="status" widget="statusbar" statusbar_visible="draft,confirm,done" options="{'clickable':'1'}"/>
  </header>
  ```
  ![statusbar1](../images/statusbar1.png)
