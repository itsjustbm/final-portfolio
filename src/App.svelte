<script>
  import { onMount } from "svelte";

  let sections = ["About", "Interests", "Projects", "Technologies", "Contact"];
  let showSuccessMessage = false;

  const handleSubmit = (event) => {
    event.preventDefault(); // Prevent default form submission
    showSuccessMessage = true;
    setTimeout(() => showSuccessMessage = false, 5000); // Hide message after 5 seconds
    event.target.reset(); // Reset the form fields
  };

  onMount(() => {
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function (e) {
        e.preventDefault();
        document.querySelector(this.getAttribute('href')).scrollIntoView({
          behavior: 'smooth'
        });
      });
    });
  });
</script>

<main>
  <header>
    <nav>
      <ul>
        {#each sections as section}
          <li><a href={`#${section.toLowerCase()}`}>{section}</a></li>
        {/each}
      </ul>
    </nav>
  </header>

  <section id="about" class="about-section">
    <h1>About Me</h1>
    <div class="profile">
      <img src="IMG_0719.JPG" alt="2024" class="profile-image" />
      <p>Hello! I am a passionate web developer who loves creating visually appealing and functional applications. Welcome to my portfolio!</p>
    </div>
  </section>

  <section id="interests" class="interests-section">
    <h1>Interests</h1>
    <p>I enjoy coding, exploring new technologies, and solving challenging problems. In my free time, I love hiking, photography, playing video games and soccer.</p>
  </section>

  <section id="projects" class="projects-section">
    <h1>Projects</h1>
    <p>Here are some of the projects I've worked on:</p>
    <ul>
      <li><strong>Portfolio Website:</strong> A personal website showcasing my work and skills.</li>
      <li><strong>Engineering design:</strong> Designed bridges and learned the foundation building a bridge</li>

      <li><strong>Circuit Design:</strong> Designed and bulit electrical circuit using Arduino</li>
    </ul>
  </section>

  <section id="technologies" class="technologies-section">
    <h1>Technologies</h1>
    <p>Proficient in:</p>
    <ul class="tech-list">
      <li>HTML5</li>
      <li>CSS3</li>
      <li>JavaScript</li>
      <li>Svelte</li>
      <li>Node.js</li>
    </ul>
  </section>

  <section id="contact" class="contact-section">
    <h1>Contact Me</h1>
    {#if showSuccessMessage}
      <p class="success-message">Your message has been sent successfully!</p>
    {/if}
    <form id="contact-form" on:submit={handleSubmit}>
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" required />

      <label for="email">Email:</label>
      <input type="email" id="email" name="email" required />

      <label for="message">Message:</label>
      <textarea id="message" name="message" rows="5" required></textarea>

      <button type="submit">Submit</button>
    </form>
  </section>
</main>

<style>
  :global(body) {
    font-family: 'Arial', sans-serif;
    margin: 0;
    padding: 0;
    line-height: 1.6;
    color: #040404;
    background: linear-gradient(135deg, #a4508b, #5f0a87);
    background-attachment: fixed;
    background-size: cover;
  }

  header {
    position: fixed;
    top: 0;
    width: 100%;
    background: linear-gradient(to right, #6a11cb, #2575fc);
    color: white;
    padding: 15px 0;
    z-index: 1000;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  }

  header nav ul {
    display: flex;
    list-style: none;
    justify-content: center;
    padding: 0;
    margin: 0;
  }

  header nav ul li a {
    color: white;
    text-decoration: none;
    padding: 10px 20px;
    font-weight: bold;
    border-radius: 5px;
    transition: background-color 0.3s ease;
  }

  header nav ul li a:hover {
    background-color: rgba(255, 255, 255, 0.2);
  }

  section {
    margin-top: 100px;
    padding: 40px;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    background: white;
    margin: 20px;
  }

  .about-section {
    text-align: center;
  }

  .profile {
    display: flex;
    align-items: center;
    flex-direction: column;
    gap: 20px;
  } 

  .profile-image {
    width: 150px;
    height: 190px;
    border-radius: 50%;
    object-fit: cover;
    border: 3px solid #6a11cb;
  }

  .interests-section, .projects-section, .technologies-section, .contact-section {
    max-width: 800px;
    margin: auto;
    background-color: #6a11cb;
    
  }

  .projects-section ul {
    padding: 0;
    list-style: none;
  }

  .projects-section ul li {
    margin: 10px 0;
  }

  .tech-list {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    padding: 0;
    list-style: none;
  }

  .tech-list li {
    background: #0c0c0c;
    color: rgb(93, 11, 125);
    padding: 5px 10px;
    border-radius: 5px;
  }

  form {
    display: flex;
    flex-direction: column;
    gap: 15px;
  }

  input, textarea {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  color: #0a0a0a; /* Set text color to a visible dark shade */
  background: #ffffff;
}


  button {
    padding: 10px;
    background-color: #e7e6e9;
    color: rgb(120, 11, 170);
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  button:hover {
    background-color: #09090a;
  }

  .success-message {
    color: #0d0f0e;
    font-weight: bold;
    text-align: center;
    margin-bottom: 15px;
    padding: 5px 10px;
    border-radius: 5px;
  }
</style>
