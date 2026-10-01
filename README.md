# yoharmen.github.io
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistem Operasi - Interactive LUMI / H5P Content</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Alpine.js CDN -->
    <script defer src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        [x-cloak] { display: none !important; }
        .gradient-bg {
            background: linear-gradient(135deg, #0284c7 0%, #0369a1 50%, #0f172a 100%);
        }
        .card-shadow {
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
        }
    </style>
</head>
<body class="bg-slate-100 font-sans text-slate-800 min-h-screen flex flex-col" x-data="lumiApp()">

    <!-- HEADER / BRANDING BANNER -->
    <header class="bg-sky-800 text-white shadow-md">
        <div class="max-w-7xl mx-auto px-4 py-3 flex flex-wrap justify-between items-center gap-4">
            <div class="flex items-center space-x-3">
                <div class="bg-white p-2 rounded-full text-sky-800 shadow">
                    <i class="fa-solid fa-graduation-cap text-2xl"></i>
                </div>
                <div>
                    <h1 class="font-bold text-lg leading-tight">SMKN 2 Kepulauan Mentawai</h1>
                    <p class="text-xs text-sky-200">"Sekolah Vokasi Unggul dan Berkarakter"</p>
                </div>
            </div>
            <div class="text-right hidden sm:block">
                <div class="text-xs text-sky-200">Pengembang & Guru TIK:</div>
                <div class="font-semibold text-sm"><i class="fa-solid fa-user-tie mr-1"></i> Yoharmen Arnov, S.Pd, M.Pd.T</div>
            </div>
        </div>
    </header>

    <!-- SUB HEADER: TITLE & TOP NAVIGATION -->
    <div class="bg-white border-b border-slate-200 shadow-sm sticky top-0 z-30">
        <div class="max-w-7xl mx-auto px-4 py-2 flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <span class="bg-amber-500 text-white text-xs font-bold px-2.5 py-1 rounded-full uppercase tracking-wider">H5P / LUMI</span>
                <h2 class="font-bold text-slate-800 text-sm md:text-base">Media Pembelajaran Interaktif: Sistem Operasi</h2>
            </div>
            
            <!-- Quick View Progress Bar -->
            <div class="flex items-center space-x-3 text-xs">
                <span class="hidden md:inline font-medium text-slate-600">Progres:</span>
                <div class="w-24 md:w-32 bg-slate-200 rounded-full h-2.5 overflow-hidden">
                    <div class="bg-emerald-500 h-2.5 rounded-full transition-all duration-300" :style="`width: ${progress}%`"></div>
                </div>
                <span class="font-bold text-slate-700" x-text="`${progress}%`">0%</span>
            </div>
        </div>
    </div>

    <!-- MAIN INTERACTIVE CONTAINER -->
    <main class="flex-1 max-w-7xl w-full mx-auto p-4 md:p-6 flex flex-col justify-center">

        <!-- SCREEN 1: SPLASH SCREEN / HALAMAN PEMBUKA -->
        <div x-show="currentScreen === 1" x-transition x-cloak class="bg-white rounded-2xl border border-slate-200 card-shadow overflow-hidden text-center p-6 md:p-12 my-auto">
            <div class="max-w-2xl mx-auto">
                <div class="w-24 h-24 bg-sky-100 rounded-full flex items-center justify-center mx-auto mb-6 text-sky-600 text-4xl shadow-inner">
                    <i class="fa-solid fa-desktop"></i>
                </div>
                <span class="text-xs font-semibold uppercase tracking-widest text-sky-600 bg-sky-50 px-3 py-1 rounded-full border border-sky-200">SMKN 2 KEPULAUAN MENTAWAI</span>
                <h1 class="text-3xl md:text-5xl font-extrabold text-slate-900 mt-4 mb-2">Sistem Operasi</h1>
                <p class="text-lg font-medium text-amber-600 mb-6">Belajar • Berpikir • Berkarya</p>
                <p class="text-slate-600 mb-8 max-w-lg mx-auto">Selamat datang dalam modul pembelajaran interaktif berbasis LUMI/H5P. Pelajari konsep dasar sistem operasi, manajemen proses, memori, dan simulasi secara interaktif.</p>
                
                <button @click="navigateTo(2)" class="inline-flex items-center space-x-2 bg-sky-600 hover:bg-sky-700 text-white font-bold px-8 py-4 rounded-xl shadow-lg hover:shadow-xl transition transform hover:-translate-y-0.5 active:translate-y-0 text-lg">
                    <span>Mulai Belajar</span>
                    <i class="fa-solid fa-circle-arrow-right"></i>
                </button>
            </div>
        </div>

        <!-- SCREEN 2: MENU UTAMA -->
        <div x-show="currentScreen === 2" x-transition x-cloak class="space-y-6">
            <div class="bg-gradient-to-r from-sky-700 to-sky-900 text-white p-6 rounded-2xl shadow-md flex justify-between items-center">
                <div>
                    <h2 class="text-2xl font-bold">Menu Utama Pembelajaran</h2>
                    <p class="text-sky-200 text-sm mt-1">Pilih menu di bawah ini untuk memulai kegiatan belajar interaktif.</p>
                </div>
                <div class="hidden sm:block text-4xl opacity-30">
                    <i class="fa-solid fa-cubes"></i>
                </div>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Card Materi -->
                <div @click="navigateTo(3)" class="bg-white p-6 rounded-2xl border border-slate-200 card-shadow hover:border-sky-500 hover:shadow-lg transition cursor-pointer group">
                    <div class="w-14 h-14 bg-amber-100 text-amber-600 rounded-xl flex items-center justify-center text-2xl mb-4 group-hover:scale-110 transition">
                        <i class="fa-solid fa-book-open"></i>
                    </div>
                    <h3 class="text-xl font-bold text-slate-800 mb-2 group-hover:text-sky-600 transition">1. Menu Materi</h3>
                    <p class="text-slate-600 text-sm">Pelajari konsep dasar sistem operasi, fungsi utama, jenis-jenis, hingga arsitektur memory.</p>
                </div>

                <!-- Card Kuis -->
                <div @click="navigateTo(4)" class="bg-white p-6 rounded-2xl border border-slate-200 card-shadow hover:border-sky-500 hover:shadow-lg transition cursor-pointer group">
                    <div class="w-14 h-14 bg-emerald-100 text-emerald-600 rounded-xl flex items-center justify-center text-2xl mb-4 group-hover:scale-110 transition">
                        <i class="fa-solid fa-list-check"></i>
                    </div>
                    <h3 class="text-xl font-bold text-slate-800 mb-2 group-hover:text-sky-600 transition">2. Kuis Interaktif</h3>
                    <p class="text-slate-600 text-sm">Uji pemahaman Anda melalui kuis pilihan ganda dengan umpan balik langsung dan penilaian otomatis.</p>
                </div>

                <!-- Card Simulasi -->
                <div @click="navigateTo(5)" class="bg-white p-6 rounded-2xl border border-slate-200 card-shadow hover:border-sky-500 hover:shadow-lg transition cursor-pointer group">
                    <div class="w-14 h-14 bg-purple-100 text-purple-600 rounded-xl flex items-center justify-center text-2xl mb-4 group-hover:scale-110 transition">
                        <i class="fa-solid fa-gamepad"></i>
                    </div>
                    <h3 class="text-xl font-bold text-slate-800 mb-2 group-hover:text-sky-600 transition">3. Simulasi Interaktif</h3>
                    <p class="text-slate-600 text-sm">Simulasi visual cara kerja penjadwalan proses CPU dan alokasi sumber daya sistem operasi.</p>
                </div>

                <!-- Card Video -->
                <div @click="navigateTo(6)" class="bg-white p-6 rounded-2xl border border-slate-200 card-shadow hover:border-sky-500 hover:shadow-lg transition cursor-pointer group">
                    <div class="w-14 h-14 bg-rose-100 text-rose-600 rounded-xl flex items-center justify-center text-2xl mb-4 group-hover:scale-110 transition">
                        <i class="fa-solid fa-circle-play"></i>
                    </div>
                    <h3 class="text-xl font-bold text-slate-800 mb-2 group-hover:text-sky-600 transition">4. Video Pembelajaran</h3>
                    <p class="text-slate-600 text-sm">Saksikan penjelasan multimedia interaktif seputar instalasi dan konfigurasi OS.</p>
                </div>

                <!-- Card Rangkuman -->
                <div @click="navigateTo(7)" class="bg-white p-6 rounded-2xl border border-slate-200 card-shadow hover:border-sky-500 hover:shadow-lg transition cursor-pointer group">
                    <div class="w-14 h-14 bg-indigo-100 text-indigo-600 rounded-xl flex items-center justify-center text-2xl mb-4 group-hover:scale-110 transition">
                        <i class="fa-solid fa-file-lines"></i>
                    </div>
                    <h3 class="text-xl font-bold text-slate-800 mb-2 group-hover:text-sky-600 transition">5. Rangkuman Materi</h3>
                    <p class="text-slate-600 text-sm">Ringkasan poin penting pembelajaran serta refleksi latihan mandiri.</p>
                </div>

                <!-- Card Profil & Pengaturan -->
                <div @click="navigateTo(8)" class="bg-white p-6 rounded-2xl border border-slate-200 card-shadow hover:border-sky-500 hover:shadow-lg transition cursor-pointer group">
                    <div class="w-14 h-14 bg-cyan-100 text-cyan-600 rounded-xl flex items-center justify-center text-2xl mb-4 group-hover:scale-110 transition">
                        <i class="fa-solid fa-user-gear"></i>
                    </div>
                    <h3 class="text-xl font-bold text-slate-800 mb-2 group-hover:text-sky-600 transition">6. Profil & Progress</h3>
                    <p class="text-slate-600 text-sm">Pantau statistik progres penyelesaian modul, riwayat belajar, dan nilai kuis Anda.</p>
                </div>
            </div>
        </div>

        <!-- SCREEN 3: MENU MATERI (COURSE PRESENTATION) -->
        <div x-show="currentScreen === 3" x-transition x-cloak class="bg-white rounded-2xl border border-slate-200 card-shadow overflow-hidden flex flex-col min-h-[500px]">
            <div class="bg-slate-800 text-white p-4 flex justify-between items-center">
                <div class="flex items-center space-x-2">
                    <i class="fa-solid fa-book-open text-amber-400"></i>
                    <h3 class="font-bold">Modul Materi Interaktif</h3>
                </div>
                <span class="text-xs bg-slate-700 px-3 py-1 rounded-full text-slate-300" x-text="`Bab ${materiTab} dari 6`"></span>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-4 flex-1">
                <!-- Sidebar Navigasi Bab -->
                <div class="bg-slate-50 border-r border-slate-200 p-4 space-y-1">
                    <template x-for="(m, idx) in materiList" :key="idx">
                        <button @click="materiTab = idx + 1" 
                                :class="materiTab === (idx + 1) ? 'bg-sky-600 text-white font-semibold' : 'hover:bg-slate-200 text-slate-700'"
                                class="w-full text-left px-3 py-2.5 rounded-lg text-sm transition flex items-center justify-between">
                            <span class="truncate" x-text="`${idx+1}. ${m.title}`"></span>
                            <i class="fa-solid fa-chevron-right text-xs opacity-70"></i>
                        </button>
                    </template>
                </div>

                <!-- Konten Bab -->
                <div class="lg:col-span-3 p-6 flex flex-col justify-between">
                    <div>
                        <!-- Bab 1 -->
                        <div x-show="materiTab === 1">
                            <h4 class="text-2xl font-bold text-slate-900 mb-4 pb-2 border-b border-slate-200">1. Pengertian Sistem Operasi</h4>
                            <p class="text-slate-700 leading-relaxed mb-4">
                                <strong>Sistem Operasi (Operating System / OS)</strong> adalah perangkat lunak sistem (*system software*) yang berfungsi sebagai penghubung (*interface*) utama antara pengguna (*user*) dengan perangkat keras komputer (*hardware*), serta bertugas mengelola seluruh sumber daya (*resources*) pada sistem komputer.
                            </p>
                            <div class="bg-sky-50 border-l-4 border-sky-500 p-4 rounded-r-lg my-6">
                                <h5 class="font-bold text-sky-900 mb-1"><i class="fa-solid fa-lightbulb text-amber-500 mr-2"></i>Analogi Sederhana:</h5>
                                <p class="text-sky-800 text-sm">Sistem operasi seperti seorang <em>Manajer Restoran</em>. Ia mengatur pesanan pelanggan (User), membagi tugas ke dapur/pelayan (Hardware), dan memastikan semua proses berjalan teratur tanpa bentrokan.</p>
                            </div>
                            <div class="grid grid-cols-3 gap-3 text-center my-4">
                                <div class="bg-slate-100 p-3 rounded-lg border border-slate-200"><i class="fa-solid fa-user text-2xl text-sky-600 mb-1"></i><p class="text-xs font-bold">User</p></div>
                                <div class="bg-sky-100 p-3 rounded-lg border border-sky-300 font-bold text-sky-800 flex flex-col justify-center"><i class="fa-solid fa-gears text-2xl text-sky-600 mb-1"></i><p class="text-xs">Sistem Operasi</p></div>
                                <div class="bg-slate-100 p-3 rounded-lg border border-slate-200"><i class="fa-solid fa-microchip text-2xl text-slate-700 mb-1"></i><p class="text-xs font-bold">Hardware</p></div>
                            </div>
                        </div>

                        <!-- Bab 2 -->
                        <div x-show="materiTab === 2">
                            <h4 class="text-2xl font-bold text-slate-900 mb-4 pb-2 border-b border-slate-200">2. Fungsi Utama Sistem Operasi</h4>
                            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                                <div class="bg-white border border-slate-200 p-4 rounded-xl shadow-sm">
                                    <div class="font-bold text-sky-700 flex items-center gap-2 mb-1"><i class="fa-solid fa-microchip"></i> Manajemen Proses</div>
                                    <p class="text-sm text-slate-600">Mengatur jadwal eksekusi instruksi CPU, membuat, menghapus, dan menyinkronkan antar-proses.</p>
                                </div>
                                <div class="bg-white border border-slate-200 p-4 rounded-xl shadow-sm">
                                    <div class="font-bold text-emerald-700 flex items-center gap-2 mb-1"><i class="fa-solid fa-memory"></i> Manajemen Memori</div>
                                    <p class="text-sm text-slate-600">Mengalokasikan dan membebaskan ruang RAM untuk aplikasi yang sedang aktif berjalan.</p>
                                </div>
                                <div class="bg-white border border-slate-200 p-4 rounded-xl shadow-sm">
                                    <div class="font-bold text-purple-700 flex items-center gap-2 mb-1"><i class="fa-solid fa-folder-open"></i> Manajemen Berkas (File)</div>
                                    <p class="text-sm text-slate-600">Mengorganisasi penyimpanan file/direktori pada harddisk/SSD, hak akses, dan backup.</p>
                                </div>
                                <div class="bg-white border border-slate-200 p-4 rounded-xl shadow-sm">
                                    <div class="font-bold text-amber-700 flex items-center gap-2 mb-1"><i class="fa-solid fa-keyboard"></i> Manajemen Perangkat I/O</div>
                                    <p class="text-sm text-slate-600">Menyediakan driver untuk mengontrol input/output seperti keyboard, printer, & mouse.</p>
                                </div>
                            </div>
                        </div>

                        <!-- Bab 3 -->
                        <div x-show="materiTab === 3">
                            <h4 class="text-2xl font-bold text-slate-900 mb-4 pb-2 border-b border-slate-200">3. Jenis-Jenis Sistem Operasi</h4>
                            <div class="space-y-4">
                                <div class="border border-slate-200 rounded-xl p-4 flex items-start gap-4 bg-slate-50">
                                    <div class="p-3 bg-blue-500 text-white rounded-lg text-2xl"><i class="fa-brands fa-windows"></i></div>
                                    <div>
                                        <h5 class="font-bold text-slate-800">Sistem Operasi Desktop / Komputer</h5>
                                        <p class="text-sm text-slate-600 mt-1">Digunakan pada PC, Laptop, atau Server. Contoh: <strong>Microsoft Windows, macOS, Linux (Ubuntu, Debian, Fedora)</strong>.</p>
                                    </div>
                                </div>
                                <div class="border border-slate-200 rounded-xl p-4 flex items-start gap-4 bg-slate-50">
                                    <div class="p-3 bg-emerald-500 text-white rounded-lg text-2xl"><i class="fa-brands fa-android"></i></div>
                                    <div>
                                        <h5 class="font-bold text-slate-800">Sistem Operasi Mobile</h5>
                                        <p class="text-sm text-slate-600 mt-1">Dirancang khusus untuk perangkat genggam (smartphone & tablet). Contoh: <strong>Android OS & Apple iOS</strong>.</p>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Bab 4 -->
                        <div x-show="materiTab === 4">
                            <h4 class="text-2xl font-bold text-slate-900 mb-4 pb-2 border-b border-slate-200">4. Struktur & Arsitektur Sistem Operasi</h4>
                            <p class="text-slate-700 text-sm mb-4">Arsitektur dasar OS terdiri dari beberapa lapisan hierarki interaksi:</p>
                            <ul class="space-y-3">
                                <li class="p-3 bg-sky-50 border border-sky-200 rounded-lg flex items-center gap-3">
                                    <span class="font-extrabold text-sky-600">01</span>
                                    <div><strong class="text-slate-800">User Interface (GUI / CLI):</strong> Antarmuka tempat pengguna memberikan perintah (tombol, ikon, atau terminal).</div>
                                </li>
                                <li class="p-3 bg-indigo-50 border border-indigo-200 rounded-lg flex items-center gap-3">
                                    <span class="font-extrabold text-indigo-600">02</span>
                                    <div><strong class="text-slate-800">System Call / Shell:</strong> Penerjemah perintah dari antarmuka pengguna ke dalam bahasa kernel.</div>
                                </li>
                                <li class="p-3 bg-purple-50 border border-purple-200 rounded-lg flex items-center gap-3">
                                    <span class="font-extrabold text-purple-600">03</span>
                                    <div><strong class="text-slate-800">Kernel:</strong> Inti terpusat OS yang langsung berkomunikasi dengan hardware (CPU, Memory, Disk).</div>
                                </li>
                            </ul>
                        </div>

                        <!-- Bab 5 -->
                        <div x-show="materiTab === 5">
                            <h4 class="text-2xl font-bold text-slate-900 mb-4 pb-2 border-b border-slate-200">5. Manajemen Proses (CPU Scheduling)</h4>
                            <p class="text-slate-700 leading-relaxed mb-4">
                                Prosedur di mana OS menentukan alokasi waktu eksekusi CPU untuk tugas-tugas (*processes*) yang mengantre.
                            </p>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 text-sm">
                                <div class="p-3 border rounded-lg bg-slate-50"><strong class="text-sky-700">FCFS (First-Come, First-Served):</strong> Proses yang datang pertama akan dilayani lebih dulu.</div>
                                <div class="p-3 border rounded-lg bg-slate-50"><strong class="text-sky-700">Round Robin (RR):</strong> Setiap proses mendapat jatah waktu (*quantum*) secara bergiliran.</div>
                            </div>
                        </div>

                        <!-- Bab 6 -->
                        <div x-show="materiTab === 6">
                            <h4 class="text-2xl font-bold text-slate-900 mb-4 pb-2 border-b border-slate-200">6. Manajemen Memori</h4>
                            <p class="text-slate-700 leading-relaxed">
                                Memori utama (RAM) adalah tempat penyimpanan berkecepatan tinggi yang dapat diakses langsung oleh CPU. OS bertanggung jawab mencatat bagian memori yang sedang digunakan dan mengalokasikan ruang untuk aplikasi baru.
                            </p>
                        </div>
                    </div>

                    <!-- Bottom Nav Sub-Materi -->
                    <div class="flex justify-between items-center pt-6 border-t border-slate-200 mt-6">
                        <button @click="materiTab = Math.max(1, materiTab - 1)" :disabled="materiTab === 1" class="px-4 py-2 bg-slate-100 hover:bg-slate-200 text-slate-700 rounded-lg disabled:opacity-40 text-sm font-semibold flex items-center gap-1">
                            <i class="fa-solid fa-arrow-left"></i> Sebelumnya
                        </button>
                        <button @click="materiTab = Math.min(6, materiTab + 1)" :disabled="materiTab === 6" class="px-4 py-2 bg-sky-600 hover:bg-sky-700 text-white rounded-lg disabled:opacity-40 text-sm font-semibold flex items-center gap-1">
                            Selanjutnya <i class="fa-solid fa-arrow-right"></i>
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- SCREEN 4: KUIS INTERAKTIF -->
        <div x-show="currentScreen === 4" x-transition x-cloak class="bg-white rounded-2xl border border-slate-200 card-shadow overflow-hidden max-w-3xl mx-auto w-full p-6 md:p-8">
            <div class="flex justify-between items-center mb-6 pb-4 border-b border-slate-200">
                <div class="flex items-center space-x-2">
                    <span class="p-2 bg-emerald-100 text-emerald-600 rounded-lg"><i class="fa-solid fa-file-signature"></i></span>
                    <h3 class="font-bold text-lg text-slate-800">Kuis Pilihan Ganda</h3>
                </div>
                <span class="text-xs font-semibold bg-slate-100 text-slate-600 px-3 py-1 rounded-full" x-text="`Soal ${quizIndex + 1} dari ${quizQuestions.length}`"></span>
            </div>

            <!-- Pertanyaan -->
            <div x-show="!quizCompleted">
                <h4 class="text-lg font-bold text-slate-900 mb-6" x-text="quizQuestions[quizIndex].question"></h4>

                <div class="space-y-3 mb-6">
                    <template x-for="(option, idx) in quizQuestions[quizIndex].options" :key="idx">
                        <button @click="selectAnswer(idx)" 
                                :class="selectedAnswer === idx ? 'border-sky-500 bg-sky-50 text-sky-900 font-medium' : 'border-slate-200 hover:border-slate-300 hover:bg-slate-50 text-slate-700'"
                                class="w-full text-left p-4 rounded-xl border-2 transition flex items-center justify-between">
                            <div class="flex items-center space-x-3">
                                <span class="w-7 h-7 rounded-full border flex items-center justify-center font-bold text-xs"
                                      :class="selectedAnswer === idx ? 'bg-sky-500 text-white border-sky-500' : 'border-slate-300 text-slate-500'"
                                      x-text="String.fromCharCode(65 + idx)"></span>
                                <span x-text="option"></span>
                            </div>
                            <i x-show="selectedAnswer === idx" class="fa-solid fa-circle-check text-sky-500"></i>
                        </button>
                    </template>
                </div>

                <!-- Feedback Box -->
                <div x-show="answerSubmitted" x-transition class="p-4 rounded-xl mb-6 text-sm"
                     :class="quizQuestions[quizIndex].correct === selectedAnswer ? 'bg-emerald-50 border border-emerald-200 text-emerald-800' : 'bg-rose-50 border border-rose-200 text-rose-800'">
                    <div class="font-bold flex items-center gap-2 mb-1">
                        <i :class="quizQuestions[quizIndex].correct === selectedAnswer ? 'fa-solid fa-circle-check text-emerald-600' : 'fa-solid fa-circle-xmark text-rose-600'"></i>
                        <span x-text="quizQuestions[quizIndex].correct === selectedAnswer ? 'Jawaban Benar!' : 'Jawaban Kurang Tepat!'"></span>
                    </div>
                    <p x-text="quizQuestions[quizIndex].feedback"></p>
                </div>

                <!-- Tombol Nav Kuis -->
                <div class="flex justify-between items-center pt-4 border-t border-slate-100">
                    <button @click="resetQuizState()" class="text-xs text-slate-500 hover:underline">Reset Pilihan</button>
                    <button x-show="!answerSubmitted" @click="submitAnswer()" :disabled="selectedAnswer === null"
                            class="px-6 py-2.5 bg-sky-600 hover:bg-sky-700 text-white rounded-xl font-bold text-sm disabled:opacity-40 transition">
                        Periksa Jawaban
                    </button>
                    <button x-show="answerSubmitted" @click="nextQuestion()"
                            class="px-6 py-2.5 bg-emerald-600 hover:bg-emerald-700 text-white rounded-xl font-bold text-sm transition">
                        <span x-text="quizIndex + 1 === quizQuestions.length ? 'Selesai Kuis' : 'Lanjut Soal'"></span>
                    </button>
                </div>
            </div>

            <!-- Kuis Selesai -->
            <div x-show="quizCompleted" class="text-center py-8 space-y-4">
                <div class="w-20 h-20 bg-emerald-100 text-emerald-600 rounded-full flex items-center justify-center text-4xl mx-auto">
                    <i class="fa-solid fa-trophy"></i>
                </div>
                <h4 class="text-2xl font-bold text-slate-900">Kuis Selesai!</h4>
                <p class="text-slate-600">Skor Akhir Anda:</p>
                <div class="text-5xl font-extrabold text-sky-600" x-text="`${quizScore} / 100`"></div>
                <div class="pt-4 flex justify-center gap-3">
                    <button @click="restartQuiz()" class="px-5 py-2.5 border border-slate-300 hover:bg-slate-50 text-slate-700 font-semibold rounded-xl text-sm">
                        Coba Lagi
                    </button>
                    <button @click="navigateTo(5)" class="px-5 py-2.5 bg-sky-600 hover:bg-sky-700 text-white font-semibold rounded-xl text-sm">
                        Lanjut ke Simulasi
                    </button>
                </div>
            </div>
        </div>

        <!-- SCREEN 5: SIMULASI INTERAKTIF (MANAJEMEN PROSES CPU) -->
        <div x-show="currentScreen === 5" x-transition x-cloak class="bg-white rounded-2xl border border-slate-200 card-shadow p-6 md:p-8 max-w-4xl mx-auto w-full">
            <div class="flex justify-between items-center mb-6 pb-4 border-b border-slate-200">
                <div class="flex items-center space-x-2">
                    <span class="p-2 bg-purple-100 text-purple-600 rounded-lg"><i class="fa-solid fa-microchip"></i></span>
                    <div>
                        <h3 class="font-bold text-lg text-slate-800">Simulasi Interaktif: Manajemen Proses</h3>
                        <p class="text-xs text-slate-500">Visualisasi eksekusi penjadwalan proses pada CPU</p>
                    </div>
                </div>
            </div>

            <!-- CPU Status Display -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
                <div class="bg-slate-900 text-white p-6 rounded-2xl flex flex-col items-center justify-center text-center shadow-md">
                    <span class="text-xs font-semibold text-slate-400 uppercase tracking-widest mb-2">STATUS CPU</span>
                    <div class="w-16 h-16 rounded-full border-4 flex items-center justify-center text-xl font-bold my-2"
                         :class="simRunning ? 'border-emerald-500 text-emerald-400 animate-pulse' : 'border-slate-700 text-slate-500'">
                        <span x-text="activeProcess !== null ? `P${activeProcess + 1}` : 'IDLE'"></span>
                    </div>
                    <p class="text-xs text-slate-300 mt-2" x-text="simRunning ? 'Memproses Instruksi...' : 'CPU Siap / Standby'"></p>
                </div>

                <div class="md:col-span-2 border border-slate-200 p-6 rounded-2xl bg-slate-50 flex flex-col justify-between">
                    <div>
                        <h4 class="font-bold text-slate-800 mb-3 text-sm flex items-center gap-2">
                            <i class="fa-solid fa-bars-staggered text-sky-600"></i> Antrian Proses (Ready Queue)
                        </h4>
                        <div class="space-y-3">
                            <template x-for="(proc, idx) in processes" :key="idx">
                                <div>
                                    <div class="flex justify-between text-xs font-semibold mb-1">
                                        <span x-text="`Proses ${proc.id}`"></span>
                                        <span x-text="`${proc.remaining} Detik Sisa`"></span>
                                    </div>
                                    <div class="w-full bg-slate-200 rounded-full h-3 overflow-hidden">
                                        <div class="h-3 rounded-full transition-all duration-300"
                                             :class="proc.color"
                                             :style="`width: ${(proc.remaining / proc.total) * 100}%`"></div>
                                    </div>
                                </div>
                            </template>
                        </div>
                    </div>

                    <div class="flex gap-3 mt-6">
                        <button @click="startSimulation()" :disabled="simRunning"
                                class="flex-1 bg-purple-600 hover:bg-purple-700 disabled:opacity-50 text-white font-bold py-2.5 rounded-xl text-sm transition flex items-center justify-center gap-2">
                            <i class="fa-solid fa-play"></i> Mulai
                        </button>
                        <button @click="resetSimulation()"
                                class="bg-slate-200 hover:bg-slate-300 text-slate-700 font-bold px-4 py-2.5 rounded-xl text-sm transition">
                            <i class="fa-solid fa-rotate-right"></i> Reset
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- SCREEN 6: VIDEO PEMBELAJARAN INTERAKTIF -->
        <div x-show="currentScreen === 6" x-transition x-cloak class="bg-white rounded-2xl border border-slate-200 card-shadow overflow-hidden max-w-4xl mx-auto w-full">
            <div class="bg-slate-800 text-white p-4 flex justify-between items-center">
                <h3 class="font-bold flex items-center gap-2"><i class="fa-solid fa-circle-play text-rose-500"></i> Video Pembelajaran Interaktif</h3>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-3">
                <!-- Mockup Video Player -->
                <div class="lg:col-span-2 bg-slate-950 p-6 flex flex-col justify-between min-h-[320px] text-white relative">
                    <div class="flex justify-between items-center text-xs text-slate-400">
                        <span class="bg-rose-600 text-white font-bold px-2 py-0.5 rounded">HD 1080p</span>
                        <span>02:15 / 08:30</span>
                    </div>

                    <div class="text-center my-auto py-8">
                        <div class="w-16 h-16 bg-rose-600 hover:bg-rose-700 rounded-full flex items-center justify-center text-2xl mx-auto cursor-pointer shadow-lg transition transform hover:scale-110">
                            <i class="fa-solid fa-play ml-1"></i>
                        </div>
                        <h4 class="font-bold text-lg mt-4">Jenis-Jenis Sistem Operasi</h4>
                        <p class="text-xs text-slate-400 mt-1">SMKN 2 Kepulauan Mentawai • Video Tutorial</p>
                    </div>

                    <div class="space-y-2">
                        <div class="w-full bg-slate-800 h-1.5 rounded-full overflow-hidden cursor-pointer">
                            <div class="bg-rose-600 h-1.5 w-1/4"></div>
                        </div>
                        <div class="flex justify-between items-center text-xs text-slate-400">
                            <div class="flex items-center space-x-3">
                                <i class="fa-solid fa-play cursor-pointer hover:text-white"></i>
                                <i class="fa-solid fa-volume-high cursor-pointer hover:text-white"></i>
                            </div>
                            <i class="fa-solid fa-expand cursor-pointer hover:text-white"></i>
                        </div>
                    </div>
                </div>

                <!-- Playlist Video -->
                <div class="p-4 bg-slate-50 border-l border-slate-200">
                    <h4 class="font-bold text-slate-800 text-sm mb-3">Daftar Video Pembelajaran</h4>
                    <div class="space-y-2">
                        <div class="p-3 bg-white border border-slate-200 rounded-xl text-xs font-semibold text-sky-700 flex items-center justify-between shadow-sm cursor-pointer">
                            <span class="flex items-center gap-2"><i class="fa-solid fa-circle-play text-rose-500"></i> 1. Pengantar OS</span>
                            <span>03:10</span>
                        </div>
                        <div class="p-3 bg-sky-50 border border-sky-300 rounded-xl text-xs font-bold text-sky-900 flex items-center justify-between shadow-sm cursor-pointer">
                            <span class="flex items-center gap-2"><i class="fa-solid fa-circle-play text-rose-500"></i> 2. Jenis-Jenis OS</span>
                            <span>08:30</span>
                        </div>
                        <div class="p-3 bg-white border border-slate-200 rounded-xl text-xs font-semibold text-slate-700 hover:bg-slate-100 flex items-center justify-between cursor-pointer">
                            <span class="flex items-center gap-2"><i class="fa-solid fa-circle-play text-slate-400"></i> 3. Instalasi OS</span>
                            <span>12:45</span>
                        </div>
                        <div class="p-3 bg-white border border-slate-200 rounded-xl text-xs font-semibold text-slate-700 hover:bg-slate-100 flex items-center justify-between cursor-pointer">
                            <span class="flex items-center gap-2"><i class="fa-solid fa-circle-play text-slate-400"></i> 4. Konfigurasi OS</span>
                            <span>10:15</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- SCREEN 7: RANGKUMAN & LATIHAN MANDIRI -->
        <div x-show="currentScreen === 7" x-transition x-cloak class="bg-white rounded-2xl border border-slate-200 card-shadow p-6 md:p-8 max-w-3xl mx-auto w-full">
            <div class="flex items-center space-x-2 border-b border-slate-200 pb-4 mb-6">
                <span class="p-2 bg-indigo-100 text-indigo-600 rounded-lg"><i class="fa-solid fa-file-lines"></i></span>
                <h3 class="font-bold text-lg text-slate-800">Rangkuman Materi & Refleksi</h3>
            </div>

            <div class="space-y-6">
                <div class="bg-slate-50 border border-slate-200 rounded-xl p-5">
                    <h4 class="font-bold text-slate-900 mb-3 flex items-center gap-2 text-sm">
                        <i class="fa-solid fa-list-check text-sky-600"></i> Poin-Poin Kunci
                    </h4>
                    <ul class="space-y-2 text-sm text-slate-700 list-disc list-inside">
                        <li>Sistem Operasi mengelola seluruh perangkat keras dan perangkat lunak komputer.</li>
                        <li>Fungsi utama meliputi manajemen proses, memori, berkas (file), I/O, serta keamanan.</li>
                        <li>Sistem operasi populer meliputi Windows, macOS, Linux, Android, dan iOS.</li>
                    </ul>
                </div>

                <div class="bg-amber-50 border-l-4 border-amber-500 p-4 rounded-r-xl">
                    <p class="italic text-amber-900 text-sm">
                        "Sistem operasi adalah jantung dari komputer yang membuat semua perangkat dapat bekerja secara terkoordinasi."
                    </p>
                </div>
            </div>
        </div>

        <!-- SCREEN 8: PROFIL & PENGATURAN -->
        <div x-show="currentScreen === 8" x-transition x-cloak class="bg-white rounded-2xl border border-slate-200 card-shadow p-6 md:p-8 max-w-2xl mx-auto w-full">
            <div class="flex items-center space-x-4 border-b border-slate-200 pb-6 mb-6">
                <div class="w-16 h-16 bg-sky-600 text-white rounded-full flex items-center justify-center text-2xl font-bold shadow-md">
                    <i class="fa-solid fa-user-graduate"></i>
                </div>
                <div>
                    <h3 class="text-xl font-bold text-slate-900">Siswa / Peserta Didik</h3>
                    <p class="text-sm text-slate-500">SMKN 2 Kepulauan Mentawai</p>
                </div>
            </div>

            <div class="space-y-6">
                <div>
                    <div class="flex justify-between text-sm font-semibold mb-2">
                        <span class="text-slate-700">Progres Penyelesaian Modul</span>
                        <span class="text-sky-600 font-bold" x-text="`${progress}%`"></span>
                    </div>
                    <div class="w-full bg-slate-200 rounded-full h-3 overflow-hidden">
                        <div class="bg-sky-600 h-3 rounded-full transition-all duration-300" :style="`width: ${progress}%`"></div>
                    </div>
                </div>

                <div class="grid grid-cols-2 gap-4">
                    <div class="p-4 bg-slate-50 border rounded-xl text-center">
                        <div class="text-xs text-slate-500 font-medium">Skor Kuis Terakhir</div>
                        <div class="text-2xl font-extrabold text-emerald-600 mt-1" x-text="`${quizScore} / 100`"></div>
                    </div>
                    <div class="p-4 bg-slate-50 border rounded-xl text-center">
                        <div class="text-xs text-slate-500 font-medium">Status Modul</div>
                        <div class="text-sm font-bold text-sky-700 mt-2" x-text="progress >= 100 ? 'Selesai' : 'Sedang Aktif'"></div>
                    </div>
                </div>
            </div>
        </div>

    </main>

    <!-- BOTTOM NAVBAR / ALUR PENGGUNAAN (SCENE NAVIGATOR) -->
    <nav class="bg-white border-t border-slate-200 py-3 px-4 sticky bottom-0 z-30 shadow-lg">
        <div class="max-w-7xl mx-auto flex justify-between items-center overflow-x-auto gap-2">
            <template x-for="s in navScreens" :key="s.id">
                <button @click="navigateTo(s.id)"
                        :class="currentScreen === s.id ? 'bg-sky-600 text-white shadow' : 'bg-slate-100 hover:bg-slate-200 text-slate-700'"
                        class="px-3 py-2 rounded-xl text-xs font-semibold transition flex items-center space-x-2 whitespace-nowrap">
                    <i :class="s.icon"></i>
                    <span x-text="s.name"></span>
                </button>
            </template>
        </div>
    </nav>

    <!-- ALPINE.JS APP LOGIC -->
    <script>
        function lumiApp() {
            return {
                currentScreen: 1,
                progress: 10,
                materiTab: 1,
                
                // Navigation Config
                navScreens: [
                    { id: 1, name: 'Beranda', icon: 'fa-solid fa-house' },
                    { id: 2, name: 'Menu', icon: 'fa-solid fa-table-cells' },
                    { id: 3, name: 'Materi', icon: 'fa-solid fa-book' },
                    { id: 4, name: 'Kuis', icon: 'fa-solid fa-list-check' },
                    { id: 5, name: 'Simulasi', icon: 'fa-solid fa-gamepad' },
                    { id: 6, name: 'Video', icon: 'fa-solid fa-video' },
                    { id: 7, name: 'Rangkuman', icon: 'fa-solid fa-file-lines' },
                    { id: 8, name: 'Profil', icon: 'fa-solid fa-user' },
                ],

                // Materi Sub-topics
                materiList: [
                    { title: 'Pengertian OS' },
                    { title: 'Fungsi Utama OS' },
                    { title: 'Jenis-Jenis OS' },
                    { title: 'Struktur Arsitektur' },
                    { title: 'Manajemen Proses' },
                    { title: 'Manajemen Memori' },
                ],

                // Quiz State & Questions
                quizIndex: 0,
                selectedAnswer: null,
                answerSubmitted: false,
                quizScore: 0,
                quizCompleted: false,
                quizQuestions: [
                    {
                        question: "1. Apa fungsi utama dari sistem operasi?",
                        options: [
                            "Mengelola perangkat keras dan sumber daya komputer",
                            "Menyimpan data pengguna secara permanen",
                            "Menjalankan aplikasi grafis saja",
                            "Mengatur koneksi internet"
                        ],
                        correct: 0,
                        feedback: "Tepat sekali! Fungsi utama OS adalah mengelola hardware dan sumber daya sistem komputer."
                    },
                    {
                        question: "2. Manakah di bawah ini yang *bukan* merupakan contoh sistem operasi?",
                        options: [
                            "Linux Ubuntu",
                            "Microsoft Windows 11",
                            "Microsoft Word",
                            "Google Android"
                        ],
                        correct: 2,
                        feedback: "Benar! Microsoft Word adalah program aplikasi pengolah kata, bukan Sistem Operasi."
                    }
                ],

                // Simulation State
                simRunning: false,
                activeProcess: null,
                processes: [
                    { id: 1, total: 4, remaining: 4, color: 'bg-emerald-500' },
                    { id: 2, total: 3, remaining: 3, color: 'bg-amber-500' },
                    { id: 3, total: 5, remaining: 5, color: 'bg-sky-500' },
                    { id: 4, total: 2, remaining: 2, color: 'bg-purple-500' },
                ],

                navigateTo(id) {
                    this.currentScreen = id;
                    // Calculate Progress
                    this.progress = Math.max(this.progress, Math.round((id / 8) * 100));
                },

                selectAnswer(idx) {
                    if (!this.answerSubmitted) {
                        this.selectedAnswer = idx;
                    }
                },

                submitAnswer() {
                    if (this.selectedAnswer !== null) {
                        this.answerSubmitted = true;
                        if (this.selectedAnswer === this.quizQuestions[this.quizIndex].correct) {
                            this.quizScore += (100 / this.quizQuestions.length);
                        }
                    }
                },

                resetQuizState() {
                    this.selectedAnswer = null;
                    this.answerSubmitted = false;
                },

                nextQuestion() {
                    if (this.quizIndex + 1 < this.quizQuestions.length) {
                        this.quizIndex++;
                        this.resetQuizState();
                    } else {
                        this.quizCompleted = true;
                    }
                },

                restartQuiz() {
                    this.quizIndex = 0;
                    this.quizScore = 0;
                    this.quizCompleted = false;
                    this.resetQuizState();
                },

                startSimulation() {
                    if (this.simRunning) return;
                    this.simRunning = true;
                    
                    let pIdx = 0;
                    const interval = setInterval(() => {
                        // Find next process with remaining time
                        let count = 0;
                        while (this.processes[pIdx].remaining === 0 && count < this.processes.length) {
                            pIdx = (pIdx + 1) % this.processes.length;
                            count++;
                        }

                        if (count === this.processes.length) {
                            // All done
                            clearInterval(interval);
                            this.simRunning = false;
                            this.activeProcess = null;
                            return;
                        }

                        this.activeProcess = pIdx;
                        this.processes[pIdx].remaining--;
                        pIdx = (pIdx + 1) % this.processes.length;
                    }, 1000);
                },

                resetSimulation() {
                    this.simRunning = false;
                    this.activeProcess = null;
                    this.processes = [
                        { id: 1, total: 4, remaining: 4, color: 'bg-emerald-500' },
                        { id: 2, total: 3, remaining: 3, color: 'bg-amber-500' },
                        { id: 3, total: 5, remaining: 5, color: 'bg-sky-500' },
                        { id: 4, total: 2, remaining: 2, color: 'bg-purple-500' },
                    ];
                }
            }
        }
    </script>
</body>
</html>
