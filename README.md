# Allin-one-ai-<!DOCTYPE html>

<html lang="hi">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>My AI Studio</title>

<style>

*{box-sizing:border-box}

body{margin:0;background:#10101c;color:#fff;font-family:Arial,sans-serif}

header{padding:24px 18px;background:linear-gradient(135deg,#632bdb,#172b70)}

h1{margin:0 0 8px;font-size:27px}

p{line-height:1.5;color:#d7d8ed}

main{padding:16px;max-width:700px;margin:auto}

.panel{background:#1c1c2d;padding:16px;border-radius:16px;margin:14px 0}

h2{font-size:19px;margin-top:0}

button,.link{display:block;width:100%;padding:13px;margin-top:10px;

border:0;border-radius:10px;background:#7654f6;color:white;

font-size:15px;text-align:center;text-decoration:none;cursor:pointer}

.secondary{background:#303047}

input,textarea{width:100%;padding:12px;border-radius:9px;

border:1px solid #51516b;background:#121222;color:white;margin:7px 0}

textarea{min-height:100px;resize:vertical}

img{max-width:100%;border-radius:12px;margin-top:10px}

.small{font-size:13px;color:#b8b9d3}

</style>

</head>

<body>

<header>

<h1>✨ My AI Studio</h1>

<p>AI फोटो और वीडियो टूल्स — एक ही जगह</p>

</header>

<main>

<div class="panel">

<h2>📸 1. अपनी फोटो चुनो</h2>

<input type="file" id="photo" accept="image/*">

<img id="preview" alt="तुम्हारी चुनी हुई फोटो का प्रीव्यू" hidden>

<p class="small">फोटो का प्रीव्यू इसी पेज पर दिखेगा।</p>

</div>

<div class="panel">

<h2>🎨 2. AI फोटो प्रॉम्प्ट</h2>

<textarea id="prompt" placeholder="लिखो: मेरी फोटो का चेहरा वही रखकर cinematic photoshoot बनाओ..."></textarea>

<button onclick="makePrompt()">✨ प्रॉम्प्ट बेहतर करो</button>

<button class="secondary" onclick="copyPrompt()">📋 प्रॉम्प्ट कॉपी करो</button>

<p class="small" id="status">पहले अपना प्रॉम्प्ट लिखो।</p>

<a class="link" target="_blank" rel="noopener"

href="https://huggingface.co/spaces?search=text-to-image">

🖼️ AI इमेज टूल्स खोलो

</a>

</div>

<div class="panel">

<h2>🎬 3. AI वीडियो टूल्स</h2>

<a class="link" target="_blank" rel="noopener"

href="https://huggingface.co/spaces?search=image-to-video">

फोटो से वीडियो बनाने वाले टूल्स

</a>

<a class="link" target="_blank" rel="noopener"

href="https://huggingface.co/spaces?search=text-to-video">

टेक्स्ट से वीडियो बनाने वाले टूल्स

</a>

<a class="link" target="_blank" rel="noopener"

href="https://huggingface.co/spaces?search=background-removal">

फोटो का बैकग्राउंड हटाने वाले टूल्स

</a>

</div>

<div class="panel">

<h2>💡 4. फोटोशूट प्रॉम्प्ट</h2>

<button onclick="preset('cinematic')">Cinematic Photoshoot</button>

<button onclick="preset('fashion')">Fashion Photoshoot</button>

<button onclick="preset('video')">Slow Motion Video</button>

</div>

<p class="small">ध्यान दें: ये लिंक उपलब्ध टूल्स खोजते हैं। हर टूल मुफ्त या हमेशा उपलब्ध हो, इसकी गारंटी नहीं है।</p>

</main>

<script>

const photo=document.getElementById('photo');

const preview=document.getElementById('preview');

photo.addEventListener('change',()=>{

 const file=photo.files[0];

 if(!file)return;

 if(!file.type.startsWith('image/')){

  alert('कृपया फोटो फ़ाइल चुनें।');return;

 }

 preview.src=URL.createObjectURL(file);

 preview.hidden=false;

});

function preset(type){

 const prompts={

 cinematic:'Create a realistic cinematic photoshoot from my reference photo. Preserve the same face, identity, skin tone and natural features. Professional lighting, realistic details, natural pose.',

 fashion:'Create a premium fashion photoshoot from my reference photo. Preserve the exact identity, face, hairstyle and skin tone. Stylish composition, realistic lighting and natural anatomy.',

 video:'Create a cinematic image-to-video scene using my reference photo. Keep the same identity and outfit. Add gentle hair movement, a natural smile and a slow smooth camera zoom.'

 };

 document.getElementById('prompt').value=prompts[type];

 document.getElementById('status').textContent='प्रॉम्प्ट तैयार है। अब कॉपी करो।';

}

function makePrompt(){

 const box=document.getElementById('prompt');

 if(!box.value.trim()){

  box.value='Create an ultra-realistic cinematic photoshoot from my reference photo. Preserve the same identity, face and skin tone. Use natural lighting and realistic details.';

 }else{

  box.value=box.value.trim()+' Preserve identity and facial features. Use realistic details, natural lighting and high-quality composition.';

 }

 document.getElementById('status').textContent='प्रॉम्प्ट तैयार है।';

}

async function copyPrompt(){

 const box=document.getElementById('prompt');

 if(!box.value.trim()){

  document.getElementById('status').textContent='पहले प्रॉम्प्ट लिखो या कोई स्टाइल चुनो।';

  return;

 }

 try{

  await navigator.clipboard.writeText(box.value);

  document.getElementById('status').textContent='प्रॉम्प्ट कॉपी हो गया!';

 }catch(e){

  box.select();

  document.getElementById('status').textContent='टेक्स्ट चुना गया है। Copy दबाओ।';

 }

}

</script>

</body>

</html>
