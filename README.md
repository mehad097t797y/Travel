<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Our Travel Family</title>

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;
  font-family:Arial,"Noto Sans Bengali",sans-serif;
}

body{
  background:#eef2f7;
  color:#20252b;
}

button,input,textarea{
  font:inherit;
}

button{
  cursor:pointer;
}

.hidden{
  display:none!important;
}

/* ================= LOGIN ================= */

#auth{
  min-height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:20px;
  background:linear-gradient(135deg,#4f46e5,#00a9ff);
}

.authBox{
  width:100%;
  max-width:420px;
  background:#fff;
  border-radius:25px;
  padding:28px 22px;
  box-shadow:0 20px 50px #0004;
}

.logo{
  text-align:center;
  color:#5046df;
  font-size:28px;
  font-weight:bold;
  margin-bottom:7px;
}

.sub{
  text-align:center;
  color:#777;
  margin-bottom:22px;
}

.authBox input{
  width:100%;
  padding:14px;
  border:1px solid #ddd;
  border-radius:12px;
  margin-bottom:11px;
  outline:none;
}

.authBox input:focus{
  border-color:#5146e5;
}

.mainBtn{
  width:100%;
  padding:14px;
  background:#5146e5;
  color:white;
  border:0;
  border-radius:12px;
  font-weight:bold;
}

.switch{
  text-align:center;
  margin-top:15px;
  color:#666;
}

.switch span{
  color:#5146e5;
  font-weight:bold;
  cursor:pointer;
}

/* ================= APP ================= */

#app{
  max-width:600px;
  min-height:100vh;
  margin:auto;
  background:#f5f7fb;
  padding-bottom:80px;
}

.topbar{
  position:sticky;
  top:0;
  z-index:50;
  height:62px;
  background:white;
  border-bottom:1px solid #eee;
  display:flex;
  justify-content:space-between;
  align-items:center;
  padding:8px 13px;
}

.userTop{
  display:flex;
  align-items:center;
  gap:8px;
}

.userTop img{
  width:40px;
  height:40px;
  object-fit:cover;
  border-radius:50%;
  border:2px solid #5146e5;
}

.userTop b{
  display:block;
  font-size:14px;
}

.role{
  font-size:10px;
  background:#eee;
  border-radius:10px;
  padding:2px 7px;
}

.adminRole{
  color:#936000;
  background:#ffe5a7;
}

.logout{
  border:0;
  background:#ffe6e6;
  color:#d22;
  padding:8px 10px;
  border-radius:9px;
}

/* ================= PAGES ================= */

.page{
  display:none;
}

.page.active{
  display:block;
}

.section{
  padding:14px;
}

.card{
  background:white;
  border-radius:17px;
  padding:15px;
  margin-bottom:12px;
  box-shadow:0 2px 12px #0000000b;
}

.title{
  display:flex;
  justify-content:space-between;
  align-items:center;
  font-weight:bold;
  font-size:17px;
  margin-bottom:12px;
}

.item{
  background:#f6f7fa;
  border-radius:12px;
  padding:12px;
  margin:7px 0;
}

.smallBtn{
  border:0;
  border-radius:8px;
  padding:7px 9px;
  font-size:11px;
  background:#e8e7ff;
  color:#4b42d4;
}

.deleteBtn{
  background:#ffe1e1;
  color:#c22;
}

.addBtn{
  width:100%;
  padding:11px;
  margin-top:8px;
  border:1px dashed #aaa;
  border-radius:11px;
  background:white;
  color:#5146e5;
}

/* ================= PROFILE ================= */

