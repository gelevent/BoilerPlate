// useForm.js
import { useState, useEffect } from 'react';

const validate = (values) => {
    const errors = {};
    if (!values.name) errors.name = 'Name is required';
    if (!values.email) errors.email = 'Email is required';
    else if (!/\S+@\S+\.\S+/.test(values.email)) errors.email = 'Email address is invalid';
    if (!values.password) errors.password = 'Password is required';
    return errors;
};

const useForm = (initialValues, onSubmit) => {
    const [values, setValues] = useState(initialValues);
    const [errors, setErrors] = useState({});
    const [isSubmitting, setIsSubmitting] = useState(false);

    const handleChange = (e) => {
        const { name, value } = e.target;
        setValues((prevValues) => ({ ...prevValues, [name]: value }));
    };

    const handleSubmit = (e) => {
        e.preventDefault();
        setErrors(validate(values)); // Validasi form
        setIsSubmitting(true);
    };

    useEffect(() => {
        if (isSubmitting && Object.keys(errors).length === 0) {
            onSubmit(values); // Call submit handler if no errors
            setIsSubmitting(false);
        }
    }, [errors, isSubmitting, values, onSubmit]);

    return { values, errors, handleChange, handleSubmit };
};

export default useForm;
