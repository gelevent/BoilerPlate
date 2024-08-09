// Form.js
import React, { useReducer } from 'react';
import { formReducer, initialState } from './formReducer';

const Form = () => {
    const [state, dispatch] = useReducer(formReducer, initialState);

    const handleChange = (e) => {
        const { name, value } = e.target;
        dispatch({ type: `SET_${name.toUpperCase()}`, payload: value });
    };

    const handleSubmit = (e) => {
        e.preventDefault();
        // Lakukan sesuatu dengan state, seperti mengirim data ke server
        console.log('Form submitted:', state);
    };

    return (
        <form onSubmit={handleSubmit}>
            <div>
                <label>Name:</label>
                <input
                    type="text"
                    name="name"
                    value={state.name}
                    onChange={handleChange}
                />
            </div>
            <div>
                <label>Email:</label>
                <input
                    type="email"
                    name="email"
                    value={state.email}
                    onChange={handleChange}
                />
            </div>
            <div>
                <label>Password:</label>
                <input
                    type="password"
                    name="password"
                    value={state.password}
                    onChange={handleChange}
                />
            </div>
            <button type="submit">Submit</button>
            <button
                type="button"
                onClick={() => dispatch({ type: 'RESET_FORM' })}
            >
                Reset
            </button>
        </form>
    );
};

export default Form;
