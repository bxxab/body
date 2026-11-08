<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>أداة تشريح وتفكيك المجسم 3D</title>
    <style>
        :root {
            --bg-color: #121214;
            --panel-bg: rgba(24, 24, 27, 0.85);
            --accent-color: #3b82f6;
            --text-color: #f3f4f6;
            --text-muted: #9ca3af;
            --border-color: rgba(255, 255, 255, 0.1);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            overflow: hidden;
            height: 100vh;
            display: flex;
        }

        #canvas-container {
            width: 100%;
            height: 100%;
            position: absolute;
            top: 0;
            left: 0;
            z-index: 1;
        }

        /* واجهة المستخدم واللوحات */
        .ui-layer {
            position: relative;
            z-index: 10;
            width: 100%;
            height: 100%;
            pointer-events: none;
            display: flex;
            justify-content: space-between;
            padding: 20px;
        }

        .panel {
            background: var(--panel-bg);
            backdrop-filter: blur(12px);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 20px;
            pointer-events: auto;
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.5);
            max-height: calc(100vh - 40px);
            overflow-y: auto;
        }

        .left-panel {
            width: 320px;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .right-panel {
            width: 280px;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        h1 {
            font-size: 1.25rem;
            font-weight: 700;
            color: #fff;
            margin-bottom: 4px;
        }

        .subtitle {
            font-size: 0.85rem;
            color: var(--text-muted);
        }

        .control-group {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        label {
            font-size: 0.9rem;
            font-weight: 500;
            color: var(--text-color);
            display: flex;
            justify-content: space-between;
        }

        label span {
            color: var(--accent-color);
            font-family: monospace;
        }

        input[type="range"] {
            width: 100%;
            accent-color: var(--accent-color);
            cursor: pointer;
        }

        .btn-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 8px;
        }

        button {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--border-color);
            color: var(--text-color);
            padding: 10px 14px;
            border-radius: 8px;
            font-size: 0.9rem;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.2s ease;
            text-align: center;
        }

        button:hover {
            background: rgba(59, 130, 246, 0.2);
            border-color: var(--accent-color);
        }

        button.active {
            background: var(--accent-color);
            border-color: var(--accent-color);
            color: white;
        }

        .info-card {
            background: rgba(0, 0, 0, 0.2);
            border-radius: 10px;
            padding: 12px;
            border: 1px solid var(--border-color);
        }

        .info-title {
            font-size: 0.8rem;
            color: var(--text-muted);
            margin-bottom: 4px;
        }

        .info-value {
            font-size: 1.1rem;
            font-weight: 600;
            color: #fff;
        }

        /* مؤشر التحميل */
        #loader {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--bg-color);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 100;
            transition: opacity 0.5s ease;
        }

        .spinner {
            width: 50px;
            height: 50px;
            border: 4px solid rgba(255,255,255,0.1);
            border-top-color: var(--accent-color);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin-bottom: 15px;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }
    </style>
    <!-- استدعاء مكتبة Three.js و OrbitControls -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.js"></script>
</head>
<body>

    <div id="loader">
        <div class="spinner"></div>
        <div style="font-size: 1rem; color: #9ca3af;">جاري تحميل الأداة ثلاثية الأبعاد...</div>
    </div>

    <div id="canvas-container"></div>

    <div class="ui-layer">
        <!-- لوحة التحكم اليسرى -->
        <div class="panel left-panel">
            <div>
                <h1>تشريح المجسم (Blockout)</h1>
                <div class="subtitle">استعراض تفصيلي لأجزاء الجسم ونسبها</div>
            </div>

            <div class="control-group">
                <label>تفكيك الأجزاء (Exploded View): <span id="explode-val">0%</span></label>
                <input type="range" id="explode-slider" min="0" max="100" value="0">
            </div>

            <div class="control-group">
                <label>أنماط العرض</label>
                <div class="btn-grid">
                    <button id="btn-color" class="active">ألوان قياسية</button>
                    <button id="btn-wire">شبكي (Wireframe)</button>
                    <button id="btn-clay">نمط صلصال (Clay)</button>
                </div>
            </div>

            <div class="control-group">
                <label>إجراءات سريعة</label>
                <div class="btn-grid">
                    <button id="btn-reset">إعادة ضبط الكاميرا</button>
                    <button id="btn-rot">تدوير تلقائي</button>
                </div>
            </div>
        </div>

        <!-- لوحة المعلومات اليمنى -->
        <div class="panel right-panel">
            <div>
                <h1>معلومات القطعة</h1>
                <div class="subtitle">انقر على أي جزء من المجسم</div>
            </div>

            <div class="info-card">
                <div class="info-title">اسم الجزء بالعربية</div>
                <div class="info-value" id="part-name-ar">اختر جزءاً من النموذج</div>
            </div>

