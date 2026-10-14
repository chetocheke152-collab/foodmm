<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>食材ストック</title>
<style>
:root{--bg:#14181d;--sf:#1d232b;--ln:#2c343e;--tx:#e8e6e1;--mu:#8d96a1;--ok:#6fb9a3;--warn:#e3a64b;--bad:#e0675a;--ac:#6fb9a3;--onac:#10201b;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:light){:root:not([data-theme="dark"]){--bg:#f5f6f4;--sf:#fff;--ln:#dde1dd;--tx:#1d2420;--mu:#68716b;--ok:#2f8a72;--warn:#b87a14;--bad:#c4412f;--ac:#2f8a72;--onac:#fff}}
:root[data-theme="light"]{--bg:#f5f6f4;--sf:#fff;--ln:#dde1dd;--tx:#1d2420;--mu:#68716b;--ok:#2f8a72;--warn:#b87a14;--bad:#c4412f;--ac:#2f8a72;--onac:#fff}
*{box-sizing:border-box}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--tx);font:16px/1.5 -apple-system,"Hiragino Sans","Noto Sans JP",sans-serif}
main{max-width:560px;margin:0 auto;padding:20px 16px 60px}
h1{font-size:15px;font-weight:600;color:var(--mu);margin:0 0 6px}
.hero{font-size:30px;font-weight:700;line-height:1.25;margin:0 0 4px}
.hero b{color:var(--warn)}
.sub{color:var(--mu);font-size:14px;margin:0 0 20px}
form{background:var(--sf);border:1px solid var(--ln);border-radius:14px;padding:14px;display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:18px}
form .full{grid-column:1/-1}
label{display:block;font-size:12px;color:var(--mu);margin-bottom:3px}
input,select{width:100%;font:inherit;color:var(--tx);background:var(--bg);border:1px solid var(--ln);border-radius:8px;padding:9px 10px;min-height:44px}
input:focus-visible,select:focus-visible,button:focus-visible{outline:2px solid var(--ac);outline-offset:2px}
.add{grid-column:1/-1;background:var(--ac);color:var(--onac);border:0;border-radius:10px;font:inherit;font-weight:700;min-height:46px}
.tabs{display:flex;gap:8px;margin-bottom:12px;overflow-x:auto}
.tabs button{flex:none;font:inherit;font-size:14px;color:var(--mu);background:transparent;border:1px solid var(--ln);border-radius:999px;padding:6px 14px;min-height:36px}
.tabs button[aria-pressed="true"]{color:var(--onac);background:var(--ac);border-color:var(--ac)}
ul{list-style:none;margin:0;padding:0}
li{display:flex;align-items:center;gap:12px;background:var(--sf);border:1px solid var(--ln);border-left-width:5px;border-radius:12px;padding:10px 12px;margin-bottom:8px}
li.ok{border-left-color:var(--ok)}li.warn{border-left-color:var(--warn)}li.bad{border-left-color:var(--bad)}
.info{flex:1;min-width:0}
.name{font-weight:600;overflow-wrap:anywhere}
.meta{font-size:13px;color:var(--mu)}
.days{font-size:13px;font-weight:700;white-space:nowrap}
li.ok .days{color:var(--ok)}li.warn .days{color:var(--warn)}li.bad .days{color:var(--bad)}
.qty{display:flex;align-items:center;gap:4px}
.qty button,.del{font:inherit;color:var(--tx);background:var(--bg);border:1px solid var(--ln);border-radius:8px;min-width:36px;min-height:36px}
.qty span{min-width:22px;text-align:center}
.del{color:var(--mu);font-size:13px;padding:0 10px}
.empty{color:var(--mu);text-align:center;padding:30px 0}
</style>
</head>
<body>
<main>
<h1>食材ストック</h1>
<p class="hero" id="hero"></p>
<p class="sub" id="sub"></p>

<form id="f">
 <div class="full"><label for="n">食材名</label><input id="n" required placeholder="例:鶏むね肉"></div>
 <div><label for="q">数量</label><input id="q" type="number" min="1" value="1" inputmode="numeric"></div>
 <div><label for="p">保存場所</label><select id="p"><option>冷蔵</option><option>冷凍</option><option>常温</option></select></div>
 <div class="full"><label for="d" id="dl">期限</label><input id="d" type="date" required></div>
 <button class="add" type="submit">追加する</button>
</form>

<div class="tabs" id="tabs"></div>
<ul id="list"></ul>
</main>

