# Super Mario Adventure

A classic platformer game inspired by Super Mario Bros, built entirely with HTML5, CSS3, and vanilla JavaScript. No external dependencies required!

![Super Mario Adventure](https://img.shields.io/badge/Game-Platformer-red)
![HTML5](https://img.shields.io/badge/HTML5-Canvas-orange)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow)

## 🎮 Game Overview

Super Mario Adventure is a browser-based platformer game featuring:

- **3 Unique Worlds**: Overworld, Underground, and Castle levels
- **Multiple Enemies**: Goombas, Koopas, and the final boss Bowser
- **Power-ups**: Super Mushroom, Fire Flower, Star (invincibility), and 1-UP Mushroom
- **Classic Gameplay**: Jump on enemies, collect coins, hit question blocks
- **Boss Battle**: Face Bowser in World 1-3 to rescue the Princess!
- **Sound Effects**: Retro-style audio using Web Audio API

## 🕹️ Controls

| Action | Keys |
|--------|------|
| Move Left/Right | `←` `→` or `A` `D` |
| Jump | `SPACE`, `↑`, or `W` |
| Crouch | `↓` or `S` |
| Run | Hold `CTRL` |
| Fire (with Fire Flower) | `SHIFT` |

## 🏗️ Architecture

### Project Structure

```
super_mario/
├── index.html      # Main game file (contains all HTML, CSS, and JavaScript)
├── README.md       # This file
└── assets/         # Asset directory (currently unused - all graphics are procedurally generated)
```

### Technical Details

The game is built as a single HTML file containing:

- **HTML**: Game container, UI elements, and overlay screens
- **CSS**: Retro-styled UI with animations and responsive design
- **JavaScript**: Complete game engine including:
  - `SoundEngine`: Web Audio API-based sound system
  - `InputHandler`: Keyboard input management
  - `Particle`: Visual effects system
  - `SpriteRenderer`: Procedural sprite drawing (no image files needed)
  - `Player`: Mario character with physics and power-up states
  - `Enemy`, `Goomba`, `Koopa`: Enemy AI and behavior
  - `Bowser`: Boss character with attack patterns
  - `PowerUp`, `Coin`: Collectible items
  - `Game`: Main game loop, level management, and collision detection

### Key Features

- **Tile-based Level System**: Levels defined as string arrays for easy editing
- **Physics Engine**: Gravity, friction, variable jump height, coyote time
- **Procedural Graphics**: All sprites drawn using Canvas 2D API
- **Collision Detection**: AABB collision with separate X/Y resolution

## 🚀 Deployment

### GitHub Pages

1. Go to your repository on GitHub
2. Navigate to **Settings** → **Pages**
3. Under "Source", select **Deploy from a branch**
4. Select **main** branch and **/ (root)** folder
5. Click **Save**
6. Your game will be available at: `https://[username].github.io/super_mario/`

### External Server Deployment

#### Static File Server (Nginx)

```nginx
server {
    listen 80;
    server_name yourdomain.com;
    root /var/www/super_mario;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
}
```

#### Apache

```apache
<VirtualHost *:80>
    ServerName yourdomain.com
    DocumentRoot /var/www/super_mario
    
    <Directory /var/www/super_mario>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
    </Directory>
</VirtualHost>
```

#### Simple Python Server (Development)

```bash
cd super_mario
python3 -m http.server 8080
# Access at http://localhost:8080
```

#### Node.js (Express)

```javascript
const express = require('express');
const app = express();
app.use(express.static('.')); 
app.listen(8080, () => console.log('Server running on port 8080'));
```

#### Docker

```dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
EXPOSE 80
```

```bash
docker build -t super-mario .
docker run -p 8080:80 super-mario
```

### Cloud Platform Deployment

- **Netlify**: Drag and drop the folder or connect GitHub repo
- **Vercel**: Import from GitHub, auto-deploys on push
- **AWS S3**: Upload files to S3 bucket with static website hosting enabled
- **Firebase Hosting**: Use `firebase deploy` after initialization

## 🎯 Game Tips

- Hold `CTRL` while moving to run faster and jump farther
- Jump on enemies to defeat them (except spikes!)
- Hit question blocks from below to get power-ups
- Fire Flower lets you shoot fireballs with `SHIFT`
- Star makes you invincible - run through enemies!
- Collect 1-UP mushrooms for extra lives

## 📝 Level Format

Levels are defined using character maps:

| Character | Element |
|-----------|---------|
| `1` | Solid block |
| `M` | Mario spawn point |
| `G` | Goal flag |
| `E` | Goomba |
| `K` | Koopa |
| `B` | Bowser (boss) |
| `?` | Question block |
| `C` | Coin |
| `P` | Pipe |
| `3` | Spikes |
| ` ` | Empty space |

## 🛠️ Browser Compatibility

- Chrome (recommended)
- Firefox
- Safari
- Edge

Requires JavaScript enabled and Web Audio API support.

## 📄 License

This project is created for educational purposes. Super Mario is a trademark of Nintendo.

## 🤝 Contributing

Feel free to fork this repository and submit pull requests for:
- New levels
- Additional enemies
- New power-ups
- Bug fixes
- Performance improvements

---

**Enjoy the game! 🍄**
