<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Construction Checklist Creator</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <!-- jsPDF-AutoTable plugin -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.23/jspdf.plugin.autotable.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        .card {
            transition: all 0.3s ease-in-out;
        }
        .card:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        .btn {
            transition: all 0.2s ease-in-out;
        }
        .btn:hover {
            transform: scale(1.05);
        }
        #generatedHtmlContainer {
            display: none;
        }
        .feedback-msg {
            transition: opacity 0.5s ease-in-out;
        }
        .section-container {
            border: 1px solid #e5e7eb;
            border-radius: 0.75rem;
            padding: 1rem;
            margin-top: 1.5rem;
            background-color: #f9fafb;
        }
        #signature-pad {
            border: 2px dashed #ccc;
            border-radius: 0.5rem;
            cursor: crosshair;
        }
    </style>
</head>
<body class="bg-gray-100 text-gray-800">

    <div class="container mx-auto p-4 md:p-8 max-w-3xl">
        <header class="text-center mb-8">
            <h1 class="text-4xl font-bold text-gray-900">Construction Checklist Creator</h1>
            <p class="text-lg text-gray-600 mt-2">Design and generate interactive checklists for field inspections.</p>
        </header>

        <main class="space-y-8">
            <!-- Creator Form Section -->
            <div class="bg-white p-6 rounded-xl shadow-lg">
                <h2 class="text-2xl font-semibold mb-6 border-b pb-3">1. Project Information</h2>
                <div class="grid grid-cols-1 gap-4">
                    <input type="text" id="projectCode" placeholder="Project Code" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                    <input type="text" id="projectTitle" placeholder="Project Title" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                    <input type="text" id="checklistTitle" placeholder="Checklist Title" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                </div>

                <div class="flex justify-between items-center mt-8 mb-6 border-b pb-3">
                    <h2 class="text-2xl font-semibold">2. Build Checklist</h2>
                    <button onclick="document.getElementById('json-upload').click()" class="btn bg-gray-200 text-gray-700 py-2 px-4 rounded-lg font-semibold hover:bg-gray-300 text-sm">Open Saved Template</button>
                    <input type="file" id="json-upload" class="hidden" accept="application/json" onchange="loadJson(event)">
                </div>
                <div id="sectionsContainer" class="space-y-6">
                    <!-- Dynamic sections will be added here -->
                </div>
                <button onclick="addSection()" class="btn mt-6 w-full bg-green-600 text-white py-2 px-4 rounded-lg font-semibold shadow hover:bg-green-700">Add New Section</button>
            </div>

            <!-- Generated HTML Section -->
            <div class="bg-white p-6 rounded-xl shadow-lg">
                <h2 class="text-2xl font-semibold mb-6 border-b pb-3">3. Generate & Share</h2>
                <button id="generateBtn" onclick="generateChecklist()" class="btn w-full bg-indigo-600 text-white py-3 px-6 rounded-lg font-bold text-lg shadow-lg hover:bg-indigo-700 mb-4">
                    Generate Interactive Checklist
                </button>
                
                <div id="generatedHtmlContainer">
                    <textarea id="htmlOutput" class="w-full h-64 p-3 border border-gray-300 rounded-lg bg-gray-50 font-mono text-sm" readonly></textarea>
                    <div class="mt-4 grid grid-cols-1 md:grid-cols-3 gap-4">
                        <button onclick="copyHtml()" class="btn w-full bg-gray-700 text-white py-2 px-4 rounded-lg font-semibold hover:bg-gray-800">Copy Code</button>
                        <button onclick="downloadHtml()" class="btn w-full bg-teal-500 text-white py-2 px-4 rounded-lg font-semibold hover:bg-teal-600">Download Checklist</button>
                        <button onclick="saveJson()" class="btn w-full bg-orange-500 text-white py-2 px-4 rounded-lg font-semibold hover:bg-orange-600">Save Template</button>
                    </div>
                     <p id="copy-success-msg" class="feedback-msg text-green-600 text-center mt-2 opacity-0 font-medium">Copied to clipboard!</p>
                     <p id="download-success-msg" class="feedback-msg text-teal-600 text-center mt-2 opacity-0 font-medium">Download started!</p>
                </div>
            </div>
        </main>
    </div>

    <script>
        let sectionCounter = 0;
        let questionCounter = 0;

        function addSection(title = '') {
            sectionCounter++;
            const container = document.getElementById('sectionsContainer');
            const sectionId = `section-${sectionCounter}`;

            const sectionDiv = document.createElement('div');
            sectionDiv.className = 'section-container card';
            sectionDiv.id = sectionId;

            sectionDiv.innerHTML = `
                <div class="flex justify-between items-center mb-4">
                    <input type="text" placeholder="Section Title" class="section-title text-lg font-semibold w-full p-2 border border-gray-300 rounded-md" value="${title}">
                    <button onclick="removeSection('${sectionId}')" class="ml-4 text-red-500 hover:text-red-700 font-bold text-2xl">&times;</button>
                </div>
                <div class="questions-container space-y-4"></div>
                <button onclick="addQuestion('${sectionId}')" class="btn mt-4 bg-blue-500 text-white py-2 px-4 rounded-lg font-semibold shadow hover:bg-blue-600 text-sm">Add Question</button>
            `;
            container.appendChild(sectionDiv);
            return sectionId;
        }
        
        function removeSection(sectionId) {
            document.getElementById(sectionId)?.remove();
        }

        function addQuestion(sectionId, text = '', type = 'yesno') {
            questionCounter++;
            const container = document.querySelector(`#${sectionId} .questions-container`);
            const questionId = `question-${questionCounter}`;

            const questionCard = document.createElement('div');
            questionCard.className = 'bg-white p-4 border border-gray-200 rounded-lg shadow-sm';
            questionCard.id = questionId;

            questionCard.innerHTML = `
                <div class="flex justify-between items-start mb-2">
                    <input type="text" placeholder="Enter your question here..." class="w-full p-2 border border-gray-300 rounded-md question-text" value="${text}">
                    <button onclick="removeQuestion('${questionId}')" class="ml-2 text-red-500 hover:text-red-700 font-bold text-xl">&times;</button>
                </div>
                <div class="flex items-center mt-2">
                     <label class="text-sm font-medium text-gray-700 mr-2">Answer Type:</label>
                     <select class="question-type p-2 border border-gray-300 rounded-md text-sm">
                         <option value="yesno" ${type === 'yesno' ? 'selected' : ''}>Yes/No/NA</option>
                         <option value="text" ${type === 'text' ? 'selected' : ''}>Data Entry</option>
                         <option value="truefalse" ${type === 'truefalse' ? 'selected' : ''}>True/False</option>
                     </select>
                </div>
            `;
            container.appendChild(questionCard);
        }

        function removeQuestion(questionId) {
            document.getElementById(questionId)?.remove();
        }

        function generateChecklist() {
            const escapeHTML = (str) => str ? str.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&quot;').replace(/'/g, '&#039;') : '';

            const projectData = {
                projectCode: document.getElementById('projectCode').value,
                projectTitle: document.getElementById('projectTitle').value,
                checklistTitle: document.getElementById('checklistTitle').value,
                sections: []
            };

            document.querySelectorAll('.section-container').forEach(sectionEl => {
                const sectionData = {
                    title: sectionEl.querySelector('.section-title').value,
                    questions: []
                };
                sectionEl.querySelectorAll('.questions-container > div').forEach(questionEl => {
                    sectionData.questions.push({
                        text: questionEl.querySelector('.question-text').value,
                        type: questionEl.querySelector('.question-type').value
                    });
                });
                projectData.sections.push(sectionData);
            });

            const template = `
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>${escapeHTML(projectData.checklistTitle)}</title>
    <script src="https://cdn.tailwindcss.com"><\/script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"><\/script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.23/jspdf.plugin.autotable.min.js"><\/script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
    <style> 
        body { font-family: 'Inter', sans-serif; } 
        .slide { animation: fadeIn 0.5s; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        #signature-pad { border: 2px dashed #ccc; border-radius: 0.5rem; cursor: crosshair; }
    </style>
</head>
<body class="bg-gray-50">
    <div id="checklistRoot" class="container mx-auto max-w-4xl p-4 md:p-8">
    </div>
    
    <script id="checklist-data" type="application/json">
        __CHECKLIST_DATA__
    <\/script>

    <script>
        __CHECKLIST_LOGIC__
    <\/script>
</body>
</html>
`;
            const checklistLogic = `
        window.jsPDF = window.jspdf.jsPDF;

        let currentSlide = 0;
        const slides = [];
        let totalQuestions = 0;
        const checklistData = JSON.parse(document.getElementById('checklist-data').textContent);

        function buildSlides() {
            const root = document.getElementById('checklistRoot');
            
            let headerHtml = \`
                <header id="mainHeader" class="bg-white p-6 rounded-xl shadow-md mb-8 border border-gray-200 text-center">
                    <p class="text-lg text-gray-500 font-mono">\${checklistData.projectCode}</p>
                    <h1 class="text-3xl font-bold text-gray-900 mt-2">\${checklistData.projectTitle}</h1>
                    <h2 class="text-2xl font-semibold text-gray-700 mt-1">\${checklistData.checklistTitle}</h2>
                </header>
            \`;

            let formHtml = '<form id="inspectionForm">';

            let timeOptions = '';
            for (let i = 0; i < 24; i++) {
                for (let j = 0; j < 60; j += 30) {
                    const hour24 = i;
                    const minute = j.toString().padStart(2, '0');
                    const ampm = hour24 >= 12 ? 'PM' : 'AM';
                    let hour12 = hour24 % 12;
                    hour12 = hour12 ? hour12 : 12; // the hour '0' should be '12'
                    const timeString = hour12.toString().padStart(2, '0') + ':' + minute + ' ' + ampm;
                    timeOptions += \`<option value="\${timeString}">\${timeString}</option>\`;
                }
            }

            formHtml += \`
                <div class="slide bg-white p-6 rounded-xl shadow-md border border-gray-200" data-slide-type="start">
                    <h2 class="text-2xl font-bold text-gray-800 mb-4">Inspection Details</h2>
                    <div class="space-y-4">
                        <div><label class="font-semibold">Inspector:</label><input type="text" id="inspectorNameInput" class="w-full p-2 border rounded-md mt-1"></div>
                        <div><label class="font-semibold">Date:</label><input type="date" id="inspectionDateGenerated" class="w-full p-2 border rounded-md mt-1"></div>
                        <div><label class="font-semibold">Location:</label><input type="text" id="locationInput" class="w-full p-2 border rounded-md mt-1"></div>
                        <div><label class="font-semibold">Contractor/Subcontractor:</label><input type="text" id="contractorInput" class="w-full p-2 border rounded-md mt-1"></div>
                        <div class="grid grid-cols-2 gap-4">
                            <div><label class="font-semibold">Start Time:</label><select id="startTimeInput" class="w-full p-2 border rounded-md mt-1">\${timeOptions}</select></div>
                            <div><label class="font-semibold">End Time:</label><select id="endTimeInput" class="w-full p-2 border rounded-md mt-1">\${timeOptions}</select></div>
                        </div>
                        <div><label class="font-semibold">Description of Work:</label><textarea id="workDescriptionInput" class="w-full p-2 border rounded-md mt-1" rows="3"></textarea></div>
                    </div>
                </div>\`;
            
            let questionIndex = 0;
            checklistData.sections.forEach((section, sectionIndex) => {
                if (section.questions.length > 0) {
                    section.questions.forEach((q, qIndex) => {
                        questionIndex++;
                        let answerHtml = '';
                        switch (q.type) {
                            case 'text':
                                answerHtml = \`<textarea name="q\${questionIndex}_answer" class="w-full p-2 border border-gray-300 rounded-md mt-2" placeholder="Enter notes..."></textarea>\`;
                                break;
                            case 'yesno':
                                answerHtml = \`
                                    <div class="flex space-x-4 mt-2 text-sm">
                                        <label class="flex items-center"><input type="radio" name="q\${questionIndex}_answer" value="Yes" class="mr-1"> Yes</label>
                                        <label class="flex items-center"><input type="radio" name="q\${questionIndex}_answer" value="No" class="mr-1"> No</label>
                                        <label class="flex items-center"><input type="radio" name="q\${questionIndex}_answer" value="NA" class="mr-1"> N/A</label>
                                    </div>\`;
                                break;
                            case 'truefalse':
                                 answerHtml = \`
                                    <div class="flex space-x-4 mt-2 text-sm">
                                        <label class="flex items-center"><input type="radio" name="q\${questionIndex}_answer" value="True" class="mr-1"> True</label>
                                        <label class="flex items-center"><input type="radio" name="q\${questionIndex}_answer" value="False" class="mr-1"> False</label>
                                    </div>\`;
                                break;
                        }

                        formHtml += \`
                            <div class="slide bg-white p-6 rounded-xl shadow-md border border-gray-200 hidden" data-slide-type="question" data-section-index="\${sectionIndex}" data-section-title="\${section.title}" data-question-text="\${q.text}" data-is-first-question="\${qIndex === 0}" data-question-in-section="\${qIndex + 1}" data-total-in-section="\${section.questions.length}">
                                <p class="text-2xl font-bold text-gray-800 mb-2">\${section.title}</p>
                                <p class="text-sm text-gray-500">Question \${qIndex + 1} of \${section.questions.length}</p>
                                <p class="font-semibold text-gray-800 mt-4 text-lg">\${q.text}</p>
                                <div class="mt-4">\${answerHtml}</div>
                                <div class="mt-4">
                                    <label class="font-semibold text-gray-700 text-sm">Notes:</label>
                                    <textarea name="q\${questionIndex}_notes" class="w-full p-2 border border-gray-300 rounded-md mt-1" placeholder="Add optional notes..."></textarea>
                                </div>
                            </div>\`;
                    });
                }
            });
            totalQuestions = questionIndex;

            formHtml += \`
                <div class="slide bg-white p-6 rounded-xl shadow-md border border-gray-200 hidden" data-slide-type="final" data-section-title="General Notes">
                    <h2 class="text-2xl font-bold text-gray-800 mb-4">General Notes</h2>
                    <textarea id="generalNotes" class="w-full p-2 border border-gray-300 rounded-md" rows="6" placeholder="Enter any additional general notes or comments here..."></textarea>
                </div>
                <div class="slide bg-white p-6 rounded-xl shadow-md border border-gray-200 hidden" data-slide-type="final" data-section-title="Findings">
                    <h2 class="text-2xl font-bold text-gray-800 mb-4">Safety/Quality Findings</h2>
                    <div id="findingsContainer" class="space-y-4"></div>
                    <button type="button" onclick="addFinding()" class="btn mt-4 bg-blue-500 text-white py-2 px-4 rounded-lg font-semibold shadow hover:bg-blue-600 text-sm">Add Finding</button>
                </div>
                 <div class="slide bg-white p-6 rounded-xl shadow-md border border-gray-200 hidden" data-slide-type="final" data-section-title="Photos">
                    <h2 class="text-2xl font-bold text-gray-800 mb-4">Attach Photos</h2>
                    <div id="photosContainer" class="space-y-4"></div>
                    <button type="button" onclick="addPhoto()" class="btn mt-4 bg-blue-500 text-white py-2 px-4 rounded-lg font-semibold shadow hover:bg-blue-600 text-sm">Add Photo</button>
                </div>
                <div class="slide bg-white p-6 rounded-xl shadow-md border border-gray-200 hidden" data-slide-type="final" data-section-title="Signature">
                    <h2 class="text-2xl font-bold text-gray-800 mb-4">Inspector Signature</h2>
                    <canvas id="signature-pad" width="400" height="200"></canvas>
                    <button type="button" onclick="clearSignature()" class="mt-2 text-sm text-blue-600 hover:underline">Clear Signature</button>
                </div>
            \`;
            formHtml += '</form>';
            
            let controlsHtml = \`
                <div id="progressContainer" class="mt-8">
                    <div class="flex justify-between mb-1"><span id="progressText" class="text-base font-medium text-gray-700"></span></div>
                    <div class="w-full bg-gray-200 rounded-full h-2.5"><div id="progressBar" class="bg-blue-600 h-2.5 rounded-full" style="width: 0%"></div></div>
                </div>
                <div id="navigation" class="flex justify-between mt-4">
                    <button id="prevBtn" onclick="navigate(-1)" class="bg-gray-300 text-gray-800 font-bold py-2 px-6 rounded-lg hover:bg-gray-400">Previous</button>
                    <button id="skipBtn" onclick="skipAction()" class="bg-yellow-500 text-white font-bold py-2 px-6 rounded-lg hover:bg-yellow-600 hidden">Skip</button>
                    <button id="nextBtn" onclick="navigate(1)" class="bg-blue-600 text-white font-bold py-2 px-6 rounded-lg hover:bg-blue-700">Next</button>
                </div>
                <div id="finishScreen" class="mt-8 text-center hidden">
                     <p class="text-2xl font-bold text-green-600">Checklist Complete!</p>
                    <button id="pdfButton" onclick="generatePdf()" class="mt-4 bg-indigo-600 text-white font-bold py-3 px-8 rounded-lg shadow-lg hover:bg-indigo-700">Save & Share</button>
                    <div id="loader" class="hidden mt-4"><p class="text-lg text-indigo-600">Generating PDF...</p></div>
                </div>
            \`;

            root.innerHTML = headerHtml + formHtml + controlsHtml;
            slides.push(...document.querySelectorAll('.slide'));
            
            if (slides.length > 0) {
                document.getElementById('inspectionDateGenerated').valueAsDate = new Date();
                showSlide(0);
                setupSignaturePad();
                attachAnswerListeners();
            } else {
                document.getElementById('navigation').classList.add('hidden');
                document.getElementById('progressContainer').classList.add('hidden');
            }
        }
        
        function showSlide(n) {
            slides.forEach(slide => slide.classList.add('hidden'));
            if (slides[n]) slides[n].classList.remove('hidden');

            const slideType = slides[n] ? slides[n].dataset.slideType : '';
            const isFirstQuestion = slides[n]?.dataset.isFirstQuestion === 'true';
            const skipBtn = document.getElementById('skipBtn');
            const nextBtn = document.getElementById('nextBtn');
            
            const skippableFinals = ['General Notes', 'Findings', 'Photos'];
            const isSkippable = isFirstQuestion || skippableFinals.includes(slides[n]?.dataset.sectionTitle);
            skipBtn.classList.toggle('hidden', !isSkippable);
            
            if (isFirstQuestion) {
                skipBtn.innerText = 'Skip Section';
            } else {
                skipBtn.innerText = 'Skip';
            }
            
            nextBtn.innerText = (n === slides.length - 1) ? 'Finish' : 'Next';

            const questionInSection = slides[n]?.dataset.questionInSection;
            const totalInSection = slides[n]?.dataset.totalInSection;

            if (slideType === 'start') {
                 document.getElementById('progressText').innerText = 'Inspector Details';
                 document.getElementById('progressBar').style.width = '0%';
            } else if (slideType === 'question') {
                const remainingQuestions = slides.filter((s, i) => i >= n && s.dataset.slideType === 'question' && s.dataset.skipped !== 'true').length;
                 document.getElementById('progressText').innerText = \`\${slides[n].dataset.sectionTitle} - Question \${questionInSection} of \${totalInSection} (\${remainingQuestions} total remaining)\`;
                 const completedQuestions = totalQuestions - remainingQuestions;
                 document.getElementById('progressBar').style.width = \`\${(completedQuestions / totalQuestions) * 100}%\`;
            } else {
                 document.getElementById('progressText').innerText = slides[n].dataset.sectionTitle || 'Final Steps';
                 document.getElementById('progressBar').style.width = '100%';
            }


            document.getElementById('prevBtn').disabled = n === 0;
            document.getElementById('prevBtn').classList.toggle('opacity-50', n === 0);
        }

        function navigate(n) {
            if (currentSlide === slides.length - 1 && n === 1) {
                document.getElementById('navigation').classList.add('hidden');
                document.getElementById('progressContainer').classList.add('hidden');
                document.getElementById('finishScreen').classList.remove('hidden');
                slides.forEach(slide => slide.classList.add('hidden'));
                return;
            }
            
            currentSlide = Math.max(0, Math.min(slides.length - 1, currentSlide + n));
            showSlide(currentSlide);
        }

        function skipAction() {
            const isFirstQuestion = slides[currentSlide]?.dataset.isFirstQuestion === 'true';

            if (isFirstQuestion) {
                const currentSectionIndex = slides[currentSlide].dataset.sectionIndex;
                slides.forEach(s => {
                    if (s.dataset.sectionIndex === currentSectionIndex) {
                        s.dataset.skipped = 'true';
                    }
                });
                
                let nextSlideIndex = -1;
                for (let i = currentSlide + 1; i < slides.length; i++) {
                    if (slides[i].dataset.sectionIndex !== currentSectionIndex) {
                        nextSlideIndex = i;
                        break;
                    }
                }

                if (nextSlideIndex !== -1) {
                    currentSlide = nextSlideIndex;
                } else { 
                    currentSlide = slides.findIndex(s => s.dataset.slideType === 'final');
                }
                showSlide(currentSlide);
            } else {
                navigate(1);
            }
        }

        function attachAnswerListeners() {
            slides.forEach(slide => {
                if (slide.dataset.slideType === 'question') {
                    const inputs = slide.querySelectorAll('[name$="_answer"], [name$="_notes"]');
                    inputs.forEach(input => {
                        input.addEventListener('input', () => {
                            const sectionIndex = slide.dataset.sectionIndex;
                            slides.forEach(s => {
                                if (s.dataset.sectionIndex === sectionIndex) {
                                    delete s.dataset.skipped;
                                }
                            });
                        });
                    });
                }
            });
        }

        let findingCounter = 0;
        function addFinding() {
            findingCounter++;
            const container = document.getElementById('findingsContainer');
            const findingId = 'finding-' + findingCounter;
            const div = document.createElement('div');
            div.id = findingId;
            div.className = 'p-2 border rounded-md bg-gray-50';
            div.innerHTML = \`<div class="flex justify-between items-center mb-2"><label class="font-semibold text-sm">Finding #\${findingCounter}</label><button type="button" onclick="document.getElementById('\${findingId}').remove()" class="text-red-500 font-bold">&times;</button></div><textarea class="w-full p-2 border rounded-md finding-text" placeholder="Describe finding..."></textarea><select class="w-full p-2 border rounded-md mt-2 finding-status"><option>Work in Progress</option><option>Resolved</option></select>\`;
            container.appendChild(div);
        }
        
        let photoCounter = 0;
        function addPhoto() {
            photoCounter++;
            const container = document.getElementById('photosContainer');
            const photoId = 'photo-' + photoCounter;
            const div = document.createElement('div');
            div.id = photoId;
            div.className = 'p-2 border rounded-md bg-gray-50 photo-entry';
            div.innerHTML = \`<div class="flex justify-between items-center mb-2"><label class="font-semibold text-sm">Photo #\${photoCounter}</label><button type="button" onclick="document.getElementById('\${photoId}').remove()" class="text-red-500 font-bold">&times;</button></div><input type="file" class="w-full text-sm photo-input" accept="image/*" onchange="previewPhoto(this)"><img class="mt-2 rounded-lg max-w-xs hidden photo-preview" alt="Photo preview"><input type="text" class="w-full p-2 border rounded-md mt-2 photo-caption" placeholder="Enter caption...">\`;
            container.appendChild(div);
        }
        
        async function previewPhoto(input) {
            const preview = input.nextElementSibling;
            if (input.files && input.files[0]) {
                const file = input.files[0];
                preview.src = URL.createObjectURL(file);
                preview.classList.remove('hidden');
            }
        }

        let signaturePad, ctx, drawing = false;
        function setupSignaturePad() {
            signaturePad = document.getElementById('signature-pad');
            if (!signaturePad) return;
            ctx = signaturePad.getContext('2d');
            
            signaturePad.addEventListener('mousedown', (e) => {
                drawing = true;
                ctx.beginPath();
                ctx.moveTo(e.offsetX, e.offsetY);
            });
            signaturePad.addEventListener('mousemove', (e) => {
                if (drawing) {
                    ctx.lineTo(e.offsetX, e.offsetY);
                    ctx.stroke();
                }
            });
             signaturePad.addEventListener('mouseup', () => drawing = false);
            signaturePad.addEventListener('mouseout', () => drawing = false);

            signaturePad.addEventListener('touchstart', (e) => {
                e.preventDefault();
                drawing = true;
                const touch = e.touches[0];
                const rect = signaturePad.getBoundingClientRect();
                ctx.beginPath();
                ctx.moveTo(touch.clientX - rect.left, touch.clientY - rect.top);
            });
            signaturePad.addEventListener('touchmove', (e) => {
                e.preventDefault();
                if (drawing) {
                    const touch = e.touches[0];
                    const rect = signaturePad.getBoundingClientRect();
                    ctx.lineTo(touch.clientX - rect.left, touch.clientY - rect.top);
                    ctx.stroke();
                }
            });
            window.addEventListener('touchend', () => drawing = false);
        }
        function clearSignature() {
            if(ctx) ctx.clearRect(0, 0, signaturePad.width, signaturePad.height);
        }

        async function generatePdf() {
            document.getElementById('loader').classList.remove('hidden');
            document.getElementById('pdfButton').classList.add('hidden');
            
            const doc = new jsPDF();
            const inspectorName = document.getElementById('inspectorNameInput').value;
            const inspectionDateRaw = document.getElementById('inspectionDateGenerated').value;
            const location = document.getElementById('locationInput').value;
            const workDescription = document.getElementById('workDescriptionInput').value;
            const startTime = document.getElementById('startTimeInput').value;
            const endTime = document.getElementById('endTimeInput').value;
            const date = new Date(inspectionDateRaw + 'T00:00:00');
            const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            const formattedDate = date.toLocaleDateString('en-US', options);

            const addHeaderAndFooter = (doc) => {
                const pageCount = doc.internal.getNumberOfPages();
                for (let i = 1; i <= pageCount; i++) {
                    doc.setPage(i);
                    doc.setFontSize(10);
                    doc.setFont('times', 'bold');
                    doc.text(checklistData.projectCode + " - " + checklistData.projectTitle, doc.internal.pageSize.getWidth() / 2, 15, { align: 'center' });
                    doc.setFontSize(12);
                    doc.setFont('times', 'bold');
                    doc.text(checklistData.checklistTitle, doc.internal.pageSize.getWidth() / 2, 25, { align: 'center' });
                    doc.setFontSize(10);
                    doc.setFont('times', 'normal');
                    doc.text('Inspector: ' + inspectorName, 14, 35);
                    doc.text('Date: ' + formattedDate, 196, 35, { align: 'right' });
                    doc.setFontSize(8);
                    doc.text(checklistData.checklistTitle + ' - Page ' + i + ' of ' + pageCount, 14, doc.internal.pageSize.getHeight() - 10);
                }
            };

            const answeredSections = new Set();
            const allSections = new Map();

            slides.forEach((slide) => {
                if(slide.dataset.slideType !== 'question') return;
                const sectionIndex = slide.dataset.sectionIndex;
                const sectionTitle = slide.dataset.sectionTitle;
                if (!allSections.has(sectionIndex)) {
                    allSections.set(sectionIndex, sectionTitle);
                }

                const input = slide.querySelector('[name$="_answer"]');
                const notesInput = slide.querySelector('[name$="_notes"]');
                let isAnswered = false;
                if (input.type === 'textarea') {
                    if (input.value.trim() !== '') isAnswered = true;
                } else if (input.type === 'radio') {
                    if (slide.querySelector('input[name="' + input.name + '"]:checked')) isAnswered = true;
                }
                if (notesInput && notesInput.value.trim() !== '') {
                    isAnswered = true;
                }

                if (isAnswered) {
                    answeredSections.add(sectionIndex);
                }
            });

            const tableData = [];
            let currentSection = '';
            let questionNumber = 0;

            slides.forEach((slide) => {
                const sectionIndex = slide.dataset.sectionIndex;
                if(slide.dataset.slideType !== 'question' || !answeredSections.has(sectionIndex)) return;
                
                const sectionTitle = slide.dataset.sectionTitle;
                if (sectionTitle !== currentSection) {
                    tableData.push([{ content: sectionTitle, colSpan: 3, styles: { fontStyle: 'bold', fillColor: [230, 230, 230], textColor: [50, 50, 50] } }]);
                    currentSection = sectionTitle;
                    questionNumber = 0;
                }
                
                questionNumber++;
                let questionText = slide.dataset.questionText;
                const notesInput = slide.querySelector('[name$="_notes"]');
                const notes = notesInput ? notesInput.value.trim() : '';
                const input = slide.querySelector('[name$="_answer"]');
                let answer = 'Not Answered';

                if (input.type === 'textarea') {
                    if(input.value.trim() !== '') answer = input.value;
                } else if (input.type === 'radio') {
                    const checked = slide.querySelector('input[name="' + input.name + '"]:checked');
                    if(checked) answer = checked.value;
                }

                if (notes) {
                    answer += '\\n\\nNotes: ' + notes;
                }

                tableData.push([questionNumber, questionText, answer]);
            });
            
            doc.autoTable({
                body: [
                    [{ content: 'Location:', styles: { fontStyle: 'bold' } }, location],
                    [{ content: 'Contractor/Sub:', styles: { fontStyle: 'bold' } }, document.getElementById('contractorInput').value],
                    [{ content: 'Work Hours:', styles: { fontStyle: 'bold' } }, \`\${startTime} to \${endTime}\`],
                    [{ content: 'Description of Work:', styles: { fontStyle: 'bold' } }, workDescription],
                ],
                startY: 40,
                theme: 'grid',
                styles: { fontSize: 10 },
            });

            if (tableData.length > 0) {
                doc.autoTable({
                    head: [['No.', 'Description', 'Response & Notes']],
                    body: tableData,
                    startY: doc.autoTable.previous.finalY + 5,
                    theme: 'grid',
                    headStyles: { fillColor: [41, 128, 185], textColor: [255, 255, 255], fontStyle: 'bold' },
                    alternateRowStyles: { fillColor: [245, 245, 245] },
                    columnStyles: { 0: { cellWidth: 15 }, 1: { cellWidth: 120 }, 2: { cellWidth: 'auto' } },
                    didParseCell: function (data) {
                        if (data.row.raw.length === 1) {
                            data.cell.styles.halign = 'left';
                        }
                    },
                    margin: { top: 40 }
                });
            }
            
            const skippedSectionTitles = [];
            allSections.forEach((title, index) => {
                if (!answeredSections.has(index)) {
                    skippedSectionTitles.push(title);
                }
            });

            if (skippedSectionTitles.length > 0) {
                doc.autoTable({
                    body: [
                        [{ content: 'Skipped Sections', styles: { fontStyle: 'bold', fillColor: [245, 245, 245], textColor: [50, 50, 50] } }],
                        [skippedSectionTitles.join(', ')]
                    ],
                    startY: doc.autoTable.previous.finalY + 5,
                    theme: 'grid',
                    styles: { fontSize: 10 },
                });
            }

            const generalNotes = document.getElementById('generalNotes').value.trim();
            if (generalNotes) {
                doc.autoTable({
                    body: [[{ content: 'General Notes', styles: { fontStyle: 'bold' } }], [generalNotes]],
                    startY: doc.autoTable.previous.finalY + 5,
                    theme: 'grid',
                    styles: { fontSize: 10 },
                });
            }

            const findingsData = [];
            document.querySelectorAll('#findingsContainer > div').forEach(el => {
                const text = el.querySelector('.finding-text').value;
                const status = el.querySelector('.finding-status').value;
                if (text) findingsData.push([text, status]);
            });

            if (findingsData.length > 0) {
                doc.autoTable({
                    head: [['Finding Description', 'Status']],
                    body: findingsData,
                    startY: doc.autoTable.previous.finalY + 5,
                    theme: 'grid',
                    headStyles: { fillColor: [231, 76, 60] },
                     margin: { top: 40 }
                });
            }
            
            const photoEntries = document.querySelectorAll('.photo-entry');
            if(photoEntries.length > 0 && Array.from(photoEntries).some(e => e.querySelector('.photo-preview').src)) {
                doc.addPage();
                let yPos = 45;
                
                for (const entry of photoEntries) {
                    const imgPreview = entry.querySelector('.photo-preview');
                    const caption = entry.querySelector('.photo-caption').value;
                    const imgSrc = imgPreview.src;

                    if (imgSrc && imgSrc.startsWith('blob:')) {
                        const tempImg = new Image();
                        tempImg.src = imgSrc;
                        
                        const pageHeight = doc.internal.pageSize.getHeight();
                        const pageWidth = doc.internal.pageSize.getWidth();
                        const margin = 14;
                        const usableWidth = pageWidth - (margin * 2);

                        let imgHeight = 101.6; 
                        const ratio = tempImg.width / tempImg.height;
                        let imgWidth = imgHeight * ratio;

                        if (imgWidth > usableWidth) {
                            imgWidth = usableWidth;
                            imgHeight = imgWidth / ratio;
                        }
                        
                        const requiredSpace = imgHeight + 20;
                        if (yPos + requiredSpace > pageHeight - margin) {
                            doc.addPage();
                            yPos = 45;
                        }
                        
                        const xPos = margin + (usableWidth - imgWidth) / 2;

                        doc.addImage(imgSrc, 'JPEG', xPos, yPos, imgWidth, imgHeight);
                        
                        doc.setFontSize(9);
                        doc.setFont(undefined, 'normal');
                        doc.text(caption, pageWidth / 2, yPos + imgHeight + 10, {maxWidth: usableWidth, align: 'center'});

                        yPos += requiredSpace;
                    }
                }
            }

            const signatureData = signaturePad.toDataURL();
            if(!signaturePad.getContext('2d').getImageData(0, 0, signaturePad.width, signaturePad.height).data.some(channel => channel !== 0)) {
                // Signature is empty
            } else {
                 doc.addPage();
                 doc.setFontSize(12);
                 doc.setFont(undefined, 'bold');
                 doc.text("Inspector's Signature", 14, 45);
                 doc.addImage(signatureData, 'PNG', 14, 50, 100, 50);
                 
                 const signingDate = new Date();
                 const signingDateStr = signingDate.toLocaleDateString('en-US', { year: 'numeric', month: 'long', day: 'numeric' });
                 const signingTimeStr = signingDate.toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit' });
                 
                 doc.setFontSize(10);
                 doc.setFont(undefined, 'normal');
                 doc.text(inspectorName, 14, 105);
                 doc.text(\`Signed: \${signingDateStr} at \${signingTimeStr}\`, 14, 112);
            }

            addHeaderAndFooter(doc);

            const dateForFilename = new Date(inspectionDateRaw + 'T00:00:00');
            const formattedDateFilename = (dateForFilename.getMonth() + 1).toString().padStart(2, '0') + '-' + dateForFilename.getDate().toString().padStart(2, '0') + '-' + dateForFilename.getFullYear();
            const safeFileName = \`\${checklistData.projectCode} - \${checklistData.checklistTitle} - \${formattedDateFilename} - \${inspectorName}\`.replace(/[^a-zA-Z0-9-]/g, '_');

            const isIOS = /iPad|iPhone|iPod/.test(navigator.userAgent) && !window.MSStream;
            if (isIOS) {
                doc.output('dataurlnewwindow');
            } else {
                doc.save(safeFileName + '.pdf');
            }
            
            document.getElementById('loader').classList.add('hidden');
            document.getElementById('pdfButton').classList.remove('hidden');
        }

        buildSlides();
    `;
            const finalHtml = template.replace('__CHECKLIST_DATA__', JSON.stringify(projectData))
                                        .replace('__CHECKLIST_LOGIC__', checklistLogic);
            document.getElementById('htmlOutput').value = finalHtml;
            document.getElementById('generatedHtmlContainer').style.display = 'block';
        }

        function copyHtml() {
            const htmlOutput = document.getElementById('htmlOutput');
            htmlOutput.select();
            document.execCommand('copy');
            const msg = document.getElementById('copy-success-msg');
            msg.style.opacity = 1;
            setTimeout(() => { msg.style.opacity = 0; }, 2000);
        }

        function downloadHtml() {
            const htmlContent = document.getElementById('htmlOutput').value;
            const date = new Date();
            const formattedDate = (date.getMonth() + 1).toString().padStart(2, '0') + '-' + date.getDate().toString().padStart(2, '0') + '-' + date.getFullYear();
            const fileName = `${document.getElementById('projectCode').value || 'project'}-${document.getElementById('checklistTitle').value || 'checklist'}-${formattedDate}`;
            const blob = new Blob([htmlContent], { type: 'text/html' });
            const a = document.createElement('a');
            a.href = URL.createObjectURL(blob);
            a.download = `${fileName}.html`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            
            const msg = document.getElementById('download-success-msg');
            msg.style.opacity = 1;
            setTimeout(() => { msg.style.opacity = 0; }, 2000);
        }

        function saveJson() {
            const data = {
                projectCode: document.getElementById('projectCode').value,
                projectTitle: document.getElementById('projectTitle').value,
                checklistTitle: document.getElementById('checklistTitle').value,
                sections: []
            };

            document.querySelectorAll('.section-container').forEach(sectionEl => {
                const sectionData = {
                    title: sectionEl.querySelector('.section-title').value,
                    questions: []
                };
                sectionEl.querySelectorAll('.questions-container > div').forEach(questionEl => {
                    sectionData.questions.push({
                        text: questionEl.querySelector('.question-text').value,
                        type: questionEl.querySelector('.question-type').value
                    });
                });
                data.sections.push(sectionData);
            });

            const jsonString = JSON.stringify(data, null, 2);
            const date = new Date();
            const formattedDate = (date.getMonth() + 1).toString().padStart(2, '0') + '-' + date.getDate().toString().padStart(2, '0') + '-' + date.getFullYear();
            const fileName = `${data.projectCode || 'project'}-${data.checklistTitle || 'checklist'}-${formattedDate}-template data`;
            const blob = new Blob([jsonString], { type: 'application/json' });
            const a = document.createElement('a');
            a.href = URL.createObjectURL(blob);
            a.download = `${fileName}.json`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
        }

        function loadJson(event) {
            const file = event.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = function(e) {
                try {
                    const data = JSON.parse(e.target.result);
                    
                    document.getElementById('sectionsContainer').innerHTML = '';
                    sectionCounter = 0;
                    questionCounter = 0;

                    document.getElementById('projectCode').value = data.projectCode || '';
                    document.getElementById('projectTitle').value = data.projectTitle || '';
                    document.getElementById('checklistTitle').value = data.checklistTitle || '';

                    if (data.sections) {
                        data.sections.forEach(sectionData => {
                            const newSectionId = addSection(sectionData.title);
                            if (sectionData.questions) {
                                sectionData.questions.forEach(questionData => {
                                    addQuestion(newSectionId, questionData.text, questionData.type);
                                });
                            }
                        });
                    }
                } catch (error) {
                    console.error("Error parsing JSON file:", error);
                    const msg = document.createElement('p');
                    msg.textContent = 'Invalid JSON file. Please check the file and try again.';
                    msg.className = 'text-red-500 text-center font-bold my-4';
                    document.getElementById('generatedHtmlContainer').prepend(msg);
                    setTimeout(() => msg.remove(), 5000);
                }
            };
            reader.readAsText(file);
            event.target.value = '';
        }
    </script>
</body>
</html>
