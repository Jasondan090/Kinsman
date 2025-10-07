
document.addEventListener('DOMContentLoaded', () => {
    console.log('Welcome to Kinsman De Tailors!');
    
    const addVideoButton = document.getElementById('addVideoButton');
    addVideoButton.addEventListener('click', addVideoToGallery);
    
    const adminPanel = document.getElementById('admin');
    const password = "Jasondan090"; // Admin password
    const userPassword = prompt("Enter admin password:");

    if (userPassword !== password) {
        adminPanel.classList.add('hidden'); // Hide admin panel if password is incorrect
        alert("Incorrect password! Admin panel hidden.");
    }
});

function addVideoToGallery() {
    const videoUrl = document.getElementById('videoUrl').value;
    const videoGallery = document.getElementById('video-gallery');

    if (videoUrl) {
        // Create a new iframe element to display the video
        const videoIframe = document.createElement('iframe');
        videoIframe.src = videoUrl.includes('youtube.com') ? 
            videoUrl.replace("watch?v=", "embed/") : videoUrl; // Correctly format YouTube URLs
        videoIframe.allow = 'autoplay; encrypted-media';
        videoIframe.setAttribute('frameborder', '0');
        videoIframe.setAttribute('allowfullscreen', '');
        
        // Append the video to the gallery
        videoGallery.appendChild(videoIframe);
        
        // Clear the input field
        document.getElementById('videoUrl').value = ''; 
    } else {
        alert('Please enter a valid video URL.');
    }
}