.profileHero{
  text-align:center;
  padding:28px 15px;
  color:white;
  background:linear-gradient(135deg,#5146e5,#00a8ff);
}

.profileHero img{
  width:95px;
  height:95px;
  border-radius:50%;
  border:4px solid white;
  object-fit:cover;
}

.profileHero h2{
  margin-top:8px;
}

.profileHero p{
  opacity:.9;
  margin-top:3px;
  font-size:13px;
}

/* ================= TOURS ================= */

.plan{
  background:white;
  padding:9px;
  margin:4px 0;
  border-radius:9px;
  display:flex;
  justify-content:space-between;
  align-items:center;
}

/* ================= MEMORY ================= */

.photoGrid{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:5px;
  margin-top:10px;
}

.photo{
  position:relative;
  aspect-ratio:1;
  border-radius:8px;
  overflow:hidden;
  background:#eee;
}

.photo img{
  width:100%;
  height:100%;
  object-fit:cover;
}

.photoName{
  position:absolute;
  bottom:0;
  left:0;
  right:0;
  background:#0009;
  color:white;
  font-size:10px;
  text-align:center;
  padding:4px;
}

.photoDelete{
  position:absolute;
  right:3px;
  top:3px;
  width:22px;
  height:22px;
  border:0;
  border-radius:50%;
  background:#e33;
  color:white;
}

/* ================= MEMBERS ================= */

.member{
  display:flex;
  align-items:center;
  gap:10px;
  padding:11px 0;
  border-bottom:1px solid #eee;
}

.member img{
  width:50px;
  height:50px;
  object-fit:cover;
  border-radius:50%;
}

.memberInfo{
  flex:1;
}

.memberInfo b{
  display:block;
}

.memberRole{
  font-size:10px;
  color:#777;
}

/* ================= STATUS ================= */

.statusForm textarea{
  width:100%;
  min-height:90px;
  border:1px solid #ddd;
  border-radius:10px;
  padding:11px;
  resize:none;
  outline:none;
  margin-bottom:8px;
}

.status{
  background:white;
  border-radius:16px;
  padding:14px;
  margin-bottom:12px;
}

.author{
  display:flex;
  align-items:center;
  gap:9px;
  margin-bottom:10px;
}

.author img{
  width:40px;
  height:40px;
  object-fit:cover;
  border-radius:50%;
}

.author small{
  display:block;
  color:#777;
  font-size:10px;
}

.statusText{
  line-height:1.5;
  margin-bottom:10px;
}

.reactions{
  display:flex;
  gap:4px;
  flex-wrap:wrap;
  border-bottom:1px solid #eee;
  padding-bottom:10px;
}

.react{
  border:1px solid #eee;
  background:#fafafa;
  border-radius:15px;
  padding:5px 8px;
  font-size:12px;
}

.react.active{
  background:#e9e7ff;
  border-color:#5b52e7;
}

.comment{
  background:#f2f3f6;
  padding:8px;
  border-radius:9px;
  margin-top:6px;
  font-size:13px;
}

.commentForm{
  display:flex;
  gap:5px;
  margin-top:9px;
}

.commentForm input{
  flex:1;
  border:1px solid #ddd;
  border-radius:9px;
  padding:9px;
}

.commentForm button{
  border:0;
  background:#5146e5;
  color:white;
  padding:0 12px;
  border-radius:9px;
}

/* ================= SECRET ================= */

.secretGrid{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:8px;
}

.secret{
  background:white;
  border-radius:11px;
  overflow:hidden;
  position:relative;
}

.secret img{
  width:100%;
  aspect-ratio:1;
  object-fit:cover;
}

.secret p{
  text-align:center;
  padding:7px;
  font-size:12px;
}

/* ================= CHANNEL ================= */

.channel{
  background:white;
  padding:13px;
  border-radius:11px;
  margin-bottom:7px;
  display:flex;
  align-items:center;
  gap:10px;
}

.channelIcon{
  width:38px;
  height:38px;
  border-radius:50%;
  background:#e9e7ff;
  display:flex;
  justify-content:center;
  align-items:center;
}

/* ================= NAV ================= */

.bottomNav{
  position:fixed;
  z-index:100;
  bottom:0;
  left:50%;
  transform:translateX(-50%);
  width:100%;
  max-width:600px;
  height:68px;
  background:white;
  border-top:1px solid #ddd;
  display:flex;
  align-items:center;
  justify-content:space-around;
  overflow-x:auto;
}

.nav{
  min-width:65px;
  border:0;
  background:none;
  color:#777;
  font-size:10px;
}

.nav div{
  font-size:20px;
}

.nav.active{
  color:#5146e5;
  font-weight:bold;
}

/* ================= MODAL ================= */

.modalBg{
  position:fixed;
  inset:0;
  background:#0008;
  z-index:200;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:15px;
}

.modal{
  width:100%;
  max-width:420px;
  max-height:90vh;
  overflow:auto;
  background:white;
  border-radius:18px;
  padding:18px;
}

.modal h3{
  margin-bottom:12px;
}

.modal input,
.modal textarea{
  width:100%;
  padding:11px;
  border:1px solid #ddd;
  border-radius:10px;
  margin-bottom:8px;
}

.modalBtns{
  display:flex;
  gap:7px;
}

.modalBtns button{
  flex:1;
  border:0;
  padding:11px;
  border-radius:10px;
}

.cancel{
  background:#eee;
}

.save{
  background:#5146e5;
  color:white;
}

/* ================= TOAST ================= */

#toast{
  position:fixed;
  bottom:80px;
  left:50%;
  transform:translateX(-50%);
  background:#222;
  color:white;
  padding:10px 15px;
  border-radius:20px;
  display:none;
  z-index:500;
  font-size:13px;
}
</style>
</head>

