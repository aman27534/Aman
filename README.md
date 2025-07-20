<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Resume Builder</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 font-sans">
    <div class="container mx-auto p-4 max-w-4xl">
        <h1 class="text-3xl font-bold text-center mb-6">Resume Builder</h1>
        <div class="bg-white shadow-md rounded-lg p-6 mb-6">
            <h2 class="text-xl font-semibold mb-4">Enter Your Details</h2>
            <div class="space-y-4">
                <!-- Personal Information -->
                <div>
                    <h3 class="text-lg font-medium">Personal Information</h3>
                    <input id="name" type="text" placeholder="Full Name" class="w-full p-2 border rounded mt-2">
                    <input id="email" type="email" placeholder="Email" class="w-full p-2 border rounded mt-2">
                    <input id="phone" type="tel" placeholder="Phone Number" class="w-full p-2 border rounded mt-2">
                    <input id="linkedin" type="text" placeholder="LinkedIn URL (optional)" class="w-full p-2 border rounded mt-2">
                </div>
                <!-- Education -->
                <div>
                    <h3 class="text-lg font-medium">Education</h3>
                    <input id="degree" type="text" placeholder="Degree (e.g., B.S. Computer Science)" class="w-full p-2 border rounded mt-2">
                    <input id="school" type="text" placeholder="School Name" class="w-full p-2 border rounded mt-2">
                    <input id="edu-year" type="text" placeholder="Graduation Year" class="w-full p-2 border rounded mt-2">
                </div>
                <!-- Experience -->
                <div>
                    <h3 class="text-lg font-medium">Work Experience</h3>
                    <textarea id="experience" placeholder="Describe your work experience (e.g., Software Intern at XYZ Corp, 2023: Developed web apps)" class="w-full p-2 border rounded mt-2 h-24"></textarea>
                </div>
                <!-- Skills -->
                <div>
                    <h3 class="text-lg font-medium">Skills</h3>
                    <input id="skills" type="text" placeholder="Skills (e.g., Python, JavaScript, SQL)" class="w-full p-2 border rounded mt-2">
                </div>
                <!-- Projects -->
                <div>
                    <h3 class="text-lg font-medium">Projects</h3>
                    <textarea id="projects" placeholder="Describe your projects (e.g., Built a web app using React)" class="w-full p-2 border rounded mt-2 h-24"></textarea>
                </div>
                <!-- Resume Type -->
                <div>
                    <h3 class="text-lg font-medium">Resume Purpose</h3>
                    <select id="resume-type" class="w-full p-2 border rounded mt-2">
                        <option value="job">Job Application</option>
                        <option value="internship">Internship</option>
                        <option value="hackathon">Hackathon</option>
                    </select>
                </div>
                <button onclick="generateResume()" class="bg-blue-500 text-white p-2 rounded hover:bg-blue-600">Generate Resume</button>
            </div>
        </div>
        <!-- Resume Preview -->
        <div id="resume-preview" class="bg-white shadow-md rounded-lg p-6 hidden">
            <h2 class="text-xl font-semibold mb-4">Your Resume</h2>
            <div id="resume-content"></div>
            <button onclick="downloadResume()" class="bg-green-500 text-white p-2 rounded hover:bg-green-600 mt-4">Download as Text</button>
        </div>
    </div>
    <script>
        function generateResume() {
            const name = document.getElementById('name').value || 'Your Name';
            const email = document.getElementById('email').value || 'email@example.com';
            const phone = document.getElementById('phone').value || '123-456-7890';
            const linkedin = document.getElementById('linkedin').value || '';
            const degree = document.getElementById('degree').value || 'Degree';
            const school = document.getElementById('school').value || 'School Name';
            const eduYear = document.getElementById('edu-year').value || 'Year';
            const experience = document.getElementById('experience').value || 'No experience provided';
            const skills = document.getElementById('skills').value || 'No skills provided';
            const projects = document.getElementById('projects').value || 'No projects provided';
            const resumeType = document.getElementById('resume-type').value;

            let resumeHtml = `
                <div class="text-center">
                    <h2 class="text-2xl font-bold">${name}</h2>
                    <p>${email} | ${phone}${linkedin ? ' | <a href="' + linkedin + '" class="text-blue-500">LinkedIn</a>' : ''}</p>
                </div>
                <hr class="my-4">
                <h3 class="text-lg font-semibold">Objective</h3>
                <p>Seeking a ${resumeType} opportunity to apply my skills in a dynamic environment.</p>
                <h3 class="text-lg font-semibold mt-4">Education</h3>
                <p><strong>${degree}</strong> - ${school}, ${eduYear}</p>
                <h3 class="text-lg font-semibold mt-4">Experience</h3>
                <p>${experience.replace(/\n/g, '<br>')}</p>
                <h3 class="text-lg font-semibold mt-4">Skills</h3>
                <p>${skills}</p>
                <h3 class="text-lg font-semibold mt-4">Projects</h3>
                <p>${projects.replace(/\n/g, '<br>')}</p>
            `;
            document.getElementById('resume-content').innerHTML = resumeHtml;
            document.getElementById('resume-preview').classList.remove('hidden');
        }

        function downloadResume() {
            const resumeContent = document.getElementById('resume-content').innerText;
            const blob = new Blob([resumeContent], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'resume.txt';
            a.click();
            URL.revokeObjectURL(url);
        }
    </script>
</body>
</html>