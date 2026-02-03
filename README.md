"use client";

import { useState } from "react";

const products = [
  { id: 1, name: "T-Shirt", price: 20 },
  { id: 2, name: "Shoes", price: 50 },
  { id: 3, name: "Cap", price: 10 },
];

export default function Home() {
  const [cart, setCart] = useState<any[]>([]);

  const addToCart = (product: any) => {
    setCart([...cart, product]);
  };

  return (
    <div>
      <h2>Products</h2>

      {products.map((p) => (
        <div key={p.id} style={{ marginBottom: 10 }}>
          <strong>{p.name}</strong> – ${p.price}
          <br />
          <button onClick={() => addToCart(p)}>Add to Cart</button>
        </div>
      ))}

      <hr />

      <h2>Cart</h2>
      {cart.length === 0 && <p>Cart is empty</p>}

      {cart.map((item, i) => (
        <p key={i}>
          {item.name} – ${item.price}
        </p>
      ))}
    </div>
  );
}