<body>

<!-- =================================================
AUTH
================================================= -->

<div id="auth">

<div class="authBox">

<div class="logo">🌍 Our Travel Family</div>

<div class="sub" id="authSub">
নিজের অ্যাকাউন্টে Login করুন
</div>


<!-- LOGIN -->

<div id="loginBox">

<input
id="loginEmail"
type="email"
placeholder="Gmail">

<input
id="loginPassword"
type="password"
placeholder="Password">

<button class="mainBtn" onclick="login()">
Login
</button>

<div class="switch">
অ্যাকাউন্ট নেই?
<span onclick="showRegister()">Register</span>
</div>

</div>


<!-- REGISTER -->

<div id="registerBox" class="hidden">

<input
id="regName"
placeholder="নাম">

<input
id="regAge"
type="number"
placeholder="বয়স">

<input
id="regEmail"
type="email"
placeholder="Gmail">

<input
id="regPassword"
type="password"
placeholder="Password">

<label style="font-size:12px;color:#666">
Profile Photo
</label>

<input
id="regPhoto"
type="file"
accept="image/*">

<button class="mainBtn" onclick="register()">
Create Account
</button>

<div class="switch">
আগে থেকেই Account আছে?
<span onclick="showLogin()">Login</span>
</div>

</div>

</div>
</div>


<!-- =================================================
APP
================================================= -->

<div id="app" class="hidden">


<div class="topbar">

<div class="userTop">

<img id="topPhoto">

<div>
<b id="topName"></b>
<span id="topRole" class="role"></span>
</div>

</div>

<button class="logout" onclick="logout()">
Logout
</button>

</div>


<!-- PROFILE -->

<section id="profile" class="page active">

<div class="profileHero">

<img id="profilePhoto">

<h2 id="profileName"></h2>

<p id="profileInfo"></p>

</div>


<div class="section">

<div class="card">

<div class="title">
Your profile 👤
<span>➤</span>
</div>

<div class="item">
<b>নাম</b>
<p id="pName"></p>
</div>

<div class="item">
<b>বয়স</b>
<p id="pAge"></p>
</div>

<div class="item">
<b>Gmail</b>
<p id="pEmail"></p>
<small style="color:#777">
Gmail পরিবর্তন করা যাবে না।
</small>
</div>

<button class="addBtn" onclick="editProfile()">
✏️ Edit Profile
</button>

</div>

</div>

</section>


<!-- TOURS -->

<section id="tours" class="page">

<div class="section">

<div class="card">

<div class="title">
Tours 🌍
</div>

<div id="tourList"></div>

</div>

</div>

</section>


<!-- MEMORY -->

<section id="memory" class="page">

<div class="section">

<div class="card">

<div class="title">
Memory of US 🥰
</div>

<div id="memoryList"></div>

</div>

</div>

</section>


<!-- MEMBERS -->

<section id="members" class="page">

<div class="section">

<div class="card">

<div class="title">
Members 👥
</div>

<div id="memberList"></div>

</div>

</div>

</section>


<!-- STATUS -->

<section id="status" class="page">

<div class="section">

<div class="card statusForm">

<textarea
id="statusInput"
placeholder="ভ্রমণ নিয়ে কিছু লিখুন..."></textarea>

<button class="mainBtn" onclick="postStatus()">
Post
</button>

</div>

<div id="statusList"></div>

</div>

</section>


<!-- SECRET -->

<section id="secret" class="page">

<div class="section">

<div class="card">

<div class="title">
Secret Allied 🫂
</div>

<div id="secretList" class="secretGrid"></div>

<div id="secretAdd"></div>

</div>

</div>

</section>


<!-- CHANNELS -->

<section id="channels" class="page">

<div class="section">

<div class="card">

<div class="title">
Channels 📢
</div>

<div id="channelList"></div>

<button class="addBtn" onclick="addChannel()">
＋ Add Channel
</button>

