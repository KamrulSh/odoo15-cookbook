### Set Default Group By For Menu Action

- To show the data by group we have to add group rules in search view. Here we have added a group rules by status.

  ```xml
  <group expand="1" string="Group By">
      <filter string="Status" name="state" context="{'group_by':'status'}"/>
  </group>
  ```

- Then we have to add context for this group in action window and add the default search for state inside `{}`. If we don't add the default search then it will be empty.

  ```xml
  <field name="context">{'search_default_state': 1}</field>
  ```

  ![groupFilter1](../images/groupFilter1.png)

  - [Check out the code for group](https://github.com/KamrulSh/km_hospital/blob/b17e37367e679328cded7f15257f9eee753e8b5d/views/appointment_view.xml#L108-L110)

### Set Default Filter For Menu

- For filtering based on gender we have to add some filter rules.

  ```xml
  <filter string="Male" name="male" domain="[('gender', '=', 'male')]"/>
  <filter string="Female" name="female" domain="[('gender', '=', 'female')]"/>
  ```

- Then we have to add context for this filter in action window just like group.

  ```xml
  <field name="context">{'search_default_state': 1, 'search_default_male': 1}</field>
  ```

  ![groupFilter2](../images/groupFilter2.png)

  - [Check out the code for filter](https://github.com/KamrulSh/km_hospital/blob/b17e37367e679328cded7f15257f9eee753e8b5d/views/appointment_view.xml#L106-L107)
  - [Check out the code for both group and filter](https://github.com/KamrulSh/km_hospital/commit/2e4d64d3e9c1e7a46ace646eb806b9a36106cc0f)

### Set Domain For Menu Action

- To set domain for menu action we have created a sub-menu named `Kids Appointments` in the `Appointments` menu. Then set a domain for kids based on age.

  ```xml
  <field name="domain">[('age', '&lt;=', 10)]</field>
  ```

  ![groupFilter3](../images/groupFilter3.png)

  - [Check out the code for kids domain](https://github.com/KamrulSh/km_hospital/commit/b17e37367e679328cded7f15257f9eee753e8b5d)

## 🚀 Happy Coding ! 🔥
