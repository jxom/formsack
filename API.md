# Example

```jsx
import { 
  Formsack, 
  Form, 
  Field, 
  useFormData,
  useFormMutators,
  useFieldData,
  useFieldMutators
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
  const { 
    getValues, 
    getErrors, 
    getTouched,
    setValues,
    setErrors,
    setTouched
  } = useFormData();
  
  const { fieldKeys, add, remove, addToStart, addAtIndex, swap, move } = useFieldArray('friends');
  
  React.useEffect(() => {
    const values = getValues();
    const usernameValue = getValues('username');
   
    setValues({ username: 'Johnny' });
    // OR
    setValues('username', 'Johnny');
  }, [])

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
      {fieldKeys.map((fieldKey) =>
        <>
          <Field as="input" name={`${fieldKey}.username`} />
          <Field as="input" name={`${fieldKey}.email`} />
        </>
      )}
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

## `ErrorMessage`

TODO

## `useFieldArray`

TODO

## `useFormData`

TODO