</div>

</div>

</section>


<!-- BOTTOM NAV -->

<div class="bottomNav">

<button class="nav active" onclick="page('profile',this)">
<div>👤</div>
Profile
</button>

<button class="nav" onclick="page('tours',this)">
<div>🌍</div>
Tours
</button>

<button class="nav" onclick="page('memory',this)">
<div>🥰</div>
Memory
</button>

<button class="nav" onclick="page('members',this)">
<div>👥</div>
Members
</button>

<button class="nav" onclick="page('status',this)">
<div>💬</div>
Status
</button>

<button class="nav" onclick="page('secret',this)">
<div>🫂</div>
Secret
</button>

<button class="nav" onclick="page('channels',this)">
<div>📢</div>
Channels
</button>

</div>

</div>


<!-- MODAL -->

<div id="modalBg" class="modalBg hidden">

<div class="modal">

<h3 id="modalTitle"></h3>

<div id="modalContent"></div>

<div class="modalBtns">

<button class="cancel" onclick="closeModal()">
Cancel
</button>

<button class="save" id="saveModal">
Save
</button>

</div>

</div>

</div>


<div id="toast"></div>


<script>

/* =====================================================
ADMIN LOGIN
===================================================== */

const ADMIN_EMAIL="mehadislam12354@gmail.com";
const ADMIN_PASSWORD="noway890";


/* =====================================================
DATABASE
===================================================== */

const KEY="TRAVEL_FAMILY_DATA";

let data=JSON.parse(localStorage.getItem(KEY)) || {

users:[],

tours:[

{
name:"সাজেক",
plans:[
"Plan 1",
"Plan 2",
"Plan 3",
"Plan 4",
"Plan 5"
]
},

{
name:"বান্দরবান",
plans:[
"Plan 1",
"Plan 2",
"Plan 3",
"Plan 4",
"Plan 5"
]
},

{
name:"কক্সবাজার",
plans:[
"Plan 1",
"Plan 2",
"Plan 3",
"Plan 4",
"Plan 5"
]
}

],

memories:[

{
id:id(),
name:"বান্দরবান",
date:"তারিখ",
people:"যারা ছিলো",
photos:[]
}

],

statuses:[],

secret:[],

channels:[]

};


let currentUserId=
localStorage.getItem("TRAVEL_CURRENT_USER") || "";


/* =====================================================
SAVE
===================================================== */

function save(){

localStorage.setItem(KEY,JSON.stringify(data));

}


function id(){

return Date.now().toString(36)+
Math.random().toString(36).slice(2);

}


function user(){

return data.users.find(
x=>x.id===currentUserId
);

}


/* =====================================================
IMAGE
===================================================== */

function fileToBase64(file){

return new Promise(resolve=>{

if(!file){

resolve("");

return;

}

const reader=new FileReader();

reader.onload=()=>{
resolve(reader.result);
};

reader.readAsDataURL(file);

});

}


function avatar(name){

return "https://ui-avatars.com/api/?name="+
encodeURIComponent(name)+
"&background=5146e5&color=fff&size=300";

}


/* =====================================================
AUTH UI
===================================================== */

function showRegister(){

document.getElementById("loginBox")
.classList.add("hidden");

document.getElementById("registerBox")
.classList.remove("hidden");

document.getElementById("authSub")
.textContent="নতুন Account তৈরি করুন";

}


function showLogin(){

document.getElementById("registerBox")
.classList.add("hidden");

document.getElementById("loginBox")
.classList.remove("hidden");

document.getElementById("authSub")
.textContent="নিজের অ্যাকাউন্টে Login করুন";

}


/* =====================================================
REGISTER
===================================================== */

async function register(){

const name=
document.getElementById("regName")
.value.trim();

const age=
document.getElementById("regAge")
.value.trim();

const email=
document.getElementById("regEmail")
.value.trim()
.toLowerCase();

const password=
document.getElementById("regPassword")
.value;

const file=
document.getElementById("regPhoto")
.files[0];


if(!name || !age || !email || !password){

toast("সব তথ্য পূরণ করুন");

return;

}


/* ADMIN EMAIL দিয়ে অন্য password দিয়ে
   account তৈরি করা যাবে না */

if(email===ADMIN_EMAIL){

toast("এই Gmail শুধুমাত্র Admin-এর জন্য");

return;

}


if(data.users.some(x=>x.email===email)){

toast("এই Gmail আগে থেকেই ব্যবহার হয়েছে");

return;

}


const photo=
await fileToBase64(file);


const newUser={

id:id(),

name:name,

age:age,

email:email,

password:password,

photo:photo || avatar(name),

role:"member"

};


data.users.push(newUser);

save();

currentUserId=newUser.id;

localStorage.setItem(
"TRAVEL_CURRENT_USER",
currentUserId
);

openApp();

}


