// ThemedComponent.js
import React, { useContext } from 'react';
import { ThemeContext } from './ThemeContext';

const ThemedComponent = () => {
    const { theme } = useContext(ThemeContext);
    const style = {
        backgroundColor: theme === 'light' ? '#fff' : '#333',
        color: theme === 'light' ? '#000' : '#fff',
        padding: '30vh',
        borderRadius: '5px',
    };

    return (
        <div style={style}>
            The current theme is {theme}.
        </div>
    );
};

export default ThemedComponent;
