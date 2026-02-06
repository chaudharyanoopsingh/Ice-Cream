<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Ice Cream Date?</title>

<style>
*{box-sizing:border-box}

body{
    margin:0;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg,#ffd6e7,#fff2cc);
    font-family:'Segoe UI',sans-serif;
    overflow:hidden;
}

.container{
    background:white;
    padding:50px 70px;
    border-radius:25px;
    text-align:center;
    box-shadow:0 25px 60px rgba(0,0,0,0.25);
}

h1{
    color:#ff4d88;
    font-size:34px;
}

p{
    color:#666;
    margin-bottom:30px;
}

.buttons{
    display:flex;
    gap:20px;
    justify-content:center;
}

button{
    padding:14px 30px;
    font-size:18px;
    border:none;
    border-radius:30px;
    cursor:pointer;
    transition:0.3s;
}

#yesBtn{
    background:#ff4d88;
    color:white;
    box-shadow:0 8px 20px rgba(255,77,136,0.5);
}

#noBtn{
    background:#eee;
}

.message{
    display:none;
    margin-top:25px;
    font-size:24px;
    color:#ff4d88;
}

/* confetti */
.confetti{
    position:absolute;
    width:10px;
    height:10px;
    opacity:0.8;
    animation:fall 3s linear forwards;
}

@keyframes fall{
    from{transform:translateY(-10vh) rotate(0deg)}
    to{transform:translateY(110vh) rotate(720deg)}
}
</style>
</head>

<body>

<div class="container">
    <h1> Judge Madam, Will you go out for ice cream with me? 🍦</h1>
    <p>Because ice cream tastes better together 💕</p>

    <div class="buttons">
        <button id="yesBtn">Yes 😍</button>
        <button id="noBtn">No 🙈</button>
    </div>

    <div class="message" id="msg">
        Yaaay! Ice cream date confirmed 🍦💖
    </div>
</div>

<script>
const yesBtn=document.getElementById("yesBtn");
const noBtn=document.getElementById("noBtn");
const msg=document.getElementById("msg");

let scale=1;

// YES CLICK → show message + confetti
yesBtn.onclick=()=>{
    msg.style.display="block";
    createConfetti();
}

// NO CLICK → grow YES button
noBtn.onclick=()=>{
    scale+=0.25;
    yesBtn.style.transform=`scale(${scale})`;
}

// Confetti generator 🎉
function createConfetti(){
    for(let i=0;i<120;i++){
        const c=document.createElement("div");
        c.className="confetti";
        c.style.left=Math.random()*100+"vw";
        c.style.background=`hsl(${Math.random()*360},70%,60%)`;
        c.style.animationDuration=(2+Math.random()*2)+"s";
        document.body.appendChild(c);
        setTimeout(()=>c.remove(),3000);
    }
}
</script>

</body>
</html>
