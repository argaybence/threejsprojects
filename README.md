Threejs telepítése:

    Szükségünk van a nodejs-re. Link: https://nodejs.org/en/download/source-code

    Ha npm -v egy valós verzió számmal tér vissza, akkor sikeresen feltelepítettük.
    Telepítsük a http-server ?alcsomagot? amellyel élőben tudjuk követni majd a
    weboldalunk építését. Ehhez adjuk ki a következő parancsot:
        npm install -g http-server
    Használat:
        Terminálba navigáljunk el a projekt mappába, és ott adjuk ki a következő parancsot:
            http-server .

    Hozzuk létra a projektünket, vagy ha már létezik, akkor a terminálba navigáljunk el
    a projekt elérési útvonalához, és adjuk ki a következő parancsokat:
        npm init -y
        npm install three
    
    A következő paranccsal tudjuk ellenőrizni, hogy valóban feltelepült-e a threejs:
        npm list
    Kimenet:
        YourProject@1.0.0 C:\Users\youruser\YourPath\YourProject\
        `-- three@0.170.0
    


Threejs használata:

    A <script> tag használata:
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


    Külső fájl beimportálva:
        Az index.html-ben:
            <script type="module" src="main.js"></script>
        
        A main.js-ben:
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


