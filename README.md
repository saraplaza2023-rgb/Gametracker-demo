# Gametracker-demo
Sistema de gestión de biblioteca para juegos 
# Gametracker-demo 🎮
Sistema de gestión de biblioteca para juegos.

## 🚀 Funcionalidades
- Registrar videojuegos en tu colección.
- Organizar títulos por estado (jugando, completado, pendiente).
- Llevar seguimiento de progreso y reseñas.

## 🛠️ Tecnologías
- **Frontend**: React (JSX)
- **Backend**: Node.js + Express
- **Base de datos**: MongoDB (Mongoose)
- **Comunicación**: API REST con JSON

## 📦 Instalación
```bash
# Clonar el repositorio
git clone https://github.com/saraplaza2023-rgb/Gametracker-demo.git

# Instalar dependencias
npm install

# Ejecutar servidor
npm start


// server.js
const express = require('express');
const mongoose = require('mongoose');
const app = express();

app.use(express.json());

// Conexión a MongoDB
mongoose.connect('mongodb://localhost:27017/gametracker');

// Modelo de juego
const Game = mongoose.model('Game', {
  title: String,
  status: String, // jugando, completado, pendiente
});

// Rutas
app.get('/api/games', async (req, res) => {
  const games = await Game.find();
  res.json(games);
});

app.post('/api/games', async (req, res) => {
  const game = new Game(req.body);
  await game.save();
  res.json(game);
});

app.listen(3000, () => console.log('Servidor en http://localhost:3000'));