addGroup: {
    <div class="info-card">
        <div class="info-title">الاسم التقني (EN)</div>
        <div class="info-value" id="part-name-en">-</div>
    </div>

    <div class="info-card">
        <div class="info-title">نوع المفصل / التوصيل</div>
        <div class="info-value" id="part-joint">-</div>
    </div>
</div>
    </div>

    <script>
        // إعداد المشهد الأساسي لـ Three.js
        const container = document.getElementById('canvas-container');
        const scene = new THREE.Scene();
        scene.fog = new THREE.FogExp2(0x121214, 0.05);

        const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 1000);
        camera.position.set(0, 2, 7);

        const renderer = new THREE.WebGLRenderer({ antialias: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setPixelRatio(window.devicePixelRatio);
        renderer.shadowMap.enabled = true;
        renderer.shadowMap.type = THREE.PCFSoftShadowMap;
        container.appendChild(renderer.domElement);

        const controls = new THREE.OrbitControls(camera, renderer.domElement);
        controls.enableDamping = true;
        controls.dampingFactor = 0.05;
        controls.target.set(0, 0, 0);

        // الإضاءة
        const ambientLight = new THREE.AmbientLight(0xffffff, 0.6);
        scene.add(ambientLight);

        const dirLight = new THREE.DirectionalLight(0xffffff, 0.8);
        dirLight.position.set(5, 10, 7);
        dirLight.castShadow = true;
        scene.add(dirLight);

        const backLight = new THREE.DirectionalLight(0x3b82f6, 0.4);
        backLight.position.set(-5, -5, -5);
        scene.add(backLight);

        // مجموعة المجسم الرئيسي
        const humanGroup = new THREE.Group();
        scene.add(humanGroup);

        // خامات الأجزاء بألوان مطابقة للصورة المرجعية
        const colors = {
            head: 0xef7c7c,      // وردي (الرأس)
            neck: 0x82e0aa,      // أخضر فاتح (الرقبة)
            chest: 0xaf7ac5,     // بنفسجي (الصدر)
            waist: 0x52be80,     // أخضر وسط (الخصر/الحوض)
            pelvis: 0x76d7c4,    // تركواز (أسفل الحوض)
            upperArm: 0x85c1e9,  // أزرق فاتح (أعلى الذراع)
            elbow: 0xf39c12,     // أصفر/برتقالي (المرفق)
            forearm: 0xf1948a,   // وردي داكن (الساعد)
            hand: 0x58d68d,      // أخضر (اليد)
            thigh: 0x2e86c1,     // أزرق (الفخذ)
            shin: 0x52be80,      // أخضر (الساق)
            foot: 0xf5b041       // أصفر/بيج (القدم)
        };

        const materials = {
            color: (c) => new THREE.MeshStandardMaterial({ color: c, roughness: 0.3, metalness: 0.1 }),
            wire: (c) => new THREE.MeshBasicMaterial({ color: c, wireframe: true }),
            clay: () => new THREE.MeshStandardMaterial({ color: 0xcccccc, roughness: 0.7, metalness: 0.0 })
        };

        // دالة مساعدة لإنشاء أجزاء المجسم مع خصائص التفصيل
        const parts = [];

        function createPart(geometry, colorKey, nameAr, nameEn, jointType, pos, explodeDir) {
            const mat = materials.color(colors[colorKey]);
            const mesh = new THREE.Mesh(geometry, mat);
            mesh.position.set(pos[0], pos[1], pos[2]);
            mesh.castShadow = true;
            mesh.receiveShadow = true;

            // بيانات وصفية للقطعة
            mesh.userData = {
                nameAr: nameAr,
                nameEn: nameEn,
                joint: jointType,
                basePos: new THREE.Vector3(pos[0], pos[1], pos[2]),
                explodeDir: new THREE.Vector3(explodeDir[0], explodeDir[1], explodeDir[2]),
                colorKey: colorKey
            };

            humanGroup.add(mesh);
            parts.push(mesh);
            return mesh;
        }

        // بناء أجزاء المجسم البشري بدقة متناهية
        // 1. الرأس والرقبة
        createPart(new THREE.SphereGeometry(0.32, 32, 32), 'head', 'الرأس (الجمجمة)', 'Head Skull', 'مفصل كروي (Ball & Socket)', [0, 2.1, 0], [0, 1.5, 0]);
        createPart(new THREE.CylinderGeometry(0.12, 0.15, 0.3, 16), 'neck', 'الرقبة', 'Neck', 'مفصل محوري (Pivot)', [0, 1.75, 0], [0, 1.2, 0]);

        // 2. الجذع والصدر
        createPart(new THREE.CylinderGeometry(0.35, 0.28, 0.6, 16), 'chest', 'الصدر والأضلاع', 'Chest & Thorax', 'ثابت / شبه مرن', [0, 1.3, 0], [0, 0.7, 0]);
        createPart(new THREE.SphereGeometry(0.22, 16, 16), 'waist', 'منطقة الخصر', 'Waist Core', 'مفصل كروي مركزي', [0, 0.85, 0], [0, 0.3, 0]);
        createPart(new THREE.CylinderGeometry(0.28, 0.32, 0.35, 16), 'pelvis', 'الحوض', 'Pelvis / Hips', 'قاعدة التوازن', [0, 0.55, 0], [0, 0, 0]);

        // 3. الذراع اليمنى
        createPart(new THREE.SphereGeometry(0.12, 16, 16), 'upperArm', 'مفصل الكتف الأيمن', 'Right Shoulder', 'مفصل كروي', [-0.5, 1.4, 0], [-1.2, 0.7, 0]);
        createPart(new THREE.CylinderGeometry(0.1, 0.08, 0.45, 16), 'upperArm', 'عضد الذراع الأيمن', 'Right Upper Arm', 'مفصل مفصلي', [-0.65, 1.05, 0], [-1.5, 0.5, 0]);
        createPart(new THREE.SphereGeometry(0.09, 16, 16), 'elbow', 'مفصل المرفق الأيمن', 'Right Elbow', 'مفصل رزي (Hinge)', [-0.75, 0.75, 0], [-1.8, 0.3, 0]);
        createPart(new THREE.CylinderGeometry(0.08, 0.06, 0.4, 16), 'forearm', 'ساعد الذراع الأيمن', 'Right Forearm', 'محوري دوراني', [-0.85, 0.45, 0], [-2.1, 0.1, 0]);
        createPart(new THREE.BoxGeometry(0.1, 0.18, 0.05), 'hand', 'اليد اليمنى', 'Right Hand', 'مفصل الرسغ', [-0.92, 0.18, 0], [-2.4, 0, 0]);

        // 4. الذراع اليسرى
        createPart(new THREE.SphereGeometry(0.12, 16, 16), 'upperArm', 'مفصل الكتف الأيسر', 'Left Shoulder', 'مفصل كروي', [0.5, 1.4, 0], [1.2, 0.7, 0]);
        createPart(new THREE.CylinderGeometry(0.1, 0.08, 0.45, 16), 'upperArm', 'عضد الذراع الأيسر', 'Left Upper Arm', 'مفصل مفصلي', [0.65, 1.05, 0], [1.5, 0.5, 0]);
        createPart(new THREE.SphereGeometry(0.09, 16, 16), 'elbow', 'مفصل المرفق الأيسر', 'Left Elbow', 'مفصل رزي (Hinge)', [0.75, 0.75, 0], [1.8, 0.3, 0]);
        createPart(new THREE.CylinderGeometry(0.08, 0.06, 0.4, 16), 'forearm', 'ساعد الذراع الأيسر', 'Left Forearm', 'محوري دوراني', [0.85, 0.45, 0], [2.1, 0.1, 0]);
        createPart(new THREE.BoxGeometry(0.1, 0.18, 0.05), 'hand', 'اليد اليسرى', 'Left Hand', 'مفصل الرسغ', [0.92, 0.18, 0], [2.4, 0, 0]);

        // 5. الساق اليمنى
        createPart(new THREE.CylinderGeometry(0.15, 0.12, 0.7, 16), 'thigh', 'الفخذ الأيمن', 'Right Thigh', 'مفصل الورك (Hip Joint)', [-0.22, -0.05, 0], [-0.5, -0.8, 0]);
        createPart(new THREE.CylinderGeometry(0.11, 0.09, 0.65, 16), 'shin', 'الساق الأيمن (الظنبوب)', 'Right Shin', 'مفصل الركبة (Knee)', [-0.22, -0.75, 0], [-0.5, -1.6, 0]);
        createPart(new THREE.BoxGeometry(0.12, 0.08, 0.25), 'foot', 'القدم اليمنى', 'Right Foot', 'مفصل الكاحل (Ankle)', [-0.22, -1.15, 0.05], [-0.5, -2.1, 0.2]);

        // 6. الساق اليسرى
        createPart(new THREE.CylinderGeometry(0.15, 0.12, 0.7, 16), 'thigh', 'الفخذ الأيسر', 'Left Thigh', 'مفصل الورك (Hip Joint)', [0.22, -0.05, 0], [0.5, -0.8, 0]);
        createPart(new THREE.CylinderGeometry(0.11, 0.09, 0.65, 16), 'shin', 'الساق الأيسر (الظنبوب)', 'Left Shin', 'مفصل الركبة (Knee)', [0.22, -0.75, 0], [0.5, -1.6, 0]);
        createPart(new THREE.BoxGeometry(0.12, 0.08, 0.25), 'foot', 'القدم اليسرى', 'Left Foot', 'مفصل الكاحل (Ankle)', [0.22, -1.15, 0.05], [0.5, -2.1, 0.2]);

        // التفاعل والنقر (Raycasting)
        const raycaster = new THREE.Raycaster();
        const mouse = new THREE.Vector2();
        let selectedMesh = null;

        window.addEventListener('click', (event) => {
            // تجاهل النقر إذا كان على لوحات التحكم
            if (event.clientX < 340 || event.clientX > window.innerWidth - 300) return;

            mouse.x = (event.clientX / window.innerWidth) * 2 - 1;
            mouse.y = -(event.clientY / window.innerHeight) * 2 + 1;

            raycaster.setFromCamera(mouse, camera);
            const intersects = raycaster.intersectObjects(parts);

            if (intersects.length > 0) {
                const hit = intersects[0].object;
                highlightPart(hit);
            }
        });

        function highlightPart(mesh) {
            parts.forEach(p => {
                if (currentMode === 'color') {
                    p.material = materials.color(colors[p.userData.colorKey]);
                } else if (currentMode === 'wire') {
                    p.material = materials.wire(colors[p.userData.colorKey]);
                } else {
                    p.material = materials.clay();
                }
            });

            selectedMesh = mesh;
            mesh.material = new THREE.MeshStandardMaterial({
                color: 0x3b82f6,
                emissive: 0x1d4ed8,
                roughness: 0.2
            });

            document.getElementById('part-name-ar').innerText = mesh.userData.nameAr;
            document.getElementById('part-name-en').innerText = mesh.userData.nameEn;
            document.getElementById('part-joint').innerText = mesh.userData.joint;
        }

        // تفاعل شريط التفكيك (Exploded View)
        const explodeSlider = document.getElementById('explode-slider');
        const explodeVal = document.getElementById('explode-val');

        explodeSlider.addEventListener('input', (e) => {
            const val = e.target.value / 100;
            explodeVal.innerText = e.target.value + '%';

            parts.forEach(p => {
                p.position.copy(p.userData.basePos).addScaledVector(p.userData.explodeDir, val * 1.2);
            });
        });

        // أنماط العرض
        let currentMode = 'color';
        document.getElementById('btn-color').addEventListener('click', () => setMode('color', 'btn-color'));
        document.getElementById('btn-wire').addEventListener('click', () => setMode('wire', 'btn-wire'));
        document.getElementById('btn-clay').addEventListener('click', () => setMode('clay', 'btn-clay'));

        function setMode(mode, btnId) {
            currentMode = mode;
            document.querySelectorAll('.btn-grid button').forEach(b => {
                if(b.id.startsWith('btn-') && (b.id === 'btn-color' || b.id === 'btn-wire' || b.id === 'btn-clay')) {
                    b.classList.remove('active');
                }
            });
            document.getElementById(btnId).classList.add('active');

            parts.forEach(p => {
                if (p === selectedMesh) return; // الحفاظ على تمييز القطعة المحددة
                if (mode === 'color') {
                    p.material = materials.color(colors[p.userData.colorKey]);
                } else if (mode === 'wire') {
                    p.material = materials.wire(colors[p.userData.colorKey]);
                } else {
                    p.material = materials.clay();
                }
            });
        }

        // أزرار التحكم الإضافية
        document.getElementById('btn-reset').addEventListener('click', () => {
            camera.position.set(0, 2, 7);
            controls.target.set(0, 0, 0);
        });

        let isRotating = false;
        document.getElementById('btn-rot').addEventListener('click', (e) => {
            isRotating = !isRotating;
            e.target.classList.toggle('active', isRotating);
        });

        // إخفاء مؤشر التحميل عند الجاهزية
        window.addEventListener('load', () => {
            setTimeout(() => {
                const loader = document.getElementById('loader');
                loader.style.opacity = '0';
                setTimeout(() => loader.style.display = 'none', 500);
            }, 600);
        });

        // حلقة الرسم والتحديث (Render Loop)
        function animate() {
            requestAnimationFrame(animate);

            if (isRotating) {
                humanGroup.rotation.y += 0.005;
            }

            controls.update();
            renderer.render(scene, camera);
        }

        animate();

        // التجاوب مع تغيير حجم النافذة
        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });
    </script>
</body>
</html>
