<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Buzón de Ideas para Bot de WhatsApp</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        body { font-family: 'Inter', sans-serif; }
    </style>
</head>
<body class="bg-gray-100 min-h-screen p-4">

    <div id="loading-container" class="flex justify-center items-center h-screen">
        <div class="text-xl font-semibold text-gray-700">Cargando aplicación...</div>
    </div>

    <div id="app-container" class="hidden w-full max-w-2xl mx-auto bg-white shadow-xl rounded-xl p-6 md:p-8">
        
        <header class="mb-8 border-b pb-4">
            <h1 class="text-3xl font-extrabold text-indigo-700 text-center">Buzón de Ideas para tu Bot de WhatsApp</h1>
            <p class="text-gray-500 text-center mt-1">Comparte tus sugerencias de funciones o canciones. ¡Todo es público!</p>
            <div id="user-id-display" class="hidden text-xs text-center text-gray-400 mt-3 p-1 bg-gray-50 rounded">
                Tu ID de Usuario: <span id="user-id-span" class="font-mono text-gray-600 break-all"></span>
            </div>
        </header>

        <section class="mb-10">
            <h2 class="text-xl font-bold text-gray-700 mb-4">Sube una Sugerencia</h2>
            <form id="suggestion-form" class="flex flex-col space-y-4">
                <textarea
                    id="new-suggestion-input"
                    placeholder="Escribe tu sugerencia (nueva función o canción)..."
                    maxlength="300"
                    rows="3"
                    class="w-full p-3 border border-gray-300 rounded-lg focus:ring-indigo-500 focus:border-indigo-500 transition duration-150 ease-in-out resize-none"
                    required
                ></textarea>
                <div class="text-right text-sm text-gray-400">
                    <span id="char-count">0</span>/300 caracteres
                </div>
                <button
                    type="submit"
                    id="submit-button"
                    class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-3 px-4 rounded-lg shadow-md transition duration-200 ease-in-out disabled:bg-indigo-300 disabled:cursor-not-allowed flex justify-center items-center"
                >
                    Enviar Sugerencia
                </button>
            </form>
            <div id="submit-message" class="mt-4 text-center text-sm text-red-500 hidden"></div>
        </section>

        <section>
            <h2 class="text-xl font-bold text-gray-700 mb-4 border-b pb-2">Ideas Recientes (<span id="suggestions-count">0</span>)</h2>
            <div id="suggestions-list" class="space-y-4">
                <p id="empty-message" class="text-gray-500 text-center p-6 bg-gray-50 rounded-lg">Aún no hay sugerencias. ¡Sé el primero en aportar una idea!</p>
            </div>
        </section>
    </div>

    <footer class="mt-8 text-center text-sm text-gray-500">
        Aplicación impulsada por Firebase y Vanilla JavaScript.
    </footer>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, query, onSnapshot, addDoc, serverTimestamp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        const FIREBASE_CONFIG_OBJ = {
            apiKey: "AIzaSyB2a-Cc09zOYfwMuTh74jtKQbNbngqmiug", 
            authDomain: "tu-dominio.firebaseapp.com",
            projectId: "tu-id-de-proyecto",
            storageBucket: "tu-storage.appspot.com",
            messagingSenderId: "tu-sender-id",
            appId: "tu-app-id-web",
        };

        const PROJECT_ID = FIREBASE_CONFIG_OBJ.projectId;
        const app = initializeApp(FIREBASE_CONFIG_OBJ);
        const db = getFirestore(app);
        const auth = getAuth(app);

        let userId = null;
        let isAuthReady = false;

        const loadingContainer = document.getElementById('loading-container');
        const appContainer = document.getElementById('app-container');
        const userIdSpan = document.getElementById('user-id-span');
        const userIdDisplay = document.getElementById('user-id-display');
        const suggestionForm = document.getElementById('suggestion-form');
        const newSuggestionInput = document.getElementById('new-suggestion-input');
        const submitButton = document.getElementById('submit-button');
        const suggestionsList = document.getElementById('suggestions-list');
        const emptyMessage = document.getElementById('empty-message');
        const suggestionsCount = document.getElementById('suggestions-count');
        const submitMessage = document.getElementById('submit-message');
        const charCount = document.getElementById('char-count');

        const showError = (message) => {
            loadingContainer.classList.add('hidden');
            appContainer.classList.add('hidden');
            const errorDiv = document.createElement('div');
            errorDiv.className = 'flex justify-center items-center h-screen bg-red-50 p-4';
            errorDiv.innerHTML = `<div class="text-xl font-semibold text-red-700">Error: ${message}</div>`;
            document.body.prepend(errorDiv);
        };

        const renderSuggestions = (suggestions) => {
            suggestionsList.innerHTML = '';
            if (suggestions.length === 0) {
                emptyMessage.classList.remove('hidden');
            } else {
                emptyMessage.classList.add('hidden');
                suggestions.forEach(s => {
                    const dateOptions = { day: 'numeric', month: 'short', year: 'numeric' };
                    const formattedDate = s.createdAt ? new Date(s.createdAt.seconds * 1000).toLocaleDateString('es-ES', dateOptions) : 'Fecha desconocida';
                    const authorSnippet = s.authorId ? s.authorId.substring(0, 8) + '...' : 'Anónimo';

                    const suggestionDiv = document.createElement('div');
                    suggestionDiv.className = 'bg-white border border-indigo-100 p-4 rounded-lg shadow-sm hover:shadow-md transition duration-150';
                    suggestionDiv.innerHTML = `
                        <p class="text-gray-800 break-words">${s.text}</p>
                        <div class="mt-2 pt-2 border-t border-gray-100 flex justify-between items-center text-xs text-gray-400">
                            <span>
                                Sugerido por: <span class="font-mono text-gray-500 break-all">${authorSnippet}</span>
                            </span>
                            <span class="text-gray-400">
                                ${formattedDate}
                            </span>
                        </div>
                    `;
                    suggestionsList.appendChild(suggestionDiv);
                });
            }
            suggestionsCount.textContent = suggestions.length;
        };

        const setupRealtimeListener = () => {
            if (!isAuthReady || !db || !userId) return;

            const suggestionsCollectionPath = `/artifacts/${PROJECT_ID}/public/data/suggestions`;
            const q = query(collection(db, suggestionsCollectionPath));

            onSnapshot(q, (snapshot) => {
                const fetchedSuggestions = snapshot.docs.map(doc => ({
                    id: doc.id,
                    ...doc.data(),
                })).sort((a, b) => (b.createdAt?.toMillis() || 0) - (a.createdAt?.toMillis() || 0));
                renderSuggestions(fetchedSuggestions);
            }, (e) => {
                showError('Error al cargar las sugerencias. Inténtalo de nuevo.');
            });
        };

        const handleSubmit = async (e) => {
            e.preventDefault();
            const suggestionText = newSuggestionInput.value.trim();

            if (!suggestionText || !db || !userId) {
                submitMessage.textContent = 'El campo no puede estar vacío.';
                submitMessage.classList.remove('hidden');
                return;
            }
            
            submitMessage.classList.add('hidden');
            submitButton.disabled = true;
            submitButton.innerHTML = `<svg class="animate-spin -ml-1 mr-3 h-5 w-5 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"><circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle><path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path></svg>Enviando...`;

            try {
                const suggestionsCollectionPath = `/artifacts/${PROJECT_ID}/public/data/suggestions`;
                await addDoc(collection(db, suggestionsCollectionPath), {
                    text: suggestionText,
                    authorId: userId,
                    createdAt: serverTimestamp(),
                });
                newSuggestionInput.value = '';
                charCount.textContent = '0';
                submitMessage.textContent = 'Sugerencia enviada con éxito.';
                submitMessage.classList.remove('text-red-500');
                submitMessage.classList.add('text-green-500');
                submitMessage.classList.remove('hidden');
                setTimeout(() => submitMessage.classList.add('hidden'), 3000);
            } catch (e) {
                submitMessage.textContent = 'Error al subir la sugerencia. Verifica tu conexión.';
                submitMessage.classList.remove('text-green-500');
                submitMessage.classList.add('text-red-500');
                submitMessage.classList.remove('hidden');
            } finally {
                submitButton.disabled = false;
                submitButton.innerHTML = 'Enviar Sugerencia';
            }
        };

        const handleCharCount = () => {
            charCount.textContent = newSuggestionInput.value.length;
        };

        document.addEventListener('DOMContentLoaded', () => {
            if (!FIREBASE_CONFIG_OBJ.apiKey) {
                showError('La configuración de Firebase está vacía. Por favor, reemplaza los valores de ejemplo en FIREBASE_CONFIG_OBJ.');
                return;
            }

            signInAnonymously(auth).then(() => {
                onAuthStateChanged(auth, (user) => {
                    if (user) {
                        userId = user.uid;
                        isAuthReady = true;

                        userIdSpan.textContent = userId;
                        userIdDisplay.classList.remove('hidden');

                        loadingContainer.classList.add('hidden');
                        appContainer.classList.remove('hidden');

                        setupRealtimeListener();
                    } else {
                        showError('No se pudo iniciar sesión anónimamente.');
                    }
                });
            }).catch(e => {
                showError('Error de autenticación: ' + e.message);
            });

            suggestionForm.addEventListener('submit', handleSubmit);
            newSuggestionInput.addEventListener('input', handleCharCount);
        });
    </script>
</body>
</html>

