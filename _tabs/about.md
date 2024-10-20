---
# the default layout is 'page'
icon: fas fa-info-circle
order: 4
---

<!-- HTML -->
<div class="console">
  <header>
    <p>about@sahl</p>
  </header>
  <div class="consolebody" id="consoleBody">
    <p>> </p>
  </div>
</div>

<!-- CSS -->
<style>
  :root {
    --chirpy-bg-light: #f8f9fa; /* Light background color */
    --chirpy-bg-dark: #1a1a1a;  /* Dark background color */
    --chirpy-text-light: #000;   /* Light text color */
    --chirpy-text-dark: #63de00; /* Dark text color */
  }

  body {
    min-width: 100vw;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    background-color: var(--chirpy-bg-light);
    transition: background-color 0.3s;
    margin: 0;
    padding: 0 10px;
  }

  .console {
    font-family: 'Fira Mono', monospace;
    width: 100%;
    max-width: 700px;
    box-sizing: border-box;
    margin: auto;
    display: flex;
    flex-direction: column;
  }

  .console header {
    border-top-left-radius: 15px;
    border-top-right-radius: 15px;
    background-color: #555;
    height: 45px;
    line-height: 45px;
    text-align: center;
    color: #ddd;
  }

  .console .consolebody {
    border-bottom-left-radius: 15px;
    border-bottom-right-radius: 15px;
    box-sizing: border-box;
    padding: 20px;
    flex: 1;
    overflow-y: auto;
    background-color: #000;
    color: var(--chirpy-text-light);
    transition: color 0.3s;
  }

  .console .consolebody p {
    margin: 0;
    padding: 0;
    line-height: 1.5rem;
  }

  .big-text {
    font-size: 2.0em;
    font-weight: bold;
  }

  @keyframes irregularFlicker {
    0% { opacity: 1; }
    5% { opacity: 0.3; }
    10% { opacity: 0.7; }
    15% { opacity: 0.1; }
    25% { opacity: 0.8; }
    30% { opacity: 0.5; }
    40% { opacity: 1; }
    50% { opacity: 0.2; }
    60% { opacity: 0.9; }
    70% { opacity: 0.4; }
    80% { opacity: 1; }
    85% { opacity: 0.3; }
    90% { opacity: 0.6; }
    100% { opacity: 1; }
  }

  .consolebody a {
    color: var(--chirpy-text-light);
    text-decoration: none;
    animation: irregularFlicker 300ms infinite;
    transition: color 0.2s, text-shadow 0.2s;
  }

  .consolebody a:hover {
    color: #63de00;
    text-shadow: 0 0 10px #63de00, 0 0 20px #63de00;
  }

  .typing::after {
    content: '|';
    animation: blink 0.7s steps(2, end) infinite;
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  @media (prefers-color-scheme: dark) {
    body {
      background-color: var(--chirpy-bg-dark);
    }
    .console .consolebody {
      color: var(--chirpy-text-dark);
    }
    .consolebody a {
      color: var(--chirpy-text-dark);
    }
  }

  @media (prefers-color-scheme: light) {
    .console .consolebody {
      background-color: #fff;
      color: var(--chirpy-text-light);
    }
  }

  @media (max-width: 768px) {
    .console {
      width: 100%;
      height: auto;
    }
    .console .consolebody {
      padding: 10px;
    }
  }

  .secalin {
    font-size: 1.5em;
  }

  .secalin11 {
    font-size: 18px;
  }

  .secalin12 {
    font-size: 18px;
  }
</style>

{% raw %}
<!-- JavaScript -->
<script>
  const lines = [
    "> <span class='big-text'>Hi, I'm Sahl.</span>",
    "><span class='secalin'> Security researcher.</span>",
    "><span class='secalin12'> Currently upskilling at Brototype.</span>",
    "><span class='secalin12'> Passionate about exploring vulnerabilities and enhancing digital security!</span>"
  ];

  const options = [
    "> <span class='secalin11'>Click Below:</span>",
    "> <span class='secalin11'> <a href='/cv-download' target='_blank'>View CV</a></span>",
    "> <span class='secalin11'><a href='/categories/Blogs/'>Blogs</a></span>",
    "> <span class='secalin11'> <a href='/categories/certifications/'>Certifications</a></span>",
    "> <span class='secalin11'><a href='/categories/projects/'>Projects</a></span>",
    "> <span class='secalin11'><a href='/categories/Tools/'>Tools</a></span>",
    "> <span class='secalin11'><a href='https://www.linkedin.com/in/muhammed-sahl-473558231'>Contact me</a></span>"
  ];

  const consoleBody = document.getElementById('consoleBody');
  let lineIndex = 0;

  function scrollToBottom() {
    consoleBody.scrollTop = consoleBody.scrollHeight;
  }

  function showOptions() {
    options.forEach(option => {
      const p = document.createElement('p');
      p.innerHTML = option;
      consoleBody.appendChild(p);
      scrollToBottom();
    });
  }

  function typeLine() {
    if (lineIndex < lines.length) {
      const p = document.createElement('p');
      p.innerHTML = lines[lineIndex];
      consoleBody.appendChild(p);

      let charIndex = 0;
      const typeChar = () => {
        if (charIndex < lines[lineIndex].length) {
          const tempText = document.createElement('span');
          tempText.innerHTML = lines[lineIndex].substring(0, charIndex + 1);
          p.innerHTML = tempText.innerHTML;
          charIndex++;
          scrollToBottom();
          setTimeout(typeChar, 30);
        } else {
          lineIndex++;
          setTimeout(typeLine, 500);
        }
      };

      typeChar();
    } else {
      setTimeout(showOptions, 1000);
    }
  }

  const prefersDarkScheme = window.matchMedia("(prefers-color-scheme: dark)");
  prefersDarkScheme.addEventListener("change", (e) => {
    document.body.style.backgroundColor = e.matches
      ? "var(--chirpy-bg-dark)"
      : "var(--chirpy-bg-light)";
  });

  window.onload = typeLine;
</script>
{% endraw %}




<br><br><br>
Hi, I'm Sahl, a BCA graduate currently upskilling at Brototype. I have a passion for exploring vulnerabilities and enhancing digital security. My journey in technology is fueled by a deep curiosity and an unwavering desire to learn and adapt in the ever-evolving landscape of cybersecurity.

I believe that the world of technology is a dynamic realm where challenges constantly arise, and I am committed to staying at the forefront of these changes. My dedication to understanding the intricacies of cybersecurity drives me to dive into complex problems, analyze potential risks, and develop innovative solutions that can truly make a difference.

I am excited about the opportunity to contribute to a safer digital environment and continually improve my skills as I navigate this fascinating field. Each day presents a new opportunity for growth, and I embrace the challenge of learning something new, whether it's through hands-on projects, collaborative teamwork, or exploring the latest trends in technology.
