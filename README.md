<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Single Page Application - Phase 5 Project</title>
  <style>
    /* Basic Page Style */
    body {
      font-family: "Poppins", Arial, sans-serif;
      margin: 0;
      background-color: #f5f6fa;
      color: #333;
    }

    header {
      background-color: #4f46e5;
      color: white;
      padding: 20px;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 28px;
    }

    nav {
      display: flex;
      justify-content: center;
      background-color: #4338ca;
      gap: 20px;
      padding: 10px 0;
    }

    nav a {
      color: white;
      text-decoration: none;
      font-weight: bold;
      padding: 8px 16px;
      border-radius: 6px;
      transition: 0.3s;
    }

    nav a:hover, nav a.active {
      background-color: #6366f1;
    }

    #content {
      padding: 40px;
      text-align: left;
      line-height: 1.6;
      animation: fadeIn 0.5s ease-in;
      background-color: white;
      max-width: 900px;
      margin: 30px auto;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    h2 {
      color: #4f46e5;
      border-bottom: 2px solid #4f46e5;
      display: inline-block;
      margin-bottom: 10px;
    }

    footer {
      text-align: center;
      background-color: #4f46e5;
      color: white;
      padding: 10px;
      position: fixed;
      bottom: 0;
      width: 100%;
    }

    @keyframes fadeIn {
      from {opacity: 0; transform: translateY(10px);}
      to {opacity: 1; transform: translateY(0);}
    }

    ul {
      list-style-type: square;
      margin-left: 20px;
    }

    .screenshot {
      width: 100%;
      border-radius: 10px;
      margin-top: 15px;
      border: 1px solid #ccc;
    }

  </style>
</head>
<body>

  <header>
    <h1>Single Page Application — Phase 5 Project</h1>
    <p>Project Demonstration & Documentation</p>
  </header>

  <nav>
    <a href="#demo" onclick="navigate('demo')">Final Demo Walkthrough</a>
    <a href="#report" onclick="navigate('report')">Project Report</a>
    <a href="#screenshots" onclick="navigate('screenshots')">Screenshots / API Docs</a>
    <a href="#challenges" onclick="navigate('challenges')">Challenges & Solutions</a>
    <a href="#readme" onclick="navigate('readme')">GitHub README & Setup</a>
    <a href="#submission" onclick="navigate('submission')">Final Submission</a>
  </nav>

  <div id="content">
    <!-- Dynamic content appears here -->
  </div>

  <footer>
    <p>&copy; 2025 Student Project | Single Page Application (SPA)</p>
  </footer>

  <script>
    // Page data (all sections)
    const pages = {
      demo: `
        <h2>Final Demo Walkthrough</h2>
        <p>This Single Page Application (SPA) demonstrates how a web app can load different sections without reloading the browser. The demo includes navigation, smooth transitions, and clean layout.</p>
        <ul>
          <li><b>Home Page:</b> Displays introduction of project.</li>
          <li><b>Feature Pages:</b> Each menu link loads content dynamically using JavaScript.</li>
          <li><b>Purpose:</b> To show how client-side rendering works.</li>
        </ul>
        <p>All components are designed using HTML, CSS, and vanilla JavaScript.</p>
      `,
      report: `
        <h2>Project Report</h2>
        <p>The Single Page Application is built to demonstrate front-end routing and modular design. It is implemented using HTML, CSS, and JavaScript. Below are the key highlights:</p>
        <ul>
          <li>Responsive design using CSS Flexbox</li>
          <li>Dynamic routing using JavaScript</li>
          <li>Simple navigation without page reloads</li>
          <li>Easy to integrate with backend APIs</li>
        </ul>
        <p>This project follows the Agile method of development: design → build → test → document.</p>
      `,
      screenshots: `
        <h2>Screenshots / API Documentation</h2>
        <p>Below are sample screenshots of the running application and example API documentation.</p>
        <img src="https://via.placeholder.com/800x400?text=Screenshot+1" class="screenshot" alt="Screenshot 1">
        <img src="https://via.placeholder.com/800x400?text=Screenshot+2" class="screenshot" alt="Screenshot 2">
        <h3>API Documentation (Example)</h3>
        <pre>
GET /api/students
→ Returns list of all students

POST /api/attendance
→ Marks attendance for selected student

Response Format:
{
  "id": 1,
  "name": "Ravi Kumar",
  "status": "Present"
}
        </pre>
      `,
      challenges: `
        <h2>Challenges & Solutions</h2>
        <ul>
          <li><b>Challenge:</b> Page reloading when clicking links.<br>
              <b>Solution:</b> Used JavaScript event handlers to dynamically update content.</li>
          <li><b>Challenge:</b> Responsive layout for all screens.<br>
              <b>Solution:</b> Used Flexbox and CSS media queries.</li>
          <li><b>Challenge:</b> Managing multiple sections in one file.<br>
              <b>Solution:</b> Stored all content in a JavaScript object for easy navigation.</li>
        </ul>
      `,
      readme: `
        <h2>GitHub README & Setup Guide</h2>
        <p>To run this project locally:</p>
        <pre>
# Clone the repository
git clone https://github.com/yourusername/spa-project.git

# Open in VS Code
cd spa-project

# Run the project
Open index.html in your browser
        </pre>
        <p>📄 <b>README.md includes:</b></p>
        <ul>
          <li>Project Overview</li>
          <li>Installation Steps</li>
          <li>Features</li>
          <li>Technology Stack</li>
          <li>Contact Details</li>
        </ul>
      `,
      submission: `
        <h2>Final Submission</h2>
        <p>The final submission includes the following files and reports:</p>
        <ul>
          <li>✅ <b>Source Code:</b> index.html, style.css, script.js</li>
          <li>✅ <b>Documentation:</b> Project report (PDF)</li>
          <li>✅ <b>Demo Video:</b> Hosted on Google Drive / YouTube</li>
          <li>✅ <b>GitHub Link:</b> <a href="https://github.com/yourusername/spa-project" target="_blank">View Repository</a></li>
        </ul>
        <p>Thank you for reviewing this project submission!</p>
      `
    };

    // Navigation function
    function navigate(page) {
      const content = document.getElementById("content");
      content.innerHTML = pages[page] || "<h2>Page Not Found</h2><p>The selected section does not exist.</p>";

      // highlight active nav link
      document.querySelectorAll("nav a").forEach(a => a.classList.remove("active"));
      const activeLink = document.querySelector(`nav a[href="#${page}"]`);
      if (activeLink) activeLink.classList.add("active");

      window.location.hash = page;
    }

    // Load page from hash or default
    window.onload = () => {
      const hash = window.location.hash.replace("#", "");
      navigate(hash || "demo");
    };
  </script>

</body>
</html>
