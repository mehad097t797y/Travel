<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>Travel Planner</title>
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:Arial,sans-serif;background:#f2f6ff;min-height:100vh;color:#222}
.home,.plans-page,.memory-page,.profile-page,.admin-page{width:calc(100% - 30px);max-width:650px;margin:20px auto;padding-bottom:30px}
.profile-box,.welcome,.destination-header,.plan-card,.memory-card,.photo-card,.admin-box{
background:#fff;border-radius:22px;padding:22px;margin-bottom:16px;box-shadow:0 7px 22px rgba(0,0,0,.08)
}
.profile-box{text-align:center;margin-top:30px}.logo{font-size:60px;margin-bottom:10px}
h1{font-size:28px;margin-bottom:10px}.subtitle{color:#777;margin-bottom:25px;line-height:1.5}
.profile-pic{width:110px;height:110px;border-radius:50%;background:#e8efff;margin:0 auto 20px;display:flex;justify-content:center;align-items:center;font-size:50px;overflow:hidden}
.profile-pic img,.user-photo{object-fit:cover}.user-photo{width:85px;height:85px;border-radius:50%;margin-bottom:10px}
.avatar{font-size:55px;margin-bottom:10px}.upload-btn,.small-btn{display:inline-block;background:#eef3ff;color:#315efb;padding:12px 18px;border-radius:12px;cursor:pointer;font-weight:bold;border:0}
#photo{display:none}.input-group{text-align:left;margin-bottom:18px}
label{display:block;margin-bottom:8px;font-weight:bold}
input,textarea,select{width:100%;padding:14px;border:1px solid #ddd;border-radius:12px;font-size:16px;outline:none}
textarea{min-height:100px;resize:vertical}
.create-btn,.plan-btn,.primary-btn{width:100%;border:0;background:#315efb;color:#fff;padding:15px;border-radius:12px;font-size:17px;font-weight:bold;cursor:pointer}
.place,.menu-btn{width:100%;border:0;background:#fff;padding:20px;margin-bottom:12px;border-radius:17px;text-align:left;font-size:18px;font-weight:bold;box-shadow:0 6px 20px rgba(0,0,0,.07);cursor:pointer}
.back-btn{border:0;background:#fff;padding:12px 18px;border-radius:12px;font-size:16px;margin-bottom:15px;box-shadow:0 4px 15px rgba(0,0,0,.08);cursor:pointer}
.big-icon{font-size:65px}.destination-header{text-align:center}.destination-header p,.welcome p{color:#777;line-height:1.5}
.plan-info{color:#666;line-height:1.8;margin-bottom:15px}.selected-count{text-align:center;color:#555;font-size:15px;font-weight:bold;margin-top:12px}
.loading{text-align:center;color:#777;padding:15px}.status-box{text-align:center;padding:14px;border-radius:15px;margin-bottom:15px;font-weight:bold;background:#eef3ff}
.status-success{background:#e5f8e9;color:#16833b}.status-cancel{background:#ffe8e8;color:#c62828}
.memory-card{cursor:pointer}.memory-card h2{margin-bottom:8px}.memory-card p{color:#777;line-height:1.6}
.photo-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}.photo-card{padding:10px}.photo-card img{width:100%;border-radius:12px}
.photo-card small{display:block;color:#777;margin-top:7px}.delete-btn{width:100%;border:0;background:#e53935;color:#fff;padding:9px;border-radius:9px;margin-top:8px;cursor:pointer}
.admin-btn{border:0;background:#222;color:#fff;padding:10px 14px;border-radius:10px;cursor:pointer;margin:4px}
.admin-btn.red{background:#e53935}.admin-btn.blue{background:#315efb}.admin-btn.green{background:#16833b}
.quote{text-align:center;font-style:italic;color:#777;line-height:1.7;padding:20px}
hr{border:0;border-top:1px solid #eee;margin:18px 0}
.row{display:flex;gap:8px;flex-wrap:wrap}.row>*{flex:1;min-width:120px}
.admin-item{background:#f7f9ff;border-radius:15px;padding:15px;margin:10px 0}
.admin-item h3{margin-bottom:8px}.tiny{font-size:13px;color:#777;line-height:1.5}
table{width:100%;border-collapse:collapse;font-size:14px}th,td{padding:9px;border-bottom:1px solid #eee;text-align:left;vertical-align:top}
</style>
</head>
<body>

<div class="profile-box" id="profilePage">
<div class="logo">🌍</div><h1>তোমার প্রোফাইল তৈরি করো</h1>
<p class="subtitle">ভ্রমণ শুরু করার আগে তোমার সম্পর্কে একটু জানি! 😊</p>
<div class="profile-pic" id="profilePreview">👤</div>
<label class="upload-btn">📷 Profile Picture<input type="file" id="photo" accept="image/*"></label>
<div class="input-group"><label>তোমার নাম</label><input id="name" placeholder="যেমন: Rahim"></div>
<div class="input-group"><label>তোমার বয়স</label><input id="age" type="number" placeholder="যেমন: 17"></div>
<button class="create-btn" id="createProfileBtn">🚀 Create Profile</button>
</div>

<script type="module">
import {initializeApp} from "https://www.gstatic.com/firebasejs/12.1.0/firebase-app.js";
import {getFirestore,collection,addDoc,getDocs,doc,deleteDoc,setDoc,getDoc,updateDoc,query,where} from "https://www.gstatic.com/firebasejs/12.1.0/firebase-firestore.js";
import {getAuth,signInWithEmailAndPassword,onAuthStateChanged,signOut} from "https://www.gstatic.com/firebasejs/12.1.0/firebase-auth.js";

const firebaseConfig={
apiKey:"AIzaSyAUbIDWnUGmI3UxQ-Qa46Rol6OuOyoouxc",
authDomain:"travel-idea-2d470.firebaseapp.com",
projectId:"travel-idea-2d470",
storageBucket:"travel-idea-2d470.firebasestorage.app",
messagingSenderId:"1001263523121",
appId:"1:1001263523121:web:9b8e550dd28f3e69167c10",
measurementId:"G-W23YCST5ZW"
};
const app=initializeApp(firebaseConfig),db=getFirestore(app),auth=getAuth(app);
const ADMIN_UID="MLjBNqf04mcpGVfTFVpEGjFSb2c2",ADMIN_NAME="Obito Uchiha";
let currentUser=null;
onAuthStateChanged(auth,u=>currentUser=u);

const photoInput=document.getElementById("photo"),profilePreview=document.getElementById("profilePreview");
photoInput.addEventListener("change",async function(){
if(this.files[0]) profilePreview.innerHTML=`<img src="${await compressImage(this.files[0])}">`;
});
function compressImage(file){
return new Promise(resolve=>{
const r=new FileReader();r.onload=e=>{const img=new Image();img.onload=()=>{
const c=document.createElement("canvas"),max=900;let w=img.width,h=img.height;
if(w>max){h=h*max/w;w=max}if(h>max){w=w*max/h;h=max}c.width=w;c.height=h;
c.getContext("2d").drawImage(img,0,0,w,h);resolve(c.toDataURL("image/jpeg",.75));
};img.src=e.target.result};r.readAsDataURL(file);
});
}
function esc(v){return String(v??"").replaceAll("&","&amp;").replaceAll("<","&lt;").replaceAll(">","&gt;").replaceAll('"',"&quot;").replaceAll("'","&#039;")}
function profile(){return JSON.parse(localStorage.getItem("travelProfile")||"null")}
function isAdmin(){return currentUser&&currentUser.uid===ADMIN_UID}

document.getElementById("createProfileBtn").onclick=async()=>{
const name=document.getElementById("name").value.trim(),age=document.getElementById("age").value.trim();
if(!name)return alert("দয়া করে তোমার নাম লিখো!");
if(!age)return alert("দয়া করে তোমার বয়স লিখো!");
let image=photoInput.files[0]?await compressImage(photoInput.files[0]):"";
const p={name,age,image,createdAt:new Date().toISOString()};
try{const ref=await addDoc(collection(db,"users"),p);p.id=ref.id;localStorage.setItem("travelProfile",JSON.stringify(p));alert("প্রোফাইল সফলভাবে তৈরি হয়েছে! 🎉");showHomePage()}
catch(e){console.error(e);alert("Profile save করতে সমস্যা হয়েছে।")}
};

window.showHomePage=()=>{
const p=profile();if(!p){location.reload();return}
document.body.innerHTML=`<div class="home"><div class="welcome">
${p.image?`<img class="user-photo" src="${p.image}">`:`<div class="avatar">👤</div>`}
<h2>Welcome, ${esc(p.name)}! 👋</h2><p>তোমার বয়স: ${esc(p.age)}</p><hr>
<button class="menu-btn" onclick="showMyProfile()">👤 My Profile</button>
<button class="menu-btn" onclick="showTourPlans()">🗺️ Tour Plans</button>
<button class="menu-btn" onclick="showMemory()">💭 Memory of US ❤️</button>
<button class="menu-btn" onclick="showTourStatus()">🔔 Tour Status</button>
<button class="menu-btn" onclick="adminLogin()">👑 Admin</button>
</div></div>`;
};

window.showMyProfile=()=>{
const p=profile();document.body.innerHTML=`<div class="profile-page"><button class="back-btn" onclick="showHomePage()">← Back</button>
<div class="welcome">${p.image?`<img class="user-photo" src="${p.image}">`:`<div class="avatar">👤</div>`}
<h2>${esc(p.name)}</h2><p>বয়স: ${esc(p.age)}</p><hr>
<button class="primary-btn" onclick="editMyProfile()">✏️ Edit My Profile</button></div></div>`;
};

window.editMyProfile=()=>{
const p=profile();document.body.innerHTML=`<div class="profile-page"><button class="back-btn" onclick="showMyProfile()">← Back</button>
<div class="profile-box"><h2>✏️ Edit Profile</h2><br>
<div class="profile-pic" id="editPreview">${p.image?`<img src="${p.image}">`:"👤"}</div>
<label class="upload-btn">📷 Change Photo<input type="file" id="editPhoto" accept="image/*"></label>
<div class="input-group"><label>নাম</label><input id="editName" value="${esc(p.name)}"></div>
<div class="input-group"><label>বয়স</label><input id="editAge" type="number" value="${esc(p.age)}"></div>
<button class="primary-btn" onclick="saveMyProfile()">💾 Save Changes</button></div></div>`;
document.getElementById("editPhoto").onchange=async e=>{if(e.target.files[0])document.getElementById("editPreview").innerHTML=`<img src="${await compressImage(e.target.files[0])}">`};
};

window.saveMyProfile=async()=>{
const old=profile(),name=document.getElementById("editName").value.trim(),age=document.getElementById("editAge").value.trim(),f=document.getElementById("editPhoto").files[0];
if(!name||!age)return alert("সব তথ্য পূরণ করো!");
const p={...old,name,age,image:f?await compressImage(f):old.image,updatedAt:new Date().toISOString()};
try{
if(old.id) await updateDoc(doc(db,"users",old.id),p);
else {const s=await getDocs(query(collection(db,"users"),where("name","==",old.name)));if(!s.empty)await updateDoc(s.docs[0].ref,p)}
localStorage.setItem("travelProfile",JSON.stringify(p));alert("Profile update হয়েছে! ✅");showMyProfile();
}catch(e){console.error(e);alert("Profile update করা যায়নি।")}
};

async function getPlans(){
const s=await getDocs(collection(db,"plans"));if(!s.empty)return s.docs.map(x=>({id:x.id,...x.data()}));
return[
{id:"default1",title:"🌊 Plan 1 — Beach Day",info:"📅 সময়: ১ দিন<br>🏖️ Cox's Bazar Beach<br>🌅 Sunset দেখা<br>🍽️ Local Food",default:true},
{id:"default2",title:"🌅 Plan 2 — Full Day Tour",info:"📅 সময়: ১ দিন<br>🏖️ Cox's Bazar Beach<br>🌴 Himchari<br>🌊 Inani Beach<br>🌅 Sunset",default:true},
{id:"default3",title:"🏝️ Plan 3 — 2 Days Tour",info:"📅 সময়: ২ দিন<br>🏖️ Cox's Bazar Beach<br>🌴 Himchari<br>🌊 Inani Beach<br>🏨 Hotel Stay",default:true}
]}
window.showTourPlans=async()=>{
document.body.innerHTML=`<div class="plans-page"><button class="back-btn" onclick="showHomePage()">← Back</button>
<h2 style="margin-bottom:15px">🗺️ কোথায় ঘুরতে চাও?</h2><button class="place" onclick="showCoxsBazar()">🏖️ Cox's Bazar</button>
<button class="place" onclick="comingSoon('Sajek')">⛰️ Sajek</button><button class="place" onclick="comingSoon('Sylhet')">🌿 Sylhet</button><button class="place" onclick="comingSoon('Bandarban')">🏔️ Bandarban</button></div>`;
};
window.comingSoon=p=>alert(p+" এর Plans আমরা পরের ধাপে যোগ করব! 🚀");

window.showCoxsBazar=async()=>{
const plans=await getPlans();let cards="";
for(const p of plans){
const q=await getDocs(query(collection(db,"selections"),where("destination","==","Cox's Bazar"),where("planId","==",p.id)));
cards+=`<div class="plan-card"><h2>${esc(p.title)}</h2><div class="plan-info">${p.info||""}</div>
<button class="plan-btn" onclick="selectPlan('${esc(p.id)}','${esc(p.title)}')">✅ Select Plan</button>
<div class="selected-count">👥 ${q.size} জন এই Plan Select করেছে</div></div>`;
}
document.body.innerHTML=`<div class="plans-page"><button class="back-btn" onclick="showTourPlans()">← Back</button>
<div class="destination-header"><div class="big-icon">🏖️</div><h1>Cox's Bazar</h1><p>একটি Tour Plan নির্বাচন করো।</p></div>${cards||"<p>কোনো Plan নেই।</p>"}</div>`;
};
window.selectPlan=async(planId,title)=>{
const p=profile();if(!p)return alert("আগে Profile তৈরি করো!");
try{await addDoc(collection(db,"selections"),{name:p.name,age:p.age,image:p.image||"",destination:"Cox's Bazar",planId,title,selectedAt:new Date().toISOString()});localStorage.setItem("mySelectedPlan",planId);alert(p.name+" তুমি Plan Select করেছো! 🎉");showCoxsBazar()}catch(e){console.error(e);alert("Plan save করতে সমস্যা হয়েছে।")}
};

window.showMemory=async()=>{document.body.innerHTML=`<div class="memory-page"><button class="back-btn" onclick="showHomePage()">← Back</button><div class="destination-header"><div class="big-icon">💭</div><h1>Memory of US ❤️</h1></div><div class="quote">"I miss all of my friends and these memories."</div><div id="memoryList" class="loading">⏳ Memories লোড হচ্ছে...</div></div>`;await loadMemories()};
async function loadMemories(){const box=document.getElementById("memoryList");try{const s=await getDocs(collection(db,"memories"));if(s.empty){box.innerHTML="<div class='memory-card'>এখনো কোনো Memory নেই। ❤️</div>";return}box.innerHTML="";s.forEach(x=>{const d=x.data();box.innerHTML+=`<div class="memory-card" onclick="openMemory('${x.id}')"><h2>📍 ${esc(d.place)}</h2><p>📅 ${esc(d.date)}<br>👥 ${esc(d.people)}</p></div>`})}catch(e){box.innerText="Memory লোড করা যায়নি।"}}
window.openMemory=async id=>{
document.body.innerHTML=`<div class="memory-page"><button class="back-btn" onclick="showMemory()">← Back</button><div id="memoryDetails" class="loading">⏳ Loading...</div></div>`;
try{const ms=await getDoc(doc(db,"memories",id));if(!ms.exists())return showMemory();const m=ms.data(),ps=await getDocs(query(collection(db,"memoryPhotos"),where("memoryId","==",id)));let photos="";
ps.forEach(x=>{const p=x.data();photos+=`<div class="photo-card"><img src="${p.image}"><small>📷 Added by: ${esc(p.uploadedBy)}</small>${isAdmin()?`<button class="delete-btn" onclick="deletePhoto('${x.id}','${id}')">🗑️ Delete</button>`:""}</div>`});
document.getElementById("memoryDetails").innerHTML=`<div class="destination-header"><div class="big-icon">📍</div><h1>${esc(m.place)}</h1><p>📅 ${esc(m.date)}</p><p>👥 ${esc(m.people)}</p></div>
<div class="memory-card"><h2>❤️ Memory</h2><p>I miss all of my friends and these memories.</p><hr><label>📸 ছবি যোগ করো</label><input type="file" id="memoryPhoto" accept="image/*"><button class="primary-btn" style="margin-top:12px" onclick="uploadMemoryPhoto('${id}')">📤 Upload Photo</button></div>
<h2 style="margin:20px 0 12px">📸 Our Photos</h2><div class="photo-grid">${photos||"<p>এখনো কোনো ছবি নেই।</p>"}</div>`}catch(e){console.error(e)}};
window.uploadMemoryPhoto=async id=>{const f=document.getElementById("memoryPhoto").files[0],p=profile();if(!f)return alert("আগে একটি ছবি নির্বাচন করো!");if(!p)return alert("আগে Profile তৈরি করো!");try{await addDoc(collection(db,"memoryPhotos"),{memoryId:id,image:await compressImage(f),uploadedBy:p.name,uploadedAt:new Date().toISOString()});alert("ছবি যোগ হয়েছে! ❤️");openMemory(id)}catch(e){alert("ছবি upload করতে সমস্যা হয়েছে।")}};
window.deletePhoto=async(pid,mid)=>{if(!isAdmin())return alert("Only Obito Uchiha can do it");if(!confirm("এই ছবিটি Delete করবে?"))return;await deleteDoc(doc(db,"memoryPhotos",pid));openMemory(mid)};

window.adminLogin=async()=>{
if(isAdmin())return showAdminPanel();
const email=prompt("Admin Email:");if(!email)return;const password=prompt("Admin Password:");if(!password)return;
try{const r=await signInWithEmailAndPassword(auth,email,password);if(r.user.uid!==ADMIN_UID){await signOut(auth);return alert("Only Obito Uchiha can do it")}showAdminPanel()}catch(e){alert("Admin login failed.")}
};

window.showAdminPanel=async()=>{
if(!isAdmin())return alert("Only Obito Uchiha can do it");
document.body.innerHTML=`<div class="admin-page"><button class="back-btn" onclick="showHomePage()">← Back</button>
<div class="admin-box"><h1>👑 ${ADMIN_NAME}</h1><p>Admin Control Panel</p></div>
<div class="admin-box"><h2>🗺️ Tour Plans Manage</h2><br>
<div class="input-group"><label>Plan Name</label><input id="planTitle" placeholder="🌊 Plan 4 — Special Tour"></div>
<div class="input-group"><label>Plan Details</label><textarea id="planInfo" placeholder="📅 সময়...&#10;🏖️ জায়গা..."></textarea></div>
<button class="primary-btn" onclick="addPlan()">➕ Add Plan</button><hr><div id="adminPlans">Loading...</div></div>
<div class="admin-box"><h2>👥 কে কোন Plan Select করেছে</h2><button class="admin-btn blue" onclick="loadSelections()">🔄 Refresh</button><div id="selectionList">Loading...</div></div>
<div class="admin-box"><h2>🔔 Tour Status</h2><button class="admin-btn green" onclick="setTourStatus('success')">✅ Tour Success</button><button class="admin-btn red" onclick="setTourStatus('cancel')">❌ Tour Cancel</button><button class="admin-btn" onclick="setTourStatus('ongoing')">🕐 আরো কিছুক্ষণ</button></div>
<div class="admin-box"><h2>💭 Memories</h2><button class="admin-btn blue" onclick="showAdminPanel()">🔄 Refresh</button><div id="adminMemoryList">Loading...</div></div>
<div class="admin-box"><button class="admin-btn" onclick="adminLogout()">Logout</button></div></div>`;
await loadAdminPlans();await loadSelections();await loadAdminMemories();
};

window.addPlan=async()=>{
if(!isAdmin())return alert("Only Obito Uchiha can do it");
const title=document.getElementById("planTitle").value.trim(),info=document.getElementById("planInfo").value.trim();
if(!title||!info)return alert("Plan Name ও Details পূরণ করো!");
try{await addDoc(collection(db,"plans"),{title,info,destination:"Cox's Bazar",createdBy:ADMIN_NAME,createdAt:new Date().toISOString()});alert("Plan যোগ হয়েছে! ✅");showAdminPanel()}catch(e){alert("Plan যোগ করা যায়নি।")}
};
async function loadAdminPlans(){
const box=document.getElementById("adminPlans"),s=await getDocs(collection(db,"plans"));if(s.empty){box.innerHTML="<p>Custom Plan নেই। উপরের ফর্ম দিয়ে Add করো।</p>";return}
box.innerHTML="";s.forEach(x=>{const d=x.data();box.innerHTML+=`<div class="admin-item"><h3>${esc(d.title)}</h3><p>${esc(d.info)}</p><button class="admin-btn red" onclick="deletePlan('${x.id}')">🗑️ Delete Plan</button></div>`})
}
window.deletePlan=async id=>{if(!isAdmin())return;if(!confirm("এই Plan Delete করবে?"))return;await deleteDoc(doc(db,"plans",id));alert("Plan Delete হয়েছে!");showAdminPanel()};

window.loadSelections=async()=>{
const box=document.getElementById("selectionList");if(!box)return;box.innerHTML="⏳ Loading...";
try{const s=await getDocs(collection(db,"selections"));if(s.empty){box.innerHTML="<p>কেউ এখনো Plan Select করেনি।</p>";return}
let html="<table><tr><th>নাম</th><th>Plan</th><th>সময়</th><th></th></tr>";
s.forEach(x=>{const d=x.data();html+=`<tr><td>${esc(d.name)}<br><span class="tiny">Age: ${esc(d.age)}</span></td><td>${esc(d.title||d.planId)}</td><td class="tiny">${esc(d.selectedAt)}</td><td><button class="admin-btn red" onclick="deleteSelection('${x.id}')">Delete</button></td></tr>`});
box.innerHTML=html+"</table>"}catch(e){box.innerText="Selections load করা যায়নি।"}
};
window.deleteSelection=async id=>{if(!isAdmin())return;if(!confirm("এই selection Delete করবে?"))return;await deleteDoc(doc(db,"selections",id));loadSelections()};

async function loadAdminMemories(){
const box=document.getElementById("adminMemoryList");if(!box)return;const s=await getDocs(collection(db,"memories"));if(s.empty){box.innerHTML="<p>কোনো Memory নেই।</p>";return}
box.innerHTML="";s.forEach(x=>{const d=x.data();box.innerHTML+=`<div class="admin-item"><h3>📍 ${esc(d.place)}</h3><p>📅 ${esc(d.date)}<br>👥 ${esc(d.people)}</p><button class="delete-btn" onclick="deleteMemory('${x.id}')">🗑️ Delete Memory</button></div>`})
}
window.deleteMemory=async id=>{if(!isAdmin())return;if(!confirm("এই Memory Delete করবে?"))return;await deleteDoc(doc(db,"memories",id));alert("Memory Delete হয়েছে!");showAdminPanel()};

window.setTourStatus=async status=>{
if(!isAdmin())return;try{await setDoc(doc(db,"tourStatus","current"),{status,updatedBy:ADMIN_NAME,updatedAt:new Date().toISOString()});alert(status==="success"?"Tour Success সবার কাছে যাবে! 🎉":status==="cancel"?"Tour Cancel সবার কাছে যাবে!":"আরো কিছুক্ষণ");}catch(e){alert("Status save করা যায়নি।")}
};
window.showTourStatus=async()=>{
document.body.innerHTML=`<div class="plans-page"><button class="back-btn" onclick="showHomePage()">← Back</button><div class="destination-header"><div class="big-icon">🔔</div><h1>Tour Status</h1><p>বর্তমান Tour status</p></div><div id="tourStatusBox" class="status-box">⏳ Loading...</div></div>`;
const s=await getDoc(doc(db,"tourStatus","current")),b=document.getElementById("tourStatusBox");if(!s.exists()){b.innerText="🕐 এখনো কোনো status দেওয়া হয়নি।";return}
const d=s.data();if(d.status==="success"){b.className="status-box status-success";b.innerText="🎉 Tour Success"}else if(d.status==="cancel"){b.className="status-box status-cancel";b.innerText="❌ Tour Cancel"}else b.innerText="🕐 Tour চলছে / আরো কিছুক্ষণ";
};
window.adminLogout=async()=>{await signOut(auth);alert("Admin Logout হয়েছে।");showHomePage()};

if(localStorage.getItem("travelProfile"))showHomePage();
</script>
</body>
</html>
