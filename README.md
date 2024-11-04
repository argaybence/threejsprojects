# Three.js Telepítése

## Előkészületek

A Three.js használatához szükségünk van a Node.js telepítésére. Letöltési link: [Node.js letöltése](https://nodejs.org/en/download/source-code)

Telepítés után ellenőrizzük az `npm` telepítettségét az alábbi paranccsal:

```bash
npm -v
```

Ha ez a parancs egy verziószámmal tér vissza, akkor sikeresen feltelepítettük a Node.js-t és az npm-et.

## HTTP-szerver Telepítése

Telepítsük a `http-server` csomagot, amellyel élőben követhetjük a weboldalunk fejlesztését. Ehhez adjuk ki a következő parancsot:

```bash
npm install -g http-server
```

### Használat

A terminálban navigáljunk el a projekt mappájába, és ott adjuk ki az alábbi parancsot a szerver elindításához:

```bash
http-server .
```

## A Projekt Létrehozása

Hozzuk létre a projektet, vagy ha már létezik, akkor a terminálban navigáljunk el a projekt elérési útvonalához, és adjuk ki a következő parancsokat:

```bash
npm init -y
npm install three
```

### Telepítés Ellenőrzése

Az alábbi paranccsal ellenőrizhetjük, hogy sikeresen feltelepült-e a Three.js:

```bash
npm list
```

### Kimenet:

```plaintext
YourProject@1.0.0 C:\Users\youruser\YourPath\YourProject\
`-- three@0.170.0
```

## Three.js Használata

### Three.js Betöltése `<script>` Tag-gel

Az index.html fájlban a következő módon adhatjuk hozzá a Three.js-t:

```html
<script type="module">
    import * as THREE from './node_modules/three/build/three.module.js';

    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(30, window.innerWidth / window.innerHeight, 0.1, 1000);

    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight);
    document.body.appendChild(renderer.domElement);

    const geometry = new THREE.BoxGeometry();
    const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
    const cube = new THREE.Mesh(geometry, material);
    scene.add(cube);

    camera.position.z = 5;

    function animate() {
        requestAnimationFrame(animate);
        cube.rotation.x += 0.01;
        cube.rotation.y += 0.01;
        renderer.render(scene, camera);
    }
    animate();
</script>
```

### Three.js Betöltése Külső Fájlból

Az index.html fájlban a következő módon hivatkozhatunk a külső fájlra:

```html
<script type="module" src="main.js"></script>
```

A `main.js` fájl tartalma:

```javascript
import * as THREE from './node_modules/three/build/three.module.js';

const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(30, window.innerWidth / window.innerHeight, 0.1, 1000);

const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

const geometry = new THREE.BoxGeometry();
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);

camera.position.z = 5;

function animate() {
    requestAnimationFrame(animate);
    cube.rotation.x += 0.01;
    cube.rotation.y += 0.01;
    renderer.render(scene, camera);
}
animate();
```
