- 👋 Hi, I’m @arpitsharma522
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Arpit Sharma</title>
  <script type="module">
    // Import Firebase SDK
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.1/firebase-app.js";
    import { getStorage, ref, uploadBytes, getDownloadURL } from "https://www.gstatic.com/firebasejs/10.8.1/firebase-storage.js";
    import { getFirestore, collection, addDoc } from "https://www.gstatic.com/firebasejs/10.8.1/firebase-firestore.js";const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};

const app = initializeApp(firebaseConfig);
const storage = getStorage(app);
const db = getFirestore(app);

window.saveData = async () => {
  const name = document.getElementById('name').value;
  const bio = document.getElementById('bio').value;
  const fileInput = document.getElementById('file');

  if (fileInput.files.length > 0) {
    const file = fileInput.files[0];
    const storageRef = ref(storage, 'photos/' + file.name);
    await uploadBytes(storageRef, file);
    const photoURL = await getDownloadURL(storageRef);

    await addDoc(collection(db, "users"), {
      name: name,
      bio: bio,
      photo: photoURL,
      timestamp: new Date()
    });

    alert("Data saved successfully!");
  } else {
    alert("Please select a photo.");
  }
};

window.loadFile = (event) => {
  const output = document.getElementById('output');
  output.src = URL.createObjectURL(event.target.files[0]);
  output.style.display = 'block';
}

  </script>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to right, #232526, #414345);
      color: #fff;
      text-align: center;
      padding: 50px;
    }
    .card {
      background-color: #2c2f33;
      border-radius: 20px;
      padding: 30px;
      max-width: 400px;
      margin: auto;
      box-shadow: 0 8px 16px rgba(0,0,0,0.3);
    }
    img {
      width: 150px;
      height: 150px;
      object-fit: cover;
      border-radius: 50%;
      border: 4px solid #fff;
    }
    input, textarea {
      margin: 10px 0;
      padding: 10px;
      width: 100%;
      border-radius: 8px;
      border: none;
    }
    button {
      padding: 10px 20px;
      border: none;
      background-color: #7289da;
      color: white;
      border-radius: 10px;
      cursor: pointer;
    }
    button:hover {
      background-color: #5b6eae;
    }
  </style>
</head>
<body>
  <div class="card">
    <h2>Arpit Sharma - Personal Profile</h2>
    <input type="file" id="file" accept="image/*" onchange="loadFile(event)" />
    <img id="output" src="" alt="Your photo" style="display:none; margin-top: 20px;" />
    <input type="text" id="name" placeholder="Your Name" />
    <textarea id="bio" rows="4" placeholder="About You"></textarea>
    <button onclick="saveData()">Save</button>
  </div>
</body>
</html>---
arpitsharma522/arpitsharma522 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
