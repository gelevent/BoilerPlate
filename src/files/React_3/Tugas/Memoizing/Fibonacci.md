// Fibonacci.js
import React, { useMemo, useState } from 'react';

// Fungsi untuk menghitung angka Fibonacci (contoh komputasi berat)
const fibonacci = (n) => {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
};

const Fibonacci = () => {
    const [number, setNumber] = useState(0);

    // Menggunakan useMemo untuk mengoptimalkan perhitungan Fibonacci
    const fibNumber = useMemo(() => fibonacci(number), [number]);

    return (
        <div>
            <h1>Fibonacci Calculator</h1>
            <input
                type="number"
                value={number}
                onChange={(e) => setNumber(Number(e.target.value))}
            />
            <p>Fibonacci Number: {fibNumber}</p>
        </div>
    );
};

export default Fibonacci;