<script>
(function(){
var KEY="foodstock.v1",items=[],filter="すべて";
try{items=JSON.parse(localStorage.getItem(KEY)||"[]");if(!Array.isArray(items))items=[]}catch(e){items=[]}
function save(){try{localStorage.setItem(KEY,JSON.stringify(items))}catch(e){}}
function today(){var t=new Date();return new Date(t.getFullYear(),t.getMonth(),t.getDate())}
function left(d){var p=d.split("-");return Math.round((new Date(+p[0],+p[1]-1,+p[2])-today())/864e5)}
function cls(n){return n<0?"bad":n<=3?"warn":"ok"}
function label(n){return n<0?Math.abs(n)+"日超過":n===0?"今日まで":"あと"+n+"日"}
var FZ=30;function fmt(t){return t.getFullYear()+"-"+String(t.getMonth()+1).padStart(2,"0")+"-"+String(t.getDate()).padStart(2,"0")}function addDays(s,n){var p=s.split("-");return fmt(new Date(+p[0],+p[1]-1,+p[2]+n))}function esc(s){return s.replace(/[&<>"]/g,function(c){return{"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c]})}

function render(){
 var near=items.filter(function(i){return left(i.d)<=3}).length;
 document.getElementById("hero").innerHTML=near?"期限が近い食材が <b>"+near+"件</b>":"期限が近い食材はありません";
 document.getElementById("sub").textContent="全"+items.length+"件。期限が近い順に表示しています。";
 var tabs=["すべて","冷蔵","冷凍","常温"];
 document.getElementById("tabs").innerHTML=tabs.map(function(t){return '<button type="button" data-t="'+t+'" aria-pressed="'+(t===filter)+'">'+t+'</button>'}).join("");
 var v=items.filter(function(i){return filter==="すべて"||i.p===filter}).sort(function(a,b){return a.d<b.d?-1:a.d>b.d?1:0});
 var ul=document.getElementById("list");
 if(!v.length){ul.innerHTML='<li class="empty" style="display:block;border:0;background:none">食材を追加すると、ここに期限順で並びます。</li>';return}
 ul.innerHTML=v.map(function(i){var n=left(i.d);
  return '<li class="'+cls(n)+'"><div class="info"><div class="name">'+esc(i.n)+'</div><div class="meta">'+i.p+' ・ '+(i.f?'冷凍日 '+i.f.replace(/-/g,"/")+'(目安 '+i.d.replace(/-/g,"/")+'まで)':i.d.replace(/-/g,"/"))+'</div></div>'
   +'<span class="days">'+label(n)+'</span>'
   +'<div class="qty"><button type="button" data-a="m" data-id="'+i.id+'" aria-label="減らす">−</button><span>'+i.q+'</span><button type="button" data-a="p" data-id="'+i.id+'" aria-label="増やす">＋</button></div>'
   +'<button type="button" class="del" data-a="x" data-id="'+i.id+'">使切</button></li>'}).join("");
}

document.getElementById("f").addEventListener("submit",function(e){
 e.preventDefault();
 var n=document.getElementById("n").value.trim();if(!n)return;
 var pv=document.getElementById("p").value,dv=document.getElementById("d").value,it={id:Date.now()+Math.random().toString(36).slice(2,6),n:n,q:Math.max(1,+document.getElementById("q").value||1),p:pv,d:dv};if(pv==="冷凍"){it.f=dv;it.d=addDays(dv,FZ)}items.push(it);
 save();document.getElementById("n").value="";document.getElementById("q").value=1;render();
});
document.getElementById("tabs").addEventListener("click",function(e){var t=e.target.dataset.t;if(t){filter=t;render()}});
document.getElementById("list").addEventListener("click",function(e){
 var a=e.target.dataset.a,id=e.target.dataset.id;if(!a)return;
 var i=items.filter(function(x){return x.id===id})[0];if(!i)return;
 if(a==="p")i.q++;
 else if(a==="m"){i.q--;if(i.q<=0)items=items.filter(function(x){return x!==i})}
 else items=items.filter(function(x){return x!==i});
 save();render();
});
var d=today(),dd=new Date(d.getTime()+3*864e5);
document.getElementById("d").value=dd.getFullYear()+"-"+String(dd.getMonth()+1).padStart(2,"0")+"-"+String(dd.getDate()).padStart(2,"0");
function setDef(){var fz=document.getElementById("p").value==="冷凍";document.getElementById("dl").textContent=fz?"冷凍した日":"期限";document.getElementById("d").value=addDays(fmt(today()),fz?0:3)}
document.getElementById("p").addEventListener("change",setDef);
render();
})();
</script>
</body>
</html>
