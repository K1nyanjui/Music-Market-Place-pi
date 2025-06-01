# Music-Market-Place-pi
An app that will allow music artist in our ecosytem to get their music to the outside world
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Music Market Place</title>
    <script>
      window.pi = window.pi || {};
      window.pi.sandbox = true;
    </script>
    <script src="https://sdk.minepi.com/pi-sdk.js"></script>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
import React, { useState } from 'react';
import './App.css';

function App() {
  const [user, setUser] = useState(null);

  const handleLogin = async () => {
    try {
      const scopes = ['username'];
      const user = await window.Pi.authenticate(scopes, onIncompletePaymentFound);
      setUser(user);
      console.log('Authenticated user:', user);
    } catch (err) {
      console.error(err);
    }
  };

  const onIncompletePaymentFound = (payment) => {
    console.log('Incomplete payment found:', payment);
  };

  return (
    <div className="App">
      <h1>🎵 Music Market Place</h1>
      {!user ? (
        <button onClick={handleLogin}>Login with Pi</button>
      ) : (
        <p>Welcome, {user.username}!</p>
      )}
    </div>
  );
}

export default App;
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
const express = require('express');
const cors = require('cors');

const app = express();
app.use(cors());
app.use(express.json());

app.get('/', (req, res) => {
  res.json({ message: 'Welcome to the Pi Music Market Place backend' });
});

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(Server running on port ${PORT}));
