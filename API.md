# Example

```jsx
import { 
  Formsack, 
  Form, 
  Field, 
  useFormValues,
  useFormErrors,
  useFormTouched,
  useFormMutators,
  useFieldValue,
  useFieldError,
  useFieldTouched
} from 'formsack';

import { isValidEmail } from './validation';

function Example() {
  return (
    <Formsack initialValues={{ username: 'Jimmy' }} validateOn="submit">
      <Form>
        <MyFields />
      </Form>
    </Formsack>
  );
}

function MyFields() {
  // Getters & setters for the global form attributes.
  const values = useFormValues();
  const errors = useFormErrors();
  const touched = useFormTouched();
  const { setValues, setErrors, setTouched } = useFormMutators();

  // Getters & setters for field-level attributes (this is better for performance).
  const [username, setUsername] = useFieldValue('username');
  const [usernameError, setUsernameError] = useFieldError('username');
  const [usernameTouched, setUsernameTouched] = useFieldTouched('username');

  return (
    <>
      <Field 
        as="input" 
        name="username" 
        validate={{ required: true }} 
      />
      <Field 
        as="input" 
        name="email" 
        validate={{ 
          required: true, 
          fns: [isValidEmail] 
        }} 
      />
    </>
  )
}
```

# APIs

## `Formsack`

### Props

**`initialValues: { [fieldKey: string]: any }`**

The initial values

**`validateOn: 'change' | 'blur' | 'submit'`**

Default: `blur`

When to validate the fields.

- `change`: Validates the field when input changes
- `blur`: Validates the field when the input is blurred
- `submit`: Validates the fields when the form is submitted

## `Form`

TODO

## `Field`

TODO

## `FieldArray`

TODO

## `ErrorMessage`

TODO

## `useFieldValue`

TODO

## `useFieldMeta`

TODO