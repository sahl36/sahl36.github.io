---
# the default layout is 'page'
icon: fas fa-info-circle
order: 4
---


<br><br>
Hi, I'm Sahl, a BCA graduate currently upskilling at Brototype. I have a passion for exploring vulnerabilities and enhancing digital security. My journey in technology is fueled by a deep curiosity and an unwavering desire to learn and adapt in the ever-evolving landscape of cybersecurity.

I believe that the world of technology is a dynamic realm where challenges constantly arise, and I am committed to staying at the forefront of these changes. My dedication to understanding the intricacies of cybersecurity drives me to dive into complex problems, analyze potential risks, and develop innovative solutions that can truly make a difference.

I am excited about the opportunity to contribute to a safer digital environment and continually improve my skills as I navigate this fascinating field. Each day presents a new opportunity for growth, and I embrace the challenge of learning something new, whether it's through hands-on projects, collaborative teamwork, or exploring the latest trends in technology.
<br><br>

<!-- HTML -->
<div class="console">
  <header>
    <p>Contact Me</p>
  </header>
  <div class="consolebody" id="consoleBody">
    <form id="contactForm" action="https://formcarry.com/s/jGB4SyAVr5j" method="POST">
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" placeholder="Enter your name" required />

      <label for="email">Email:</label>
      <input type="email" id="email" name="email" placeholder="Enter your email" required />

      <label for="message">Message:</label>
      <textarea id="message" name="message" rows="5" placeholder="Write your message..." required></textarea>

      <button type="submit">Send</button>
    </form>
  </div>
</div>


<!-- CSS -->
<style>
  :root {
    --chirpy-bg-light: #f8f9fa;
    --chirpy-bg-dark: #1a1a1a;
    --chirpy-text-light: #000;
    --chirpy-text-dark: #63de00;
  }

  body {
    min-width: 100vw;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: var(--chirpy-bg-light);
    transition: background-color 0.3s;
    margin: 0;
    padding: 0 10px;
  }

  .console {
    font-family: 'Fira Mono', monospace;
    width: 100%;
    max-width: 700px;
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

  .consolebody {
    border-bottom-left-radius: 15px;
    border-bottom-right-radius: 15px;
    padding: 20px;
    background-color: #000;
    color: var(--chirpy-text-light);
    transition: color 0.3s;
  }

  form {
    display: flex;
    flex-direction: column;
    gap: 15px;
  }

  input, textarea, button {
    font-family: 'Fira Mono', monospace;
    width: 100%;
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #ddd;
    background-color: #fff;
    transition: background-color 0.3s, border-color 0.3s;
  }

  input:focus, textarea:focus {
    border-color: #63de00;
    outline: none;
  }

  button {
    background-color: #63de00;
    color: #000;
    cursor: pointer;
    font-weight: bold;
    border: none;
    transition: background-color 0.3s;
  }

  button:hover {
    background-color: #4cad00;
  }

  @media (prefers-color-scheme: dark) {
    body {
      background-color: var(--chirpy-bg-dark);
    }
    .consolebody {
      background-color: #111;
      color: var(--chirpy-text-dark);
    }
    input, textarea {
      background-color: #222;
      color: #ddd;
      border: 1px solid #444;
    }
  }

  @media (max-width: 768px) {
    .console {
      width: 100%;
      height: auto;
    }
  }
</style>
<!-- JavaScript -->
<script>
  const contactForm = document.getElementById('contactForm');

  contactForm.addEventListener('submit', (event) => {
    event.preventDefault(); // Prevent form from refreshing the page
    const formData = new FormData(contactForm);

    fetch(contactForm.action, {
      method: 'POST',
      body: formData,
      headers: {
        'Accept': 'application/json'
      }
    })
    .then(response => {
      if (response.ok) {
        alert('Thank you! Your message has sent');
        contactForm.reset(); // Clear the form
        // Optionally redirect to a thank you page
        // window.location.href = 'https://yourwebsite.com/thank-you';
      } else {
        alert('There was an error sending your message. Please try again.');
      }
    })
    .catch(error => {
      alert('There was an error sending your message. Please try again.');
    });
  });
</script>