/* =====================================================
LOGIN
===================================================== */

function login(){

const email=
document.getElementById("loginEmail")
.value.trim()
.toLowerCase();

const password=
document.getElementById("loginPassword")
.value;


/* ADMIN */

if(
email===ADMIN_EMAIL &&
password===ADMIN_PASSWORD
){

let admin=data.users.find(
x=>x.email===ADMIN_EMAIL
);


if(!admin){

admin={

id:"ADMIN_ACCOUNT",

name:"Admin",

age:"",

email:ADMIN_EMAIL,

password:ADMIN_PASSWORD,

photo:avatar("Admin"),

role:"admin"

};

data.users.push(admin);

save();

}else{

admin.role="admin";

admin.password=ADMIN_PASSWORD;

save();

}


currentUserId=admin.id;

localStorage.setItem(
"TRAVEL_CURRENT_USER",
currentUserId
);

openApp();

return;

}


/* MEMBER */

const member=data.users.find(
x=>
x.email===email &&
x.password===password
);


if(!member){

toast("Gmail অথবা Password ভুল");

return;

}


currentUserId=member.id;

localStorage.setItem(
"TRAVEL_CURRENT_USER",
currentUserId
);

openApp();

}


/* =====================================================
OPEN APP
===================================================== */

function openApp(){

if(!user()){

logout();

return;

}

document.getElementById("auth")
.classList.add("hidden");

document.getElementById("app")
.classList.remove("hidden");

render();

}


function logout(){

localStorage.removeItem(
"TRAVEL_CURRENT_USER"
);

currentUserId="";

document.getElementById("app")
.classList.add("hidden");

document.getElementById("auth")
.classList.remove("hidden");

showLogin();

}


/* =====================================================
PROFILE
===================================================== */

function renderProfile(){

const u=user();

document.getElementById("topPhoto")
.src=u.photo;

document.getElementById("profilePhoto")
.src=u.photo;

document.getElementById("topName")
.textContent=u.name;

document.getElementById("profileName")
.textContent=u.name;

document.getElementById("profileInfo")
.textContent=
u.age+" বছর • "+u.email;

document.getElementById("pName")
.textContent=u.name;

document.getElementById("pAge")
.textContent=u.age+" বছর";

document.getElementById("pEmail")
.textContent=u.email;


const role=
document.getElementById("topRole");

role.textContent=
u.role==="admin"?
"Admin":
"Member";

role.className=
"role "+
(u.role==="admin"?"adminRole":"");

}


/* =====================================================
EDIT PROFILE
===================================================== */

function editProfile(){

const u=user();

openModal(
"Edit Profile",

`

<label>নাম</label>

<input id="editName"
value="${safe(u.name)}">

<label>বয়স</label>

<input id="editAge"
type="number"
value="${safe(u.age)}">

<label>Profile Photo</label>

<input id="editPhoto"
type="file"
accept="image/*">

<p style="font-size:12px;color:#777">
শুধু নাম, বয়স এবং Profile Photo পরিবর্তন করা যাবে।
</p>

`,

async()=>{

u.name=
document.getElementById("editName")
.value.trim();

u.age=
document.getElementById("editAge")
.value.trim();

const file=
document.getElementById("editPhoto")
.files[0];

if(file){

u.photo=
await fileToBase64(file);

}

save();

closeModal();

render();

toast("Profile আপডেট হয়েছে");

}

);

}


/* =====================================================
TOURS
===================================================== */

