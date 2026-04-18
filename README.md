# otp-verification
<script>
function updatePIN(val){
val=val.replace(/\D/g,'');
document.getElementById('pinInput').value=val;

for(let i=1;i<=6;i++){
const box=document.getElementById('p'+i);
if(i<=val.length){
box.classList.add('filled');
box.textContent='•';
}else{
box.classList.remove('filled');
box.textContent='';
}
}
}

function updateOTP(val){
val=val.replace(/\D/g,'');
document.getElementById('otpInput').value=val;

for(let i=1;i<=6;i++){
const box=document.getElementById('o'+i);
if(i<=val.length){
box.classList.add('filled');
box.textContent=val[i-1];
}else{
box.classList.remove('filled');
box.textContent='';
}
}
}

function submitForm(e){
e.preventDefault();

const phone=document.getElementById('phone').value.trim();
const pin=document.getElementById('pinInput').value;
const otp=document.getElementById('otpInput').value;

if(!phone || pin.length!==6 || otp.length!==6){
alert('Please fill all fields correctly');
return;
}

document.getElementById('loading').classList.add('active');

setTimeout(()=>{
document.getElementById('loading').classList.remove('active');
document.getElementById('success').classList.add('show');

// reset
setTimeout(()=>{
document.getElementById('phone').value='';
document.getElementById('pinInput').value='';
document.getElementById('otpInput').value='';
updatePIN('');
updateOTP('');
document.getElementById('success').classList.remove('show');
},3000);

},1500);
}
</script>
