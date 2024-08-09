// formReducer.js
const initialState = {
    name: '',
    email: '',
    password: '',
};

const formReducer = (state, action) => {
    switch (action.type) {
        case 'SET_NAME':
            return { ...state, name: action.payload };
        case 'SET_EMAIL':
            return { ...state, email: action.payload };
        case 'SET_PASSWORD':
            return { ...state, password: action.payload };
        case 'RESET_FORM':
            return initialState;
        default:
            return state;
    }
};

export { initialState, formReducer };