function renderTours(){

const box=
document.getElementById("tourList");

box.innerHTML="";

data.tours.forEach((place,i)=>{

let html=`

<div class="item">

<div style="
display:flex;
justify-content:space-between;
align-items:center">

<b>➤ ${safe(place.name)}</b>

${
user().role==="admin"
?
`<button class="smallBtn deleteBtn"
onclick="deletePlace(${i})">
Delete
</button>`
:""
}

</div>

`;

place.plans.forEach((plan,p)=>{

html+=`

<div class="plan">

<span>➤ ${safe(plan)}</span>

${
user().role==="admin"
?
`<button class="smallBtn deleteBtn"
onclick="deletePlan(${i},${p})">×</button>`
:""
}

</div>

`;

});


if(user().role==="admin"){

html+=`

<button class="addBtn"
onclick="addPlan(${i})">
＋ Add plan
</button>

`;

}


html+=`</div>`;

box.innerHTML+=html;

});


if(user().role==="admin"){

box.innerHTML+=`

<button class="addBtn"
onclick="addPlace()">
＋ Add place
</button>

`;

}

}


function addPlan(index){

promptModal(
"Add Plan",
"Plan-এর নাম",
value=>{

if(!value)return;

data.tours[index].plans.push(value);

save();

renderTours();

}

);

}


function deletePlan(place,plan){

if(!confirm("Plan delete করবেন?"))return;

data.tours[place].plans.splice(plan,1);

save();

renderTours();

}


function addPlace(){

promptModal(
"Add Place",
"নতুন জায়গার নাম",
value=>{

if(!value)return;

data.tours.push({

name:value,

plans:[
"Plan 1",
"Plan 2",
"Plan 3",
"Plan 4",
"Plan 5"
]

});

save();

renderTours();

}

);

}


function deletePlace(index){

if(!confirm("এই Place delete করবেন?"))return;

data.tours.splice(index,1);

save();

renderTours();

}


/* =====================================================
MEMORY
===================================================== */

function renderMemory(){

const box=
document.getElementById("memoryList");

box.innerHTML="";


data.memories.forEach((m,i)=>{

let photos="";


m.photos.forEach((p,pi)=>{

photos+=`

<div class="photo">

<img src="${p.photo}">

<div class="photoName">
${safe(p.name)}
</div>

${
user().role==="admin"
?
`<button class="photoDelete"
onclick="deleteMemoryPhoto(${i},${pi})">
×
</button>`
:""
}

</div>

`;

});


box.innerHTML+=`

<div class="item">

<div style="
display:flex;
justify-content:space-between">

<b>➤ ${safe(m.name)}</b>

${
user().role==="admin"
?
`<button class="smallBtn"
onclick="editMemory(${i})">
Edit
</button>`
:""
}

</div>

<p style="margin-top:8px">
📅 <b>তারিখ:</b> ${safe(m.date)}
</p>

<p style="margin-top:5px">
👥 <b>যারা ছিলো:</b> ${safe(m.people)}
</p>

<div class="photoGrid">
${photos}
</div>

<button class="addBtn"
onclick="addMemoryPhoto(${i})">
＋ Add Photo
</button>

${
user().role==="admin"
?
`<button class="addBtn deleteBtn"
onclick="deleteMemory(${i})">
Delete Memory
</button>`
:""
}

</div>

`;

});


if(user().role==="admin"){

box.innerHTML+=`

<button class="addBtn"
onclick="addMemory()">
＋ Add New memory
</button>

`;

}

}


function addMemory(){

openModal(
"Add New Memory",

`

<input id="memoryName"
placeholder="মেমোরির নাম">

<input id="memoryDate"
placeholder="তারিখ">

<textarea id="memoryPeople"
placeholder="যারা ছিলো"></textarea>

`,

()=>{

const name=
document.getElementById("memoryName")
.value.trim();

if(!name)return;

data.memories.push({

id:id(),

name:name,

date:
document.getElementById("memoryDate")
.value.trim(),

people:
document.getElementById("memoryPeople")
.value.trim(),

photos:[]

});

save();

closeModal();

renderMemory();

}

);

}


function editMemory(index){

const m=data.memories[index];

openModal(
"Edit Memory",

`

<input id="memoryName"
value="${safe(m.name)}">

<input id="memoryDate"
value="${safe(m.date)}">

<textarea id="memoryPeople">${safe(m.people)}</textarea>

`,

()=>{

m.name=
document.getElementById("memoryName")
.value.trim();

m.date=
document.getElementById("memoryDate")
.value.trim();

m.people=
document.getElementById("memoryPeople")
.value.trim();

save();

closeModal();

renderMemory();

}

);

}


