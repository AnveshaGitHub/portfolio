document.addEventListener('DOMContentLoaded', () => {
    const navButtons = document.querySelectorAll('.nav-button');
    const contentSections = document.querySelectorAll('.content-section');
    const fab = document.getElementById('fab');
    const body = document.body;
    const homeBackgroundId = 'home-background'; // ID used for background styling

    // Function to switch tabs
    function switchTab(targetId) {
        // Hide all sections
        contentSections.forEach(section => {
            section.classList.remove('active');
        });

        // Deactivate all nav buttons
        navButtons.forEach(button => {
            button.classList.remove('active-tab');
        });

        // Activate the target section and button
        const targetSection = document.getElementById(targetId);
        const targetButton = document.querySelector(`.nav-button[data-target="${targetId}"]`);

        if (targetSection) {
            targetSection.classList.add('active');

             // --- Skill Bar Animation Trigger ---
             // Animate skill bars only when the 'about' section becomes active
             if (targetId === 'about') {
                 const skillBars = targetSection.querySelectorAll('.skill-bar');
                 skillBars.forEach(bar => {
                     const targetWidth = bar.style.width; // Get width from inline style
                     // Set custom property for CSS animation
                     bar.style.setProperty('--target-width', targetWidth);
                     // Temporarily reset width to 0 to replay animation if needed (optional)
                     // bar.style.width = '0%';
                     // void bar.offsetWidth; // Trigger reflow
                     // bar.style.width = targetWidth; // Set it back - relies more on CSS animation keyframes now
                 });
             }

        }
        if (targetButton) {
            targetButton.classList.add('active-tab');
        }

        // Optional: Remove background image class from body if not on 'home'
        // If your 'About' section IS the home/initial view, you might keep the bg
        // Or fade it out / change it based on the section.
        // Example: If 'about' is the effective home page view:
         if (targetId !== 'about') { // Or whatever your initial page is
             // body.classList.remove(homeBackgroundId); // If you want to remove the BG
             // body.style.backgroundImage = 'none'; // Alternative
         } else {
             // body.classList.add(homeBackgroundId); // Add it back if needed
             // body.style.backgroundImage = "url('images/anvesha-bg.jpg')"; // Ensure it's set
         }
         // For simplicity, the current CSS keeps the body background fixed,
         // and opaque sections cover it. No JS needed for this part with current CSS.

        // Scroll to top of content area when switching tabs
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    // Add click listeners to navigation buttons
    navButtons.forEach(button => {
        button.addEventListener('click', () => {
            const targetId = button.getAttribute('data-target');
            switchTab(targetId);
        });
    });

    // Add click listener to FAB (Floating Action Button)
    if (fab) {
        fab.addEventListener('click', () => {
            // Make the FAB switch to the Contact tab
            switchTab('contact');
            // Optional: Smooth scroll specifically to the contact section if needed
            // document.getElementById('contact').scrollIntoView({ behavior: 'smooth' });
        });
    }

    // Initialize the page: Show the 'About' section by default
    // The 'active' class is already set in HTML, so no extra JS needed for initial load
    // Trigger initial skill bar animation if 'about' is the default active section
    if (document.getElementById('about').classList.contains('active')) {
        const initialSkillBars = document.querySelectorAll('#about .skill-bar');
        initialSkillBars.forEach(bar => {
             const targetWidth = bar.style.width;
             bar.style.setProperty('--target-width', targetWidth);
        });
    }

    // Handle Contact Form Submission (Demo)
    const contactForm = document.getElementById('contact-form');
    if(contactForm) {
        contactForm.addEventListener('submit', (e) => {
            e.preventDefault(); // Prevent actual form submission
            alert('Thank you for your message! (Frontend demo - data not sent)');
            // Optionally clear the form
             contactForm.reset();
        });
    }

});