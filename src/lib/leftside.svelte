<script>
    export let selectedFile; // To receive the selected file from the parent
    export let showUploadPage; // To receive the flag to show the upload section
  
    // Function to reset to the search page
    const resetToSearch = () => {
      // Emit an event to reset the search state in the parent
      const event = new CustomEvent('resetSearch');
      dispatchEvent(event);
    };
  </script>
  
  <style>
    .left-side { 
        flex: 3; /* Takes 3 parts of the flex container, equivalent to 75% */
        height: 100vh;
        background-color: #f4f4f4; /* Light gray background */
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column; /* Stack items vertically */
        padding: 20px;
        box-sizing: border-box;
    }
  
    .upload-section {
      display: flex; /* Flexbox for side-by-side layout */
      justify-content: space-between;
      align-items: flex-start; /* Align items at the top */
      margin-top: 20px; /* Space above the section */
      width: 100%; /* Full width */
      max-width: 800px; /* Limit maximum width */
    }
  
    .image-container {
      display: flex;
      flex-direction: column;
      align-items: center; /* Center the image and text */
      margin-top: 20px; /* Space above the image */
      padding: 20px; /* Space around the image */
      border: 1px solid #ccc; /* Optional: border around the image container */
      border-radius: 10px; /* Rounded corners */
      background-color: #f9f9f9; /* Light background color */
      max-width: 90%; /* Maximum width for the image container */
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); /* Subtle shadow */
    }
  
    img {
      max-width: 100%;
      height: auto;
      border: 2px solid #ccc;
      border-radius: 5px;
      margin-top: 20px;
    }
  
    .form-container {
      display: flex;
      flex-direction: column;
      max-width: 45%; /* Maximum width for the form container */
      width: 100%; /* Full width */
    }
  
    input[type="text"] {
      width: 300px;
      padding: 10px;
      font-size: 16px;
      border: 2px solid #ccc;
      border-radius: 5px;
      margin-bottom: 20px;
    }
  
    button {
      padding: 10px 20px;
      font-size: 16px;
      border: none;
      border-radius: 5px;
      background-color: #007bff;
      color: white;
      cursor: pointer;
    }
  
    button:hover {
      background-color: #0056b3;
    }
  </style>
  
  <div class="left-side">
    {#if showUploadPage}
      <!-- Upload Display Section -->
      <div class="upload-section">
        <!-- Image display -->
        <div class="image-container">
          <img src={URL.createObjectURL(selectedFile)} alt="Uploaded Image" />
        </div>
        <!-- Additional Form for Image Data -->
        <div class="form-container">
          <h3>Image Details</h3>
          <input type="text" placeholder="Enter additional data..." />
          <button on:click={resetToSearch}>Back to Search</button>
        </div>
      </div>
    {/if}
  </div>
  