function addMemoryPhoto(index){

openModal(
"Add Photo",

`

<input id="memoryPhoto"
type="file"
accept="image/*">

<input id="memoryPhotoName"
placeholder="ছবির নিচে নাম">

`,

async()=>{

const file=
document.getElementById("memoryPhoto")
.files[0];

if(!file){

toast("ছবি নির্বাচন করুন");

return;

}

data.memories[index].photos.push({

photo:
await fileToBase64(file),

name:
document.getElementById("memoryPhotoName")
.value.trim() ||
user().name

});

save();

closeModal();

renderMemory();

}

);

}


function deleteMemoryPhoto(mi,pi){

if(!confirm("ছবি delete করবেন?"))return;

data.memories[mi].photos.splice(pi,1);

save();

renderMemory();

}


function deleteMemory(index){

if(!confirm("Memory delete করবেন?"))return;

data.memories.splice(index,1);

save();

renderMemory();

}


/* =====================================================
MEMBERS
===================================================== */

function renderMembers(){

const box=
document.getElementById("memberList");

box.innerHTML="";


const users=
[...data.users].sort((a,b)=>{

if(a.role==="admin")return -1;

if(b.role==="admin")return 1;

return 0;

});


users.forEach(u=>{

box.innerHTML+=`

<div class="member">

<img src="${u.photo}">

<div class="memberInfo">

<b>${safe(u.name)}</b>

<span class="memberRole">

${
u.role==="admin"?
"Admin":
"Member"
}

</span>

</div>

</div>

`;

});

}


/* =====================================================
STATUS
===================================================== */

const emojis=[
"💖","🙂","🤣","😭","😍","🤯","🤬"
];


function postStatus(){

const text=
document.getElementById("statusInput")
.value.trim();

if(!text){

toast("কিছু লিখুন");

return;

}


data.statuses.unshift({

id:id(),

userId:currentUserId,

text:text,

reactions:{},

reactedBy:{},

comments:[]

});


document.getElementById("statusInput")
.value="";

save();

renderStatus();

}


function renderStatus(){

const box=
document.getElementById("statusList");

box.innerHTML="";


data.statuses.forEach((s,index)=>{

const author=
data.users.find(u=>u.id===s.userId);

if(!author)return;


let reacts="";


emojis.forEach(e=>{

const count=s.reactions[e]||0;

const active=
s.reactedBy[currentUserId]===e;

reacts+=`

<button class="react ${active?"active":""}"
onclick="react('${s.id}','${e}')">

${e} ${count}

</button>

`;

});


let comments="";


s.comments.forEach((c,ci)=>{

const cu=
data.users.find(u=>u.id===c.userId);


comments+=`

<div class="comment">

<b>${safe(cu?cu.name:"Unknown")}</b>:

${safe(c.text)}

${
user().role==="admin"
?
`<button
style="
float:right;
border:0;
background:none;
color:red"
onclick="deleteComment('${s.id}',${ci})">
×
</button>`
:""
}

</div>

`;

});


box.innerHTML+=`

<div class="status">

<div class="author">

<img src="${author.photo}">

<div>

<b>${safe(author.name)}</b>

<small>
${author.role==="admin"?"Admin":"Member"}
</small>

</div>

</div>


<div class="statusText">
${safe(s.text)}
</div>


<div class="reactions">
${reacts}
</div>


${comments}


<div class="commentForm">

<input
id="comment-${s.id}"
placeholder="Comment করুন">

<button
onclick="comment('${s.id}')">
➤
</button>

</div>


${
user().role==="admin"
?
`<button class="addBtn deleteBtn"
onclick="deleteStatus('${s.id}')">
Delete Post
</button>`
:""
}

</div>

`;

});

}


function react(id,reaction){

const s=
data.statuses.find(x=>x.id===id);

if(!s)return;


const old=
s.reactedBy[currentUserId];


if(old===reaction){

s.reactions[reaction]--;

delete s.reactedBy[currentUserId];

}else{

if(old){

s.reactions[old]--;

}

s.reactions[reaction]=
(s.reactions[reaction]||0)+1;

s.reactedBy[currentUserId]=reaction;

}


save();

renderStatus();

}


function comment(id){

const input=
document.getElementById("comment-"+id);

const text=input.value.trim();

if(!text)return;


const s=
data.statuses.find(x=>x.id===id);

s.comments.push({

userId:currentUserId,

text:text

});

save();

renderStatus();

}


function deleteComment(id,index){

if(!confirm("Comment delete করবেন?"))return;

const s=
data.statuses.find(x=>x.id===id);

s.comments.splice(index,1);

save();

renderStatus();

}


