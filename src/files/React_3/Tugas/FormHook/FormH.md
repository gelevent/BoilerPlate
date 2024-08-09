// Form.js
import React from 'react';
import useForm from './useForm';

const Form = () => {
    const initialValues = { name: '', email: '', password: '' };

    const submitForm = (values) => {
        console.log('Form submitted with values:', values);
    };

    const { values, errors, handleChange, handleSubmit } = useForm(initialValues, submitForm);

    return (
        <form onSubmit={handleSubmit}>
            <div>
                <label>Name:</label>
                <input
                    type="text"
                    name="name"
                    value={values.name}
                    onChange={handleChange}
                />
                {errors.name && <p style={{ color: 'red' }}>{errors.name}</p>}
            </div>
            <div>
                <label>Email:</label>
                <input
                    type="email"
                    name="email"
                    value={values.email}
                    onChange={handleChange}
                />
                {errors.email && <p style={{ color: 'red' }}>{errors.email}</p>}
            </div>
            <div>
                <label>Password:</label>
                <input
                    type="password"
                    name="password"
                    value={values.password}
                    onChange={handleChange}
                />
                {errors.password && <p style={{ color: 'red' }}>{errors.password}</p>}
            </div>
            <button type="submit">Submit</button>
        </form>
    );
};

export default Form;
