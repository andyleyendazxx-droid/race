<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard Escolar Pro</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <script src="https://rawgit.com/schmich/instascan-builds/master/instascan.min.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; transition: background-color 0.3s, color 0.3s; }
    </style>
</head>
<body class="bg-gray-50 text-gray-900 dark:bg-gray-950 dark:text-gray-100 min-h-screen">

    <div class="flex flex-col md:flex-row min-h-screen">
        
        <aside class="w-full md:w-64 bg-white dark:bg-gray-900 border-b md:border-b-0 md:border-r border-gray-200 dark:border-gray-800 p-5 flex flex-col justify-between shrink-0">
            <div>
                <div class="flex items-center gap-3 mb-6">
                    <div class="p-2 bg-indigo-600 rounded-xl text-white">
                        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 14l9-5-9-5-9 5 9 5z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 14l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14z"/></svg>
                    </div>
                    <div>
                        <h1 class="text-md font-bold tracking-tight">EduControl</h1>
                        <p class="text-xs text-gray-500 dark:text-gray-400">Dashboard de Asistencia</p>
                    </div>
                </div>

                <button onclick="toggleDarkMode()" class="w-full flex items-center justify-center gap-2 mb-6 py-2 px-4 rounded-xl border border-gray-200 dark:border-gray-800 hover:bg-gray-50 dark:hover:bg-gray-800 text-sm font-medium transition cursor-pointer">
                    <span class="dark:hidden flex items-center gap-2">🌙 Modo Oscuro</span>
                    <span class="hidden dark:flex items-center gap-2">☀️ Modo Claro</span>
                </button>

                <div class="space-y-2">
                    <p class="text-xs font-semibold uppercase tracking-wider text-gray-400 mb-2">Acciones</p>
                    <button onclick="exportarBackup()" class="w-full flex items-center gap-3 px-3 py-2.5 rounded-xl bg-emerald-600 hover:bg-emerald-700 text-white text-sm font-medium transition shadow-sm cursor-pointer">
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7H5a2 2 0 00-2 2v9a2 2 0 002 2h14a2 2 0 002-2V9a2 2 0 00-2-2h-3m-1 4l-3 3m0 0l-3-3m3 3V4"/></svg>
                        Exportar Backup (.js)
                    </button>
                </div>
            </div>
            
            <div class="text-xs text-gray-400 pt-4 border-t border-gray-100 dark:border-gray-800 mt-6 md:mt-0">
                Versión Pro v2.1
            </div>
        </aside>

        <main class="flex-1 p-4 md:p-8 space-y-6 max-w-7xl mx-auto w-full overflow-hidden">
            
            <section class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                <div class="bg-white dark:bg-gray-900 rounded-2xl border border-gray-200 dark:border-gray-800 p-5 shadow-sm flex flex-col justify-between">
                    <div>
                        <h2 class="text-sm font-semibold uppercase tracking-wider text-gray-400 mb-3 flex items-center gap-2">
                            <span class="inline-block w-2 h-2 rounded-full bg-indigo-600 animate-pulse"></span> Escáner QR de Entrada
                        </h2>
                        <div class="relative bg-gray-900 rounded-xl overflow-hidden aspect-video flex items-center justify-center text-center">
                            <video id="preview" class="w-full h-full object-cover"></video>
                            <div id="scanner-placeholder" class="absolute inset-0 bg-gray-900/95 flex flex-col items-center justify-center p-4">
                                <svg class="w-8 h-8 text-gray-500 animate-bounce mb-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z"/></svg>
                                <p class="text-xs text-gray-400">Solicitando acceso a la cámara...</p>
                            </div>
                        </div>
                    </div>
                    <p class="text-[11px] text-gray-400 dark:text-gray-500 mt-3">Sostén el código QR del alumno frente a la cámara frontal o trasera.</p>
                </div>

                <div class="lg:col-span-2 bg-white dark:bg-gray-900 rounded-2xl border border-gray-200 dark:border-gray-800 p-5 shadow-sm">
                    <h2 class="text-sm font-semibold uppercase tracking-wider text-gray-400 mb-4">🔍 Búsqueda y Filtros Globales</h2>
                    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                        <div class="sm:col-span-3">
                            <label class="block text-xs font-medium text-gray-500 mb-1">Buscar por descripción, notas o nombre</label>
                            <input type="text" id="filtro-buscar" oninput="renderizarAsistencias()" placeholder="Escribe el nombre del alumno o tipo de estado..." class="w-full p-2.5 bg-gray-50 dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-xl text-sm focus:outline-none focus:border-indigo-500 transition">
                        </div>
                        <div>
                            <label class="block text-xs font-medium text-gray-500 mb-1">Filtrar por Fecha</label>
                            <input type="date" id="filtro-fecha" onchange="renderizarAsistencias()" class="w-full p-2.5 bg-gray-50 dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-xl text-sm focus:outline-none focus:border-indigo-500 transition">
                        </div>
                        <div>
                            <label class="block text-xs font-medium text-gray-500 mb-1">Categoría</label>
                            <select id="filtro-categoria" onchange="renderizarAsistencias()" class="w-full p-2.5 bg-gray-50 dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-xl text-sm focus:outline-none focus:border-indigo-500 transition">
                                <option value="Todos">Todas las carreras</option>
                                <option value="Contabilidad">Contabilidad</option>
                                <option value="Administración">Administración</option>
                            </select>
                        </div>
                        <div class="flex items-end">
                            <button onclick="limpiarFiltros()" class="w-full py-2.5 px-4 bg-gray-100 hover:bg-gray-200 dark:bg-gray-800 dark:hover:bg-gray-700 text-gray-700 dark:text-gray-300 rounded-xl text-sm font-medium transition cursor-pointer">
                                Limpiar Filtros
                            </button>
                        </div>
                    </div>
                </div>
            </section>

            <section class="bg-white dark:bg-gray-900 rounded-2xl border border-gray-200 dark:border-gray-800 shadow-sm overflow-hidden">
                <div class="p-5 border-b border-gray-100 dark:border-gray-800 flex flex-col sm:flex-row justify-between items-start sm:items-center gap-3">
                    <div>
                        <h2 class="text-lg font-bold">Base de Alumnos (20 Registrados)</h2>
                        <p class="text-xs text-gray-400">Gestión de datos de alumnos matriculados</p>
                    </div>
                    <button onclick="agregarEstudianteForm()" class="px-4 py-2 bg-indigo-600 hover:bg-indigo-700 text-white rounded-xl text-xs font-semibold transition shadow-sm cursor-pointer">
                        + Agregar Estudiante
                    </button>
                </div>
                <div class="overflow-x-auto max-h-72">
                    <table class="w-full text-left border-collapse text-sm">
                        <thead class="bg-gray-50/70 dark:bg-gray-800/50 text-gray-400 text-xs font-semibold uppercase tracking-wider sticky top-0 backdrop-blur-md">
                            <tr>
                                <th class="p-4">ID / Código</th>
                                <th class="p-4">Estudiante</th>
                                <th class="p-4">Especialidad / Categoría</th>
                                <th class="p-4 text-right">Panel de Operaciones</th>
                            </tr>
                        </thead>
                        <tbody id="tabla-estudiantes" class="divide-y divide-gray-100 dark:divide-gray-800">
                            </tbody>
                    </table>
                </div>
            </section>

            <section class="bg-white dark:bg-gray-900 rounded-2xl border border-gray-200 dark:border-gray-800 shadow-sm overflow-hidden">
                <div class="p-5 border-b border-gray-100 dark:border-gray-800 flex flex-col sm:flex-row justify-between items-start sm:items-center gap-3">
                    <div>
                        <h2 class="text-lg font-bold">Bitácora de Asistencia Escolar</h2>
                        <p class="text-xs text-gray-400">Historial completo (Últimos 30 registros precargados)</p>
                    </div>
                    <button onclick="crearAsistenciaManualForm()" class="px-4 py-2 bg-amber-600 hover:bg-amber-700 text-white rounded-xl text-xs font-semibold transition shadow-sm cursor-pointer">
                        + Registrar Asistencia Manual
                    </button>
                </div>
                <div class="overflow-x-auto max-h-96">
                    <table class="w-full text-left border-collapse text-sm">
                        <thead class="bg-gray-50/70 dark:bg-gray-800/50 text-gray-400 text-xs font-semibold uppercase tracking-wider sticky top-0 backdrop-blur-md">
                            <tr>
                                <th class="p-4">Fecha de Registro</th>
                                <th class="p-4">Estudiante</th>
                                <th class="p-4">Categoría</th>
                                <th class="p-4">Estado / Tipo</th>
                                <th class="p-4 text-right">Acciones</th>
                            </tr>
                        </thead>
                        <tbody id="tabla-asistencias" class="divide-y divide-gray-100 dark:divide-gray-800">
                            </tbody>
                    </table>
                </div>
            </section>

        </main>
    </div>

    <script>
        // --- DATA INICIAL REQUERIDA (20 Estudiantes y 30 Históricos) ---
        const estudiantesIniciales = [
            { id: 101, nombre: "Juan Pérez Ramos", categoria: "Contabilidad" },
            { id: 102, nombre: "María Gomez Soler", categoria: "Contabilidad" },
            { id: 103, nombre: "Carlos Flores Mendoza", categoria: "Administración" },
            { id: 104, nombre: "Ana Torres Castro", categoria: "Contabilidad" },
            { id: 105, nombre: "Luis Castillo Vega", categoria: "Administración" },
            { id: 106, nombre: "Sofía Medina Ortiz", categoria: "Contabilidad" },
            { id: 107, nombre: "Diego Peralta Rojas", categoria: "Contabilidad" },
            { id: 108, nombre: "Laura Vega Benítez", categoria: "Administración" },
            { id: 109, nombre: "Pedro Campos Arce", categoria: "Contabilidad" },
            { id: 110, nombre: "Elena Diaz Pardo", categoria: "Administración" },
            { id: 111, nombre: "Miguel Rivas Peña", categoria: "Contabilidad" },
            { id: 112, nombre: "Clara Mendoza Luna", categoria: "Contabilidad" },
            { id: 113, nombre: "Jorge Soto Villarreal", categoria: "Administración" },
            { id: 114, font: "Patricia Lara", nombre: "Patricia Lara Quiroz", categoria: "Contabilidad" },
            { id: 115, nombre: "Roberto Luna Fuentes", categoria: "Administración" },
            { id: 116, nombre: "Natalia Cruz Saldaña", categoria: "Contabilidad" },
            { id: 117, nombre: "Gabriel Rios Tello", categoria: "Contabilidad" },
            { id: 118, nombre: "Lucia Solis Miranda", categoria: "Administración" },
            { id: 119, nombre: "Andrés Silva Duarte", categoria: "Contabilidad" },
            { id: 120, nombre: "Sonia Peña Palacios", categoria: "Administración" }
        ];

        let asistenciasIniciales = [];
        let controlFecha = new Date();
        // Generar exactamente 30 registros históricos interactivos distribuidos
        for (let i = 1; i <= 30; i++) {
            let estudiante = estudiantesIniciales[i % 20];
            let f = new Date(controlFecha);
            f.setDate(f.getDate() - Math.floor(i / 3)); 
            asistenciasIniciales.push({
                id: 2000 + i,
                idEstudiante: estudiante.id,
                fecha: f.toISOString().split('T')[0] + " " + f.toTimeString().split(' ')[0].substring(0,5),
                estado: i % 6 === 0 ? "Tarde" : "Presente"
            });
        }

        // Estado Reactivo LocalStorage
        let estudiantes = JSON.parse(localStorage.getItem('db_estudiantes')) || estudiantesIniciales;
        let asistencias = JSON.parse(localStorage.getItem('db_asistencias')) || asistenciasIniciales;

        function persistir() {
            localStorage.setItem('db_estudiantes', JSON.stringify(estudiantes));
            localStorage.setItem('db_asistencias', JSON.stringify(asistencias));
        }

        // --- MANEJO DEL DISEÑO MODO OSCURO ---
        if (localStorage.getItem('theme') === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
            document.documentElement.classList.add('dark');
        } else {
            document.documentElement.classList.remove('dark');
        }

        function toggleDarkMode() {
            if (document.documentElement.classList.contains('dark')) {
                document.documentElement.classList.remove('dark');
                localStorage.setItem('theme', 'light');
            } else {
                document.documentElement.classList.add('dark');
                localStorage.setItem('theme', 'dark');
            }
        }

        // --- RENDERS DE TABLAS ---
        function renderizarEstudiantes() {
            const listado = document.getElementById('tabla-estudiantes');
            listado.innerHTML = '';
            estudiantes.forEach(est => {
                listado.innerHTML += `
                    <tr class="hover:bg-gray-50/50 dark:hover:bg-gray-800/30 transition">
                        <td class="p-4 font-mono font-semibold text-xs text-indigo-600 dark:text-indigo-400">#${est.id}</td>
                        <td class="p-4 font-medium">${est.nombre}</td>
                        <td class="p-4">
                            <span class="px-2.5 py-1 rounded-lg text-xs font-medium ${est.categoria === 'Contabilidad' ? 'bg-blue-50 text-blue-700 dark:bg-blue-900/30 dark:text-blue-300' : 'bg-purple-50 text-purple-700 dark:bg-purple-900/30 dark:text-purple-300'}">
                                ${est.categoria}
                            </span>
                        </td>
                        <td class="p-4 text-right space-x-3">
                            <button onclick="editarEstudianteForm(${est.id})" class="text-indigo-600 dark:text-indigo-400 hover:underline font-medium text-xs cursor-pointer">Editar</button>
                            <button onclick="eliminarEstudiante(${est.id})" class="text-red-500 hover:underline font-medium text-xs cursor-pointer">Eliminar</button>
                        </td>
                    </tr>
                `;
            });
        }

        function renderizarAsistencias() {
            const listado = document.getElementById('tabla-asistencias');
            const buscarQuery = document.getElementById('filtro-buscar').value.toLowerCase();
            const filtroFecha = document.getElementById('filtro-fecha').value;
            const filtroCat = document.getElementById('filtro-categoria').value;

            listado.innerHTML = '';

            let dataFiltrada = asistencias.filter(asist => {
                let est = estudiantes.find(e => e.id == asist.idEstudiante);
                let nombreAlumno = est ? est.nombre.toLowerCase() : 'eliminado';
                let descEstado = asist.estado.toLowerCase();

                let cumpleMatch = nombreAlumno.includes(buscarQuery) || descEstado.includes(buscarQuery);
                let cumpleFecha = filtroFecha ? asist.fecha.startsWith(filtroFecha) : true;
                let cumpleCat = filtroCat !== "Todos" ? (est && est.categoria === filtroCat) : true;

                return cumpleMatch && cumpleFecha && cumpleCat;
            });

            dataFiltrada.sort((a,b) => b.fecha.localeCompare(a.fecha));

            if(dataFiltrada.length === 0) {
                listado.innerHTML = `<tr><td colspan="5" class="p-8 text-center text-gray-400 text-xs">Ningún registro coincide con los términos de búsqueda establecidos.</td></tr>`;
                return;
            }

            dataFiltrada.forEach(asist => {
                let est = estudiantes.find(e => e.id == asist.idEstudiante);
                listado.innerHTML += `
                    <tr class="hover:bg-gray-50/50 dark:hover:bg-gray-800/30 transition">
                        <td class="p-4 text-xs font-mono text-gray-500">${asist.fecha}</td>
                        <td class="p-4 font-medium">${est ? est.nombre : '<em class="text-gray-400">Alumno Retirado</em>'}</td>
                        <td class="p-4 text-xs text-gray-500">${est ? est.categoria : '-'}</td>
                        <td class="p-4">
                            <span class="px-2.5 py-0.5 rounded-full text-xs font-semibold ${asist.estado === 'Presente' ? 'bg-emerald-50 text-emerald-700 dark:bg-emerald-900/20 dark:text-emerald-400' : 'bg-amber-50 text-amber-700 dark:bg-amber-900/20 dark:text-amber-400'}">
                                ${asist.estado}
                            </span>
                        </td>
                        <td class="p-4 text-right space-x-2">
                            <button onclick="editarAsistenciaForm(${asist.id})" class="text-gray-400 hover:text-gray-700 dark:hover:text-gray-200 text-xs cursor-pointer">Editar</button>
                            <button onclick="eliminarAsistencia(${asist.id})" class="text-red-400 hover:text-red-600 text-xs cursor-pointer">❌</button>
                        </td>
                    </tr>
                `;
            });
        }

        function limpiarFiltros() {
            document.getElementById('filtro-buscar').value = '';
            document.getElementById('filtro-fecha').value = '';
            document.getElementById('filtro-categoria').value = 'Todos';
            renderizarAsistencias();
        }

        // --- CRUD INTERACTIVO ESTUDIANTES ---
        async function agregarEstudianteForm() {
            const { value: res } = await Swal.fire({
                title: 'Matricular Estudiante',
                html: `
                    <input id="add-id" type="number" placeholder="Código ID Único (Numérico)" class="swal2-input">
                    <input id="add-nombre" type="text" placeholder="Apellidos y Nombres" class="swal2-input">
                    <select id="add-cat" class="swal2-input"><option value="Contabilidad">Contabilidad</option><option value="Administración">Administración</option></select>
                `,
                confirmButtonText: 'Registrar Alumno',
                focusConfirm: false,
                preConfirm: () => ({
                    id: parseInt(document.getElementById('add-id').value),
                    nombre: document.getElementById('add-nombre').value,
                    categoria: document.getElementById('add-cat').value
                })
            });

            if (res) {
                if(!res.id || !res.nombre) return Swal.fire('Incompleto', 'Rellena todos los campos.', 'warning');
                if(estudiantes.some(e => e.id === res.id)) return Swal.fire('Error ID', 'Este código ya pertenece a un estudiante', 'error');
                
                estudiantes.push(res);
                persistir(); renderizarEstudiantes();
                Swal.fire('Éxito', 'Estudiante añadido correctamente', 'success');
            }
        }

        async function editarEstudianteForm(id) {
            let est = estudiantes.find(e => e.id === id);
            const { value: res } = await Swal.fire({
                title: 'Modificar Datos',
                html: `
                    <input id="edit-nombre" type="text" value="${est.nombre}" class="swal2-input">
                    <select id="edit-cat" class="swal2-input">
                        <option value="Contabilidad" ${est.categoria === 'Contabilidad' ? 'selected' : ''}>Contabilidad</option>
                        <option value="Administración" ${est.categoria === 'Administración' ? 'selected' : ''}>Administración</option>
                    </select>
                `,
                confirmButtonText: 'Guardar Cambios',
                preConfirm: () => ({
                    nombre: document.getElementById('edit-nombre').value,
                    categoria: document.getElementById('edit-cat').value
                })
            });

            if(res) {
                est.nombre = res.nombre;
                est.categoria = res.categoria;
                persistir(); renderizarEstudiantes(); renderizarAsistencias();
            }
        }

        function eliminarEstudiante(id) {
            Swal.fire({
                title: '¿Remover Alumno?',
                text: "El estudiante será dado de baja del listado activo.",
                icon: 'warning',
                showCancelButton: true,
                confirmButtonColor: '#ef4444',
                confirmButtonText: 'Eliminar'
            }).then(r => {
                if(r.isConfirmed) {
                    estudiantes = estudiantes.filter(e => e.id !== id);
                    persistir(); renderizarEstudiantes(); renderizarAsistencias();
                }
            });
        }

        // --- CONTROL DE ASISTENCIAS QR / MANUAL ---
        function procesarEntradaQR(idEscaneado) {
            let alumno = estudiantes.find(e => e.id == idEscaneado);
            if(!alumno) {
                Swal.fire('No Reconocido', 'El ID del código QR no existe en la base.', 'error');
                return;
            }
            let ahora = new Date();
            asistencias.push({
                id: Date.now(),
                idEstudiante: alumno.id,
                fecha: ahora.toISOString().split('T')[0] + " " + ahora.toTimeString().split(' ')[0].substring(0,5),
                estado: "Presente"
            });
            persistir(); renderizarAsistencias();
            Swal.fire({ title: 'Entrada Registrada', text: alumno.nombre, icon: 'success', timer: 1500, showConfirmButton: false });
        }

        async function crearAsistenciaManualForm() {
            let options = estudiantes.map(e => `<option value="${e.id}">${e.nombre}</option>`).join('');
            let hoy = new Date().toISOString().split('T')[0];
            const { value: res } = await Swal.fire({
                title: 'Asistencia Manual',
                html: `
                    <select id="man-est" class="swal2-input">${options}</select>
                    <input id="man-fecha" type="datetime-local" class="swal2-input" value="${hoy}T08:00">
                    <select id="man-estd" class="swal2-input"><option value="Presente">Presente</option><option value="Tarde">Tarde</option></select>
                `,
                preConfirm: () => ({
                    idEstudiante: parseInt(document.getElementById('man-est').value),
                    fecha: document.getElementById('man-fecha').value.replace('T', ' '),
                    estado: document.getElementById('man-estd').value
                })
            });

            if(res) {
                res.id = Date.now();
                asistencias.push(res);
                persistir(); renderizarAsistencias();
            }
        }

        async function editarAsistenciaForm(id) {
            let asist = asistencias.find(a => a.id === id);
            let convFecha = asist.fecha.replace(' ', 'T');
            const { value: res } = await Swal.fire({
                title: 'Editar Estado',
                html: `
                    <input id="edit-as-fecha" type="datetime-local" value="${convFecha}" class="swal2-input">
                    <select id="edit-as-estd" class="swal2-input">
                        <option value="Presente" ${asist.estado === 'Presente' ? 'selected' : ''}>Presente</option>
                        <option value="Tarde" ${asist.estado === 'Tarde' ? 'selected' : ''}>Tarde</option>
                    </select>
                `,
                preConfirm: () => ({
                    fecha: document.getElementById('edit-as-fecha').value.replace('T', ' '),
                    estado: document.getElementById('edit-as-estd').value
                })
            });
            if(res) {
                asist.fecha = res.fecha;
                asist.estado = res.estado;
                persistir(); renderizarAsistencias();
            }
        }

        function eliminarAsistencia(id) {
            asistencias = asistencias.filter(a => a.id !== id);
            persistir(); renderizarAsistencias();
        }

        // --- EXPORTAR RESPALDO BACKUP (.JS) ---
        function exportarBackup() {
            let contenido = `/** BACKUP DE DATOS GENERADO AUTOMÁTICAMENTE **/\n\n`;
            contenido += `const BackupEstudiantes = ${JSON.stringify(estudiantes, null, 4)};\n\n`;
            contenido += `const BackupAsistencias = ${JSON.stringify(asistencias, null, 4)};\n`;
            
            const blob = new Blob([contenido], { type: 'text/javascript' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `backup_sistema_${new Date().toISOString().split('T')[0]}.js`;
            a.click();
            URL.revokeObjectURL(url);
        }

        // --- INICIALIZADOR DE CÁMARA E INSTASCAN ---
        window.addEventListener('DOMContentLoaded', () => {
            renderizarEstudiantes();
            renderizarAsistencias();

            let scanner = new Instascan.Scanner({ video: document.getElementById('preview'), mirror: false });
            scanner.addListener('scan', function (content) {
                if (content) procesarEntradaQR(content.trim());
            });

            Instascan.Camera.getCameras().then(function (cameras) {
                if (cameras.length > 0) {
                    document.getElementById('scanner-placeholder').style.display = 'none';
                    // Selecciona la cámara trasera en móviles por defecto si existe
                    let backCam = cameras.find(c => c.name.toLowerCase().includes('back') || c.name.toLowerCase().includes('trasera'));
                    scanner.start(backCam || cameras[0]);
                } else {
                    document.getElementById('scanner-placeholder').innerHTML = "<p class='text-xs text-red-400 p-2'>Cámara no detectada.</p>";
                }
            }).catch(function (e) {
                console.error(e);
                document.getElementById('scanner-placeholder').innerHTML = "<p class='text-xs text-red-400 p-2'>Permisos denegados.</p>";
            });
        });
    </script>
</body>
</html>