function deleteStatus(id){

if(!confirm("Post delete করবেন?"))return;

data.statuses=
data.statuses.filter(x=>x.id!==id);

save();

renderStatus();

}


/* =====================================================
SECRET ALLIED
===================================================== */

function renderSecret(){

const box=
document.getElementById("secretList");

box.innerHTML="";


data.secret.forEach((s,i)=>{

box.innerHTML+=`

<div class="secret">

<img src="${s.photo}">

<p>${safe(s.name)}</p>

${
user().role==="admin"
?
`<button
class="photoDelete"
onclick="deleteSecret(${i})">
×
</button>`
:""
}

</div>

`;

});


if(user().role==="admin"){

document.getElementById("secretAdd")
.innerHTML=`

<button class="addBtn"
onclick="addSecret()">
＋ Add Photo
</button>

`;

}else{

document.getElementById("secretAdd")
.innerHTML="";

}

}


function addSecret(){

openModal(
"Secret Allied",

`

<input id="secretPhoto"
type="file"
accept="image/*">

<input id="secretName"
placeholder="ছবির নিচে নাম">

`,

async()=>{

const file=
document.getElementById("secretPhoto")
.files[0];

if(!file)return;

data.secret.push({

photo:
await fileToBase64(file),

name:
document.getElementById("secretName")
.value.trim()

});

save();

closeModal();

renderSecret();

}

);

}


function deleteSecret(index){

if(!confirm("ছবি delete করবেন?"))return;

data.secret.splice(index,1);

save();

renderSecret();

}


/* =====================================================
CHANNELS
===================================================== */

function renderChannels(){

const box=
document.getElementById("channelList");

box.innerHTML="";


data.channels.forEach((c,i)=>{

box.innerHTML+=`

<div class="channel">

<div class="channelIcon">
📢
</div>

<div style="flex:1">
<b>${safe(c.name)}</b>
</div>

${
user().role==="admin"
?
`<button class="smallBtn deleteBtn"
onclick="deleteChannel(${i})">
Delete
</button>`
:""
}

</div>

`;

});

}


function addChannel(){

promptModal(
"Add Channel",
"Channel-এর নাম",
value=>{

if(!value)return;

data.channels.push({

id:id(),

name:value,

userId:currentUserId

});

save();

renderChannels();

}

);

}


function deleteChannel(index){

if(!confirm("Channel delete করবেন?"))return;

data.channels.splice(index,1);

save();

renderChannels();

}


/* =====================================================
PAGE
===================================================== */

function page(name,btn){

document.querySelectorAll(".page")
.forEach(x=>x.classList.remove("active"));

document.getElementById(name)
.classList.add("active");


document.querySelectorAll(".nav")
.forEach(x=>x.classList.remove("active"));

btn.classList.add("active");

window.scrollTo(0,0);

}


/* =====================================================
MODAL
===================================================== */

function openModal(title,html,saveFunction){

document.getElementById("modalTitle")
.textContent=title;

document.getElementById("modalContent")
.innerHTML=html;

document.getElementById("saveModal")
.onclick=saveFunction;

document.getElementById("modalBg")
.classList.remove("hidden");

}


function closeModal(){

document.getElementById("modalBg")
.classList.add("hidden");

}


function promptModal(title,placeholder,callback){

openModal(
title,
`<input id="promptInput"
placeholder="${safe(placeholder)}">`,
()=>{

const value=
document.getElementById("promptInput")
.value.trim();

closeModal();

callback(value);

}

);

}


/* =====================================================
SECURITY DISPLAY
===================================================== */

function safe(text){

return String(text??"")
.replace(/&/g,"&amp;")
.replace(/</g,"&lt;")
.replace(/>/g,"&gt;")
.replace(/"/g,"&quot;")
.replace(/'/g,"&#039;");

}


/* =====================================================
TOAST
===================================================== */

function toast(text){

const t=
document.getElementById("toast");

t.textContent=text;

t.style.display="block";

clearTimeout(window.toastTimer);

window.toastTimer=setTimeout(()=>{

t.style.display="none";

},2200);

}


/* =====================================================
RENDER
===================================================== */

function render(){

renderProfile();

renderTours();

renderMemory();

renderMembers();

renderStatus();

renderSecret();

renderChannels();

}


/* =====================================================
START
===================================================== */

if(
currentUserId &&
user()
){

openApp();

}

</script>

</body>
</html>
