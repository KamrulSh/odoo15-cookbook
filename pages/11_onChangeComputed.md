### On change function

- If we choose a patient name while creating a new appointment, it will automatically fill the `Note` field and if we remove the patient it will be empty. This task is done using `onChange` function.

  ```py
  @api.onchange('patient_id')
    def _change_appointment_note(self):
        if self.patient_id:
            if not self.note:
                self.note = "New appointment"
        else:
            self.note = ""
  ```

  ![onChange](../images/onChange.png)

  - [Check out the code for onChange](https://github.com/KamrulSh/km_hospital/commit/6673e3f8f3d9791ad18064dd6cdb37f10336afdb)

- If we set `Note` as a `readonly` field and save it will not store the data of `Note`. To save we have to use `force_save="1"` in the form view of the `Note` field.
  ```xml
  <field name="note" readonly="1" force_save="1"/>
  ```
  - [Check out the code](https://github.com/KamrulSh/km_hospital/blob/ae7e36f3bacd49504659a2e72dd13b61c14335d7/views/appointment_view.xml#L57)

## 🚀 Happy Coding ! 🔥