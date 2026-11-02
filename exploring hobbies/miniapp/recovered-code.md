# 从对话提取的代码片段

以下仅去掉聊天引用前缀，未执行其中的命令。这些是历史中间片段，不是最终版本源码。

## 1. `/tmp/preview.cjs`

~~~~~~~~~~
const {chromium}=require('playwright');
(async()=>{const b=await chromium.launch({headless:true,args:['--no-sandbox']});const p=await b.newPage({viewport:{width:1280,height:940}});await p.goto('file:///workspace/attachments/5964155d-288f-48bc-9da5-4da2b0a120de/truth-or-dare.html');await p.waitForTimeout(1500);await p.screenshot({path:'/tmp/before.png'});await b.close()})()
~~~~~~~~~~

## 2. `/tmp/optimize.py`

~~~~~~~~~~
from pathlib import Path
import re
src=Path('/workspace/attachments/5964155d-288f-48bc-9da5-4da2b0a120de/truth-or-dare.html')
s=src.read_text()
# Original SVG illustrations inspired by the upstream chibi proportions and blue palette.
def gradient(i, colors, cx='32%',cy='20%'):
 return f'<radialGradient id="{i}" cx="{cx}" cy="{cy}" r="85%">'+''.join(f'<stop offset="{j/(len(colors)-1):.2f}" stop-color="{c}"/>' for j,c in enumerate(colors))+'</radialGradient>'
def pet(kind):
 cat=kind=='cat'; fur='v2-pearl' if cat else 'v2-blue'; ear='v2-rose' if cat else 'v2-indigo'
 tail='<path d="M140 152C184 173 190 125 172 128C161 130 177 153 145 141" fill="url(#v2-pearl)" stroke="#A6B9DB" stroke-width="1"/>' if cat else '<path d="M140 151C178 149 181 121 167 125C157 128 163 141 140 138" fill="url(#v2-indigo)"/>'
 ears='<path d="M45 78L42 29Q43 16 55 23L83 47M117 47L145 23Q157 16 158 29L155 78" fill="url(#v2-pearl)" stroke="#B1C5E7"/><path d="M52 34L54 65 75 50M148 34L146 65 125 50" fill="url(#v2-rose)"/>' if cat else '<g class="v2-ear"><path d="M62 48C33 26 14 48 24 88C29 111 48 111 56 88L69 59Z" fill="url(#v2-indigo)"/><path d="M138 48C167 26 186 48 176 88C171 111 152 111 144 88L131 59Z" fill="url(#v2-indigo)"/><path d="M35 52Q25 68 34 88" fill="none" stroke="#A8C4FB" stroke-width="4" stroke-linecap="round" opacity=".55"/></g>'
 nose='<path d="M95 105Q100 101 105 105L100 110Z" fill="url(#v2-rose)"/>' if cat else '<path d="M91 103Q100 98 109 103Q109 111 100 113Q91 111 91 103" fill="url(#v2-indigo)"/><ellipse cx="97" cy="103" rx="4" ry="1.7" fill="#BFD9FF"/>'
 mouth='<path d="M100 110V114M88 115Q94 123 100 115Q106 123 112 115" stroke="#667B9F" fill="none" stroke-width="1.6" stroke-linecap="round"/>' if cat else '<path d="M87 115Q100 128 113 115" stroke="#667B9F" fill="none" stroke-width="1.6" stroke-linecap="round"/><path d="M96 122V127Q100 136 105 127V122" fill="url(#v2-rose)"/>'
 return f'''<symbol id="{kind}-art" viewBox="0 0 200 200">
 <ellipse class="v2-ground" cx="100" cy="186" rx="53" ry="7" fill="url(#v2-ground)"/>
 <g class="v2-breathe">
 <g class="pet-tail v2-tail">{tail}</g>
 <ellipse cx="101" cy="153" rx="38" ry="33" fill="url(#{fur})"/>
 <ellipse cx="97" cy="153" rx="23" ry="26" fill="url(#v2-belly)"/>
 <ellipse cx="76" cy="180" rx="20" ry="10" fill="url(#{fur})"/><ellipse cx="124" cy="180" rx="20" ry="10" fill="url(#{fur})"/>
 <path d="M70 180v4m7-4v4m45-4v4m7-4v4" stroke="#9EB5DA" stroke-width="1" opacity=".6"/>
 <g class="v2-head">
 {ears}
 <path d="M39 83C39 51 62 39 100 39S161 51 161 83C166 122 144 139 100 139S34 122 39 83Z" fill="url(#{fur})" stroke="#AFC3E1" stroke-width=".65"/>
 <ellipse cx="75" cy="58" rx="26" ry="10" transform="rotate(-16 75 58)" fill="white" opacity=".48"/>
 {'<path d="M87 44L91 56M100 42V53M113 44L109 56" stroke="#ADC5EC" stroke-width="4" stroke-linecap="round"/>' if cat else '<path d="M94 40C86 56 89 65 100 65S114 54 105 40" fill="url(#v2-belly)"/>'}
 <ellipse cx="100" cy="115" rx="26" ry="15" fill="url(#v2-belly)"/>
 <g class="v2-eyes"><use href="#v2-eye" x="72" y="87"/><use href="#v2-eye" x="128" y="87"/></g>
 <ellipse cx="52" cy="108" rx="13" ry="8" fill="url(#v2-blush)"/><ellipse cx="148" cy="108" rx="13" ry="8" fill="url(#v2-blush)"/>
 {nose}{mouth}
 {'<path d="M39 106L51 109M37 115L50 115M149 109L161 106M150 115L163 115" stroke="#91ACD2" stroke-width="1.2" stroke-linecap="round"/>' if cat else ''}
 </g>
 <path d="M71 135Q100 147 129 135L126 143Q100 154 74 143Z" fill="url(#v2-indigo)"/>
 <path d="M99 144C90 134 82 145 99 155C116 145 108 134 99 144" fill="url(#v2-rose)" stroke="#D28AA9" stroke-width=".6"/>
 <g class="pet-paw"><ellipse cx="66" cy="156" rx="12" ry="19" transform="rotate(22 66 156)" fill="url(#{fur})"/><ellipse cx="61" cy="163" rx="5" ry="6" fill="url(#v2-rose)" opacity=".8"/></g>
 <ellipse cx="135" cy="156" rx="11" ry="18" transform="rotate(-24 135 156)" fill="url(#{fur})"/>
 </g></symbol>'''
defs=''.join([gradient('v2-pearl',['#FFFFFF','#EDF4FF','#B4C9EA','#7797C8']),gradient('v2-blue',['#F6FAFF','#CCDEFB','#90AFE4','#5877B4']),gradient('v2-belly',['#FFFFFF','#F8FBFF','#DCE7F7']),gradient('v2-indigo',['#B3D1FF','#7698DE','#445FAD']),gradient('v2-rose',['#FFF1F5','#F2B4CB','#CF7F9E']),gradient('v2-blush',['#F2A8C1','#F7CEDD00'],cx='50%',cy='50%'),gradient('v2-ground',['#6A82B35C','#8097BD00'],cx='50%',cy='50%'),gradient('v2-iris',['#99E2FF','#598BD6','#294D92'],cx='42%',cy='78%')])
defs+='''<g id="v2-eye"><ellipse rx="14" ry="18" fill="#F8FCFF"/><ellipse cy="1" rx="11.8" ry="16" fill="url(#v2-iris)"/><g class="v2-pupil"><ellipse cy="-1" rx="7" ry="11.5" fill="#213957"/><ellipse cx="-4" cy="-7" rx="4.5" ry="5" fill="white"/><circle cx="5" cy="7" r="2.5" fill="#D9F7FF"/></g><path d="M-13-8Q0-21 13-8" fill="none" stroke="#56749F" stroke-width="2.2" stroke-linecap="round"/></g>'''
s=re.sub(r'<symbol id="cat-art".*?</symbol>',lambda m: defs+pet('cat'),s,flags=re.S)
s=re.sub(r'<symbol id="dog-art".*?</symbol>',lambda m: pet('dog'),s,flags=re.S)
# Unify all static and dynamically inserted UI font stacks, including the pet settings.
s=re.sub(r"--font: [^;]+;",'--font: "PingFang SC", "Microsoft YaHei", "Noto Sans CJK SC", system-ui, sans-serif;',s,count=1)
s=re.sub(r'font-family:[^;}]+', 'font-family:var(--font)',s)
css='''
<style id="companion-upgrade">
/* Shared type system; keep the existing game and storage behavior. */
html { font-size:16px; -webkit-text-size-adjust:100%; }
body { -webkit-font-smoothing:antialiased; text-rendering:optimizeLegibility; }
body, button, input, select, textarea, code { font-family:var(--font); }
h1,h2,h3,h4 { font-weight:700; letter-spacing:0; }
.hero h2 { font-weight:700; letter-spacing:-.035em; }
.logo-text,.choice-label,.section-title { font-weight:700; letter-spacing:0; }
button,input,select,textarea { line-height:1.5; }
.game-container { box-shadow:0 8px 0 #DFE8EE,0 18px 42px #48659708; }
.choice-truth { background:radial-gradient(ellipse at 40% 32%,#FFFFFF 0%,#EDF3FF 55%,#DDE8FD 100%); }
.choice-dare { background:radial-gradient(ellipse at 40% 32%,#FFFFFF 0%,#FFF1F7 55%,#F6DFED 100%); }
.choice-pet { height:174px; filter:drop-shadow(0 9px 8px #526B9B18); }
.choice-btn { overflow:hidden; }
.v2-breathe { transform-box:view-box; transform-origin:100px 182px; animation:companion-breathe 4.6s ease-in-out infinite; }
.v2-head { transform-box:view-box; transform-origin:100px 125px; transition:transform .35s ease; }
.v2-eyes { transform-box:fill-box; transform-origin:center; animation:companion-blink 6.2s infinite; }
.v2-pupil { transform:translate(var(--gaze-x,0px),var(--gaze-y,0px)); transition:transform .15s ease-out; }
.v2-tail { transform-box:view-box; transform-origin:145px 148px; animation:companion-tail 3.6s ease-in-out infinite; }
.choice-dare .v2-breathe { animation-delay:-1.8s; }
.choice-dare .v2-eyes { animation-delay:-2.7s; }
.choice-btn:is(:hover,:focus-visible) .v2-head { transform:rotate(-5deg) translateY(-2px); }
.choice-dare:is(:hover,:focus-visible) .v2-head { transform:rotate(5deg) translateY(-2px); }
.choice-btn:is(:hover,:focus-visible) .v2-tail { animation-duration:.7s; }
@keyframes companion-breathe { 0%,100%{transform:translateY(0) scale(1,1)}50%{transform:translateY(-2px) scale(1.008,1.015)} }
@keyframes companion-blink { 0%,42%,46%,94%,98%,100%{transform:scaleY(1)}44%,96%{transform:scaleY(.08)} }
@keyframes companion-tail {0%,100%{transform:rotate(-5deg)}50%{transform:rotate(9deg)}}
html[data-pet-visibility="hidden"] .v2-breathe,html[data-pet-visibility="hidden"] .v2-eyes,html[data-pet-visibility="hidden"] .v2-tail { animation-play-state:paused; }
@media(max-width:600px){.choice-pet{height:140px}.choice-label{font-size:22px}.hero h2{letter-spacing:-.025em}}
@media(prefers-reduced-motion:reduce){.v2-breathe,.v2-eyes,.v2-tail{animation:none!important}.v2-head,.v2-pupil{transform:none!important;transition:none!important}}
html[data-motion="reduced"] .v2-head,html[data-motion="reduced"] .v2-pupil {transform:none!important}
</style>
'''
s=s.replace('</head>',css+'</head>')
# Existing runtime adds its own styles later; normalize those stacks in the original source above.
js='''<script id="companion-gaze">
(()=>{
 const cards=document.querySelectorAll('.choice-btn');
 for(const card of cards){
  card.addEventListener('pointermove',e=>{
   if(e.pointerType==='touch'||document.documentElement.dataset.motion==='reduced'||matchMedia('(prefers-reduced-motion: reduce)').matches)return;
   const r=card.getBoundingClientRect();
   card.style.setProperty('--gaze-x',((e.clientX-r.left)/r.width*4-2).toFixed(1)+'px');
   card.style.setProperty('--gaze-y',((e.clientY-r.top)/r.height*3-1.5).toFixed(1)+'px');
  },{passive:true});
  card.addEventListener('pointerleave',()=>{card.style.removeProperty('--gaze-x');card.style.removeProperty('--gaze-y')});
 }
 const visibility=()=>document.documentElement.dataset.petVisibility=document.hidden?'hidden':'visible';
 document.addEventListener('visibilitychange',visibility);visibility();
})();
</script>'''
s=s.replace('</body>',js+'</body>')
Path('/workspace/output/truth-or-dare-optimized.html').write_text(s)
print('Saved',len(s.encode()),'bytes')
~~~~~~~~~~

## 3. `/tmp/check.cjs`

~~~~~~~~~~
const {chromium}=require('playwright');
(async()=>{
const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});
const p=await b.newPage({viewport:{width:1280,height:940}});const errors=[];p.on('pageerror',e=>errors.push(e.message));
await p.goto('http://127.0.0.1:8765/output/truth-or-dare-optimized.html');await p.waitForTimeout(1000);
await p.locator('#btn-truth').click();await p.waitForTimeout(400);if(!await p.locator('#question-text').innerText())throw Error('Missing question');
await p.locator('#btn-next').click();await p.waitForTimeout(400);await p.locator('#btn-quick-complete').click();await p.locator('#btn-back').click();
await p.locator('#nav-bank').click();if(await p.locator('#stat-total').innerText()!=='100')throw Error('Bank count');
await p.locator('#nav-agent').click();await p.locator('#agent-input').fill('统计');await p.locator('#agent-send').click();await p.waitForTimeout(200);
await p.locator('#nav-game').click();await p.locator('#motion-toggle').click();
if(await p.locator('html').getAttribute('data-motion')!=='reduced')throw Error('Motion toggle');
const animation=await p.locator('#btn-truth').evaluate(el=>getComputedStyle(el.querySelector('svg.choice-pet').querySelector('use')).fontFamily);
await p.setViewportSize({width:390,height:844});await p.waitForTimeout(400);
if(await p.evaluate(()=>document.documentElement.scrollWidth>innerWidth))throw Error('Horizontal overflow');
await p.screenshot({path:'/workspace/output/preview-mobile.png',fullPage:true});
await p.locator('#motion-toggle').click();await p.emulateMedia({reducedMotion:'reduce'});await p.waitForTimeout(150);
if(await p.locator('html').getAttribute('data-motion')!=='reduced')throw Error('OS reduced motion');
console.log(JSON.stringify({checks:['抽题、换题、完成、返回','题库100题','指令助手','手动与系统减少动画','390px手机无横向溢出'],pageErrors:errors,font:animation}));
if(errors.length)throw Error(errors.join(';'));
await b.close();
})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 4. `/tmp/upgrade_v3.py`

~~~~~~~~~~
from pathlib import Path
import re
s=Path('/workspace/output/truth-or-dare-optimized.html').read_text()
# Soften contours without changing any SVG view boxes or layout dimensions.
s=s.replace('M45 78L42 29Q43 16 55 23L83 47M117 47L145 23Q157 16 158 29L155 78','M43 79Q37 56 43 30Q46 19 56 28L83 48M117 48L144 28Q154 19 157 30Q163 56 157 79')
s=s.replace('M52 34L54 65 75 50M148 34L146 65 125 50','M53 38Q51 49 55 63Q63 54 73 51Q63 43 53 38M147 38Q149 49 145 63Q137 54 127 51Q137 43 147 38')
s=s.replace('M39 83C39 51 62 39 100 39S161 51 161 83C166 122 144 139 100 139S34 122 39 83Z','M39 85C37 56 61 39 100 40C139 39 163 56 161 85C168 116 147 141 100 141C53 141 32 116 39 85Z')
s=s.replace('<ellipse cx="101" cy="153" rx="38" ry="33"','<ellipse cx="101" cy="153" rx="40" ry="35"')
# Place smile lids beside each pair of eyes for warm, expressive reactions.
s=s.replace('<g class="v2-eyes"><use href="#v2-eye" x="72" y="87"/><use href="#v2-eye" x="128" y="87"/></g>', '<g class="v2-eyes"><use href="#v2-eye" x="72" y="87"/><use href="#v2-eye" x="128" y="87"/></g><g class="v3-smile-eyes" fill="none" stroke="#52729C" stroke-width="3.5" stroke-linecap="round"><path d="M61 89Q72 76 83 89M117 89Q128 76 139 89"/></g>')
s=re.sub(r'<script id="companion-gaze">.*?</script>','',s,flags=re.S)
# Stable hooks in the existing controller: no duplicated drag or proximity listeners.
old='let n=["approach","evade","orbit","nuzzle"][c(Math.floor(this.random()*4),0,3)];this.action(n,s)'
new='let n=this.nextInteraction();this.action(n,s)'
assert old in s;s=s.replace(old,new,1)
needle='action(t,e=performance.now()){if(!z.includes(t)'
replacement='''nextInteraction(){if(!this.interactionBag?.length){this.interactionBag=["approach","evade","orbit","nuzzle","hop","wag"];for(let i=this.interactionBag.length-1;i>0;i--){let j=Math.floor(this.random()*(i+1));[this.interactionBag[i],this.interactionBag[j]]=[this.interactionBag[j],this.interactionBag[i]]}if(this.interactionBag.at(-1)===this.lastInteraction)[this.interactionBag[0],this.interactionBag[this.interactionBag.length-1]]=[this.interactionBag.at(-1),this.interactionBag[0]]}return this.lastInteraction=this.interactionBag.pop()}action(t,e=performance.now()){if(!z.includes(t)'''
assert needle in s;s=s.replace(needle,replacement,1)
s=s.replace('this.trigger(["nuzzle","hop","wag"][Math.floor(Math.random()*3)])','this.trigger(this.brain.nextInteraction())',1)
s=s.replace('this.tapAt=performance.now(),this.trigger("nuzzle")','this.tapAt=performance.now(),this.trigger(this.brain.nextInteraction())',1)
# Fire before resume so the whale renderer can suspend all upstream video decoding.
needle='this.syncControls(),this.resume(),this.persist()}catch(t)'
assert needle in s;s=s.replace(needle,'this.syncControls(),document.dispatchEvent(new Event("pet3d-ready")),this.resume(),this.persist()}catch(t)',1)
Path('/tmp/v3-base.html').write_text(s)
~~~~~~~~~~

## 5. `/tmp/whale.svg`

~~~~~~~~~~
<svg class="v3-whale" id="pet3d-whale" viewBox="0 0 256 280" aria-hidden="true" data-emote="idle">
<defs>
 <radialGradient id="whale-skin" cx="30%" cy="20%" r="88%"><stop stop-color="#DCFAFF"/><stop offset=".34" stop-color="#91CFFA"/><stop offset=".72" stop-color="#6499E6"/><stop offset="1" stop-color="#476DBA"/></radialGradient>
 <radialGradient id="whale-belly" cx="36%" cy="22%" r="85%"><stop stop-color="#FFFFFF"/><stop offset=".6" stop-color="#E7F6FF"/><stop offset="1" stop-color="#B5D6F8"/></radialGradient>
 <linearGradient id="whale-fin" x1="0" y1="0" x2="1" y2="1"><stop stop-color="#ADDFFD"/><stop offset=".65" stop-color="#6C9DE3"/><stop offset="1" stop-color="#4A6AB3"/></linearGradient>
 <radialGradient id="whale-cheek"><stop stop-color="#F3AFCD" stop-opacity=".85"/><stop offset="1" stop-color="#F3AFCD" stop-opacity="0"/></radialGradient>
 <radialGradient id="whale-shadow"><stop stop-color="#6986B5" stop-opacity=".25"/><stop offset="1" stop-color="#6986B5" stop-opacity="0"/></radialGradient>
</defs>
<ellipse cx="124" cy="229" rx="80" ry="11" fill="url(#whale-shadow)"/>
<g class="whale-float">
 <g class="whale-tail"><path d="M166 154C186 163 201 146 199 125C199 117 204 117 212 130C219 132 230 122 237 123C241 131 230 149 219 151C220 177 190 185 166 176Z" fill="url(#whale-fin)"/><path d="M201 144Q211 156 207 164" fill="none" stroke="#B3DCFF" stroke-width="2" opacity=".6" stroke-linecap="round"/></g>
 <path d="M45 140C39 104 60 77 106 77C153 72 183 101 184 140C193 179 165 210 115 212C69 214 36 188 45 140Z" fill="url(#whale-skin)"/>
 <path d="M49 158C73 178 117 177 144 160C158 151 175 157 180 169C170 201 146 211 114 212C79 214 53 194 49 158Z" fill="url(#whale-belly)"/>
 <ellipse cx="87" cy="98" rx="29" ry="10" transform="rotate(-19 87 98)" fill="white" opacity=".32"/>
 <path d="M54 121C54 103 66 94 76 91" stroke="#EEFDFF" stroke-width="3" stroke-linecap="round" fill="none" opacity=".45"/>
 <g class="whale-eyes"><use href="#v2-eye" x="79" y="141"/><use href="#v2-eye" x="133" y="141"/></g>
 <g class="whale-happy-eyes" stroke="#375B94" stroke-width="3" stroke-linecap="round" fill="none"><path d="M68 142Q79 128 90 142M122 142Q133 128 144 142"/></g>
 <path class="whale-wink-eye" d="M122 142Q133 130 144 142" stroke="#375B94" stroke-width="3" stroke-linecap="round" fill="none"/>
 <ellipse cx="58" cy="158" rx="15" ry="9" fill="url(#whale-cheek)"/><ellipse cx="153" cy="158" rx="15" ry="9" fill="url(#whale-cheek)"/>
 <path class="whale-mouth" d="M98 158Q106 166 114 158" fill="none" stroke="#466591" stroke-width="2.3" stroke-linecap="round"/>
 <ellipse class="whale-ooh" cx="106" cy="162" rx="5" ry="7" fill="#6484AE"/>
 <g class="whale-fin"><path d="M60 167C38 153 29 169 39 184C46 193 60 198 70 195C77 190 70 174 60 167Z" fill="url(#whale-fin)"/><path d="M45 171Q43 181 57 187" fill="none" stroke="#CCEFFF" stroke-width="2" opacity=".6" stroke-linecap="round"/></g>
 <path d="M143 181Q157 196 167 181" fill="none" stroke="#B2D3F3" stroke-width="2" stroke-linecap="round"/>
 <g class="whale-spout" fill="#A9E4FF"><path d="M108 75C111 57 104 46 98 48C94 50 99 59 106 62C106 50 114 39 120 43C126 49 117 55 112 57L112 75Z"/><circle cx="93" cy="43" r="3.5"/><circle cx="125" cy="36" r="2.5"/></g>
 <g class="whale-hearts" fill="#E6A1C2"><path d="M66 75C50 63 59 54 66 61C73 54 82 63 66 75Z"/><path d="M164 86C153 76 160 70 165 75C170 70 177 77 164 86Z"/></g>
 <g class="whale-bubbles" fill="#E8FAFF" stroke="#92CCEF" stroke-width="1.2"><circle cx="176" cy="88" r="8"/><circle cx="194" cy="68" r="5"/><circle cx="185" cy="50" r="3"/></g>
 <g class="whale-stars" fill="#FFD68B"><path d="M54 84L57 92 65 95 57 98 54 106 51 98 43 95 51 92Z"/><path d="M168 62L171 69 178 72 171 75 168 82 165 75 158 72 165 69Z"/></g>
</g>
</svg>
~~~~~~~~~~

## 6. `/tmp/v3.css`

~~~~~~~~~~
<style id="companion-interactions-v3">
/* All reactions stay inside the existing SVG boxes; no layout animation. */
.v3-smile-eyes{opacity:0}
svg[data-reaction="smile"] .v2-eyes{opacity:0}
svg[data-reaction="smile"] .v3-smile-eyes{opacity:1}
svg[data-near="true"] .v2-head{transform:translate(var(--pet-lean,0px),-2px) rotate(var(--pet-tilt,0deg))}
svg[data-reaction="blink"] .v2-eyes{animation:pet-near-blink .55s ease-in-out}
svg[data-reaction="wiggle"] .v2-breathe{animation:pet-near-wiggle .85s ease-in-out}
svg[data-reaction="wave"] .pet-paw{animation:pet-near-wave .85s ease-in-out}
svg[data-reaction="bounce"] .v2-breathe{animation:pet-near-bounce .85s ease-in-out}
svg[data-reaction="wave"] .v2-tail,svg[data-reaction="smile"] .v2-tail{animation-duration:.65s}
@keyframes pet-near-blink{0%,35%,70%,100%{transform:scaleY(1)}18%,52%{transform:scaleY(.1)}}
@keyframes pet-near-wiggle{0%,100%{transform:rotate(0)}25%{transform:rotate(-5deg)}65%{transform:rotate(5deg)}}
@keyframes pet-near-wave{0%,100%{transform:rotate(0)}25%,65%{transform:rotate(30deg)}45%,85%{transform:rotate(-6deg)}}
@keyframes pet-near-bounce{0%,100%{transform:translateY(0) scale(1)}25%{transform:translateY(2px) scale(1.03,.97)}55%{transform:translateY(-6px) scale(.99,1.01)}80%{transform:translateY(0) scale(1.02,.98)}}
.v3-whale{position:absolute;inset:0;width:100%;height:100%;pointer-events:none;transform-origin:50% 66%}
#pet3d-widget[data-appearance="whale"] .pet3d-canvas{visibility:hidden}
#pet3d-widget[data-appearance="original"] .v3-whale{display:none}
.whale-float{transform-origin:115px 205px;animation:whale-breathe 4.5s ease-in-out infinite}
.whale-tail{transform-origin:173px 165px;animation:whale-tail 3.2s ease-in-out infinite}
.whale-fin{transform-origin:64px 173px;animation:whale-fin 4.8s ease-in-out infinite}
.whale-eyes{transform-box:fill-box;transform-origin:center;animation:companion-blink 7s infinite}
.whale-spout,.whale-hearts,.whale-bubbles,.whale-stars,.whale-happy-eyes,.whale-wink-eye,.whale-ooh{opacity:0}
#pet3d-whale[data-emote="splash"] .whale-spout{animation:whale-spout 1.5s ease-out}
#pet3d-whale[data-emote="love"] .whale-hearts{animation:whale-rise 1.5s ease-out}
#pet3d-whale[data-emote="bubbles"] .whale-bubbles{animation:whale-rise 1.5s ease-out}
#pet3d-whale[data-emote="star"] .whale-stars{animation:whale-twinkle 1.5s ease-out}
#pet3d-whale[data-emote="smile"] .whale-eyes{opacity:0}
#pet3d-whale[data-emote="smile"] .whale-happy-eyes{opacity:1}
#pet3d-whale[data-emote="wink"] .whale-eyes use:last-child{opacity:0}
#pet3d-whale[data-emote="wink"] .whale-wink-eye{opacity:1}
#pet3d-whale[data-emote="bubbles"] .whale-mouth{opacity:0}
#pet3d-whale[data-emote="bubbles"] .whale-ooh{opacity:1}
#pet3d-whale[data-emote="wink"] .whale-fin,#pet3d-whale[data-emote="smile"] .whale-fin{animation:whale-fin .5s ease-in-out 3}
#pet3d-whale[data-emote="love"] .whale-float{animation:whale-cuddle 1.5s ease-in-out}
#pet3d-widget[data-variant="lilac"] .v3-whale{filter:hue-rotate(20deg)}
#pet3d-widget[data-paused="true"] .v3-whale *,html[data-pet-visibility="hidden"] .v3-whale *{animation-play-state:paused!important}
.pet3d-appearance{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin:12px 0}
.pet3d-appearance button{padding:9px 6px;border:1px solid #CFD7EF;border-radius:10px;background:white;font-size:12px}
.pet3d-appearance button[aria-pressed="true"]{color:#3C5FD5;background:#E6EDFF;border-color:#99AEE9;font-weight:700}
.pet3d-random{width:100%;min-height:38px;padding:8px;border-radius:10px;background:#E6EDFF;color:#3C5FD5;font-size:12px;font-weight:700;margin:8px 0}
.pet3d-random:disabled{opacity:.5;cursor:not-allowed}
@keyframes whale-breathe{0%,100%{transform:translateY(0) rotate(-1deg)}50%{transform:translateY(-4px) rotate(1deg)}}
@keyframes whale-tail{0%,100%{transform:rotate(-5deg)}50%{transform:rotate(7deg)}}
@keyframes whale-fin{0%,100%{transform:rotate(0)}50%{transform:rotate(-9deg)}}
@keyframes whale-spout{0%{opacity:0;transform:translateY(7px) scaleY(.7)}25%,65%{opacity:1;transform:translateY(0) scaleY(1)}100%{opacity:0;transform:translateY(-10px)}}
@keyframes whale-rise{0%{opacity:0;transform:translateY(8px)}25%,70%{opacity:1}100%{opacity:0;transform:translateY(-16px)}}
@keyframes whale-twinkle{0%,100%{opacity:0}30%,65%{opacity:1}45%{opacity:.4}}
@keyframes whale-cuddle{0%,100%{transform:rotate(0)}30%{transform:rotate(-6deg)}70%{transform:rotate(6deg)}}
html[data-motion="reduced"] svg[data-near] .v2-head{transform:none!important}
html[data-motion="reduced"] .v3-whale *,html[data-motion="reduced"] svg[data-reaction] *{animation:none!important;transition:none!important}
@media(prefers-reduced-motion:reduce){.v3-whale *,svg[data-reaction] *{animation:none!important;transition:none!important}svg[data-near] .v2-head{transform:none!important}}
</style>
~~~~~~~~~~

## 7. `/tmp/v3.js`

~~~~~~~~~~
/* Companion interactions, v3. Geometry is read once per input frame, never in an idle loop. */
(()=>{
'use strict';
const root=document.documentElement;
const reduceQuery=matchMedia('(prefers-reduced-motion: reduce)');
const reduced=()=>reduceQuery.matches||root.dataset.motion==='reduced';
const visible=()=>!document.hidden;
function bag(values){
 let pool=[],last;
 return ()=>{
  if(!pool.length){
   pool=[...values];
   for(let i=pool.length-1;i>0;i--){const j=Math.floor(Math.random()*(i+1));[pool[i],pool[j]]=[pool[j],pool[i]]}
   if(pool.length>1&&pool[pool.length-1]===last)[pool[0],pool[pool.length-1]]=[pool[pool.length-1],pool[0]];
  }
  return last=pool.pop();
 };
}
const animals=[...document.querySelectorAll('svg')].filter(svg=>svg.querySelector('use[href="#cat-art"],use[href="#dog-art"]'));
const states=animals.map(el=>({el,near:false,last:-Infinity,choose:bag(['blink','wiggle','wave','bounce','smile']),timer:0}));
let pointer=null,inputFrame=0,lastInput=-Infinity;
function resetAnimal(s){
 clearTimeout(s.timer);s.near=false;delete s.el.dataset.near;delete s.el.dataset.reaction;
 for(const key of ['--gaze-x','--gaze-y','--pet-lean','--pet-tilt'])s.el.style.removeProperty(key);
}
function reactAnimal(s,now){
 if(now-s.last<2300)return;
 s.last=now;s.el.dataset.reaction=s.choose();
 clearTimeout(s.timer);s.timer=setTimeout(()=>{delete s.el.dataset.reaction},1100);
}
function updatePointer(now){
 inputFrame=0;if(!pointer||!visible()||reduced())return;
 if(now-lastInput<32){inputFrame=requestAnimationFrame(updatePointer);return}lastInput=now;
 // Read all geometry before writing styles, avoiding interleaved layout work.
 const boxes=states.map(s=>s.el.getBoundingClientRect());
 states.forEach((s,i)=>{
  const r=boxes[i];
  if(!r.width||!r.height||r.bottom<0||r.top>innerHeight){if(s.near)resetAnimal(s);return}
  const cx=r.left+r.width*.5,cy=r.top+r.height*.55;
  const dx=pointer.x-cx,dy=pointer.y-cy;
  const ex=Math.max(Math.abs(dx)-r.width*.36,0),ey=Math.max(Math.abs(dy)-r.height*.4,0);
  const distance=Math.hypot(ex,ey),near=distance<=(s.near?84:64);
  if(near){
   if(!s.near){s.near=true;s.el.dataset.near='true';reactAnimal(s,now)}
   const clamp=(x,m)=>Math.max(-m,Math.min(m,x));
   s.el.style.setProperty('--gaze-x',clamp(dx/40,2.8).toFixed(1)+'px');
   s.el.style.setProperty('--gaze-y',clamp(dy/50,1.8).toFixed(1)+'px');
   s.el.style.setProperty('--pet-lean',clamp(dx/60,2).toFixed(1)+'px');
   s.el.style.setProperty('--pet-tilt',clamp(dx/35,4).toFixed(1)+'deg');
  }else if(s.near)resetAnimal(s);
 });
}
function schedule(){if(pointer&&!inputFrame&&!reduced()&&visible())inputFrame=requestAnimationFrame(updatePointer)}
window.addEventListener('pointermove',e=>{if(e.pointerType==='touch')return;pointer={x:e.clientX,y:e.clientY};schedule()},{passive:true});
window.addEventListener('scroll',schedule,{passive:true});window.addEventListener('resize',schedule,{passive:true});
function clearPointer(){pointer=null;cancelAnimationFrame(inputFrame);inputFrame=0;states.forEach(resetAnimal)}
window.addEventListener('blur',clearPointer);
window.addEventListener('pointerout',e=>{if(!e.relatedTarget)clearPointer()});
// Keyboard feedback uses the existing card buttons; decorative artwork gains no tab stops.
for(const s of states){
 const button=s.el.closest('button');
 if(button)button.addEventListener('focus',()=>{if(!reduced()&&visible())reactAnimal(s,performance.now())});
 s.el.addEventListener('pointerdown',()=>{if(!reduced()&&visible())reactAnimal(s,performance.now())},{passive:true});
}
const appearanceKey='truth_or_dare_pet_appearance_v3';
let appearance='whale';try{if(localStorage.getItem(appearanceKey)==='original')appearance='original'}catch{}
const whaleMarkup=__WHALE_MARKUP__;
let pet,whale,widget,randomButton,emoteTimer=0,buttonTimer=0,appearanceButtons;
const nextEmote=bag(['splash','wink','love','bubbles','smile','star']);
const phrases={
 splash:['噗——送你一朵小水花。','冒个泡，今天也想陪着你。'],
 wink:['眨眨眼，偷偷给你加油。','收到！给你一个小小的暗号。'],
 love:['把软乎乎的喜欢，分你一点。','今天的心情，是甜甜的。'],
 bubbles:['咕噜咕噜，把烦恼吹成泡泡。','慢慢来，我在这里等你。'],
 smile:['听你说话，我就很开心。','嘿嘿，又被你发现啦。'],
 star:['给认真生活的你一颗小星星。','今天也有值得期待的小惊喜。']
};
const choosePhrase=Object.fromEntries(Object.entries(phrases).map(([k,v])=>[k,bag(v)]));
function resetEffects(){clearTimeout(emoteTimer);if(whale)whale.dataset.emote='idle'}
function syncPaused(){if(widget&&pet)widget.dataset.paused=String(pet.paused||!pet.enabled||document.hidden)}
function setAppearance(value,save=true){
 appearance=value;widget.dataset.appearance=value;
 appearanceButtons.forEach(b=>b.setAttribute('aria-pressed',String(b.dataset.appearance===value)));
 document.querySelector('#pet3d-hit').setAttribute('aria-label',`摸摸${value==='whale'?'DeepSeek 大肥鱼':'原版 DeepSeek 搭子'}，按回车随机互动，可拖动改变位置`);
 if(save)try{localStorage.setItem(appearanceKey,value)}catch{}
 resetEffects();
 if(pet.renderer){
  if(value==='whale')pet.renderer.fallback();
  pet.renderer.setActive(pet.enabled&&!pet.paused&&!document.hidden,pet.reduced);
 }
 syncPaused();pet.wake();
}
function installRenderer(){
 if(!pet?.renderer||pet.renderer.v3Installed)return;
 const renderer=pet.renderer;renderer.v3Installed=true;
 const originalActive=renderer.setActive.bind(renderer);
 const originalBehavior=renderer.setBehavior.bind(renderer);
 const originalResponse=renderer.playResponse.bind(renderer);
 renderer.setActive=(active,reduce)=>{
  // The SVG appearance does not decode hidden videos or run video frame callbacks.
  if(appearance==='whale')return originalActive(false,reduce);
  return originalActive(active,reduce);
 };
 renderer.setBehavior=(...args)=>{if(appearance==='original')return originalBehavior(...args)};
 renderer.playResponse=(...args)=>{if(appearance==='original')return originalResponse(...args)};
 setAppearance(appearance,false);
}
function installPet(){
 pet=window.gamePet3D;if(!pet||pet.v3Installed)return;pet.v3Installed=true;
 widget=document.querySelector('#pet3d-widget');
 widget.insertAdjacentHTML('afterbegin',whaleMarkup);whale=document.querySelector('#pet3d-whale');
 const panel=document.querySelector('#pet3d-panel');
 const group=document.createElement('div');group.className='pet3d-appearance';group.setAttribute('role','group');group.setAttribute('aria-label','搭子外观');
 group.innerHTML='<button type="button" data-appearance="whale">大肥鱼</button><button type="button" data-appearance="original">原版搭子</button>';
 panel.querySelector('header').insertAdjacentElement('afterend',group);
 appearanceButtons=[...group.querySelectorAll('button')];appearanceButtons.forEach(b=>b.addEventListener('click',()=>setAppearance(b.dataset.appearance)));
 randomButton=document.createElement('button');randomButton.type='button';randomButton.className='pet3d-random';randomButton.id='pet3d-random';randomButton.textContent='随机互动 · 看看它会做什么';
 panel.querySelector('.pet3d-stats').before(randomButton);
 const hint=document.createElement('p');hint.textContent='鼠标靠近或轻点搭子，会随机回应；也可以拖动它。大肥鱼会吐泡泡、喷水花、眨眼或送小心心。';
 group.after(hint);
 pet.randomInteraction=()=>{
  const now=performance.now();
  if(!pet.diagnostics.ready||!pet.enabled||pet.paused||document.hidden||pet.drag?.moved||now<(pet.v3Cooldown||0))return false;
  return pet.trigger(pet.brain.nextInteraction());
 };
 randomButton.addEventListener('click',()=>{pet.unlockAudio();pet.randomInteraction()});
 const oldFeedback=pet.feedback.bind(pet);
 pet.feedback=(action,now)=>{
  oldFeedback(action,now);
  pet.v3Cooldown=now+Math.max(1800,pet.brain.current.duration+500);
  const emote=nextEmote();
  clearTimeout(emoteTimer);
  // Reduced motion retains a static facial expression and a text acknowledgement.
  whale.dataset.emote=reduced()?'smile':emote;
  widget.dataset.lastReaction=emote;
  const bubble=document.querySelector('#pet3d-bubble');
  if(appearance==='whale')bubble.textContent=choosePhrase[emote]();
  randomButton.disabled=true;clearTimeout(buttonTimer);
  buttonTimer=setTimeout(()=>{randomButton.disabled=pet.paused||!pet.enabled},Math.max(1800,pet.brain.current.duration+500));
  emoteTimer=setTimeout(resetEffects,1650);
 };
 const oldDraw=pet.draw.bind(pet);
 pet.draw=(now,delta)=>{
  oldDraw(now,delta);
  if(appearance==='whale'){
   whale.style.transform=document.querySelector('#pet3d-canvas').style.transform;
   document.querySelector('#pet3d-performance').textContent='大肥鱼 · 矢量轻量显示；靠近互动有冷却，页面隐藏时暂停。';
  }
  if(widget.dataset.variant!==pet.settings.variant)widget.dataset.variant=pet.settings.variant;
 };
 const oldTrigger=pet.trigger.bind(pet);
 pet.trigger=action=>{
  if(action!=='idle'&&(document.hidden||performance.now()<(pet.v3Cooldown||0)))return false;
  return oldTrigger(action);
 };
 const oldSync=pet.syncControls.bind(pet);
 pet.syncControls=()=>{oldSync();syncPaused();randomButton.disabled=pet.paused||!pet.enabled||performance.now()<(pet.v3Cooldown||0)};
 setAppearance(appearance,false);installRenderer();
}
document.addEventListener('pet3d-ready',()=>{installPet();installRenderer()});
if(document.readyState==='loading')document.addEventListener('DOMContentLoaded',installPet,{once:true});else installPet();
function motionChanged(){if(reduced()){clearPointer();resetEffects()}syncPaused()}
new MutationObserver(motionChanged).observe(root,{attributes:true,attributeFilter:['data-motion']});
reduceQuery.addEventListener('change',motionChanged);
document.addEventListener('visibilitychange',()=>{
 root.dataset.petVisibility=document.hidden?'hidden':'visible';
 if(document.hidden){clearPointer();resetEffects()}syncPaused();
});
root.dataset.petVisibility=document.hidden?'hidden':'visible';
window.addEventListener('pagehide',()=>{clearPointer();resetEffects();clearTimeout(buttonTimer)},{once:true});
})();
~~~~~~~~~~

## 8. `/tmp/build_v3.py`

~~~~~~~~~~
from pathlib import Path
import json
s=Path('/tmp/v3-base.html').read_text()
js=Path('/tmp/v3.js').read_text().replace('__WHALE_MARKUP__',json.dumps(Path('/tmp/whale.svg').read_text(),ensure_ascii=False))
s=s.replace('this.trigger(this.brain.nextInteraction())','this.randomInteraction()',2)
s=s.replace('</body>',Path('/tmp/v3.css').read_text()+'\n<script id="companion-interactions-v3-runtime">\n'+js+'\n</script>\n</body>')
Path('/workspace/output/truth-or-dare-v3.html').write_text(s)
print('Built',len(s.encode()),'bytes')
~~~~~~~~~~

## 9. `/tmp/v3-preview.cjs`

~~~~~~~~~~
const {chromium}=require('playwright');
(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});const p=await b.newPage({viewport:{width:1280,height:940}});const errors=[];p.on('pageerror',e=>errors.push(e.stack));await p.goto('http://127.0.0.1:8765/output/truth-or-dare-v3.html');await p.waitForTimeout(1300);await p.screenshot({path:'/workspace/output/v3-preview-desktop.png'});console.log(JSON.stringify({errors,pet:await p.evaluate(()=>({ready:gamePet3D?.diagnostics.ready,renderer:gamePet3D?.renderer?.mode,active:gamePet3D?.renderer?.running,svg:document.querySelector('#pet3d-whale')?.getBoundingClientRect().toJSON(),shape:document.querySelector('#pet3d-widget')?.dataset.appearance}))}));await b.close()})()
~~~~~~~~~~

## 10. `/tmp/v3-test.cjs`

~~~~~~~~~~
const {chromium}=require('playwright');const assert=require('node:assert/strict');
const url='http://127.0.0.1:8766/output/truth-or-dare-v3.html';
(async()=>{
 const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});
 const p=await b.newPage({viewport:{width:1280,height:940}});p.setDefaultTimeout(5000);
 const errors=[];p.on('pageerror',e=>errors.push(e.stack));const checks=[];
 await p.goto(url);await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready&&window.gamePet3D.v3Installed);
 const base=await b.newPage({viewport:{width:1280,height:940}});await base.goto(url.replace('truth-or-dare-v3.html','truth-or-dare-optimized.html'));
 const boxes=page=>page.evaluate(()=>Object.fromEntries(['.app-header','.hero','.game-container','.choice-area','.game-sidebar'].map(s=>{const r=document.querySelector(s).getBoundingClientRect();return[s,[r.x,r.y,r.width,r.height]]})));
 assert.deepEqual(await boxes(p),await boxes(base));await base.close();checks.push('主页面布局尺寸与上一版一致');
 const cat=p.locator('#btn-truth .choice-pet');const r=await cat.boundingBox();
 // Outside the actual image box, but inside its 64px proximity range.
 await p.mouse.move(r.x+r.width/2,r.y-18);await p.waitForTimeout(100);
 assert.equal(await cat.getAttribute('data-near'),'true');assert.ok(await cat.getAttribute('data-reaction'));checks.push('猫图像外的靠近范围可以触发反馈');
 await p.mouse.move(10,110);await p.waitForTimeout(80);assert.equal(await cat.getAttribute('data-near'),null);
 await p.waitForTimeout(2350);await p.mouse.move(r.x+r.width/2,r.y+20);await p.waitForTimeout(100);
 assert.ok(await cat.getAttribute('data-reaction'));checks.push('离开后可重新触发，带冷却及表情状态');
 const draws=await p.evaluate(()=>{const brain=gamePet3D.brain;brain.interactionBag=[];return Array.from({length:18},()=>brain.nextInteraction())});
 for(let i=1;i<draws.length;i++)assert.notEqual(draws[i],draws[i-1]);for(let i=0;i<18;i+=6)assert.equal(new Set(draws.slice(i,i+6)).size,6);checks.push('随机动作每组六种不重复，相邻组不连播相同动作');
 // Feedback exercises the real controller and expression bag, with no wait for visual durations.
 const emotes=await p.evaluate(()=>{const pet=gamePet3D;const out=[];for(let i=0;i<12;i++){pet.v3Cooldown=0;pet.trigger(i%2?'wag':'hop');out.push(document.querySelector('#pet3d-whale').dataset.emote)}pet.brain.action('idle');pet.v3Cooldown=0;return out});
 for(let i=1;i<emotes.length;i++)assert.notEqual(emotes[i],emotes[i-1]);assert.equal(new Set(emotes.slice(0,6)).size,6);checks.push('六种大肥鱼表情实际触发且不连续重复');
 assert.equal(await p.evaluate(()=>gamePet3D.renderer.running),false);
 assert.equal(await p.evaluate(()=>[...document.querySelectorAll('.pet3d-original-video')].every(v=>v.paused)),true);checks.push('大肥鱼模式不播放隐藏视频');
 await p.mouse.move(10,110);await p.locator('#pet3d-launcher').click();
 await p.locator('[data-appearance="original"]:is(button)').click();await p.waitForTimeout(300);
 assert.equal(await p.locator('#pet3d-widget').getAttribute('data-appearance'),'original');
 await p.reload();await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready&&window.gamePet3D.v3Installed);
 assert.equal(await p.locator('#pet3d-widget').getAttribute('data-appearance'),'original');checks.push('原版搭子可切换并保存选择');
 await p.locator('#pet3d-launcher').click();await p.locator('button[data-appearance="whale"]').click();
 await p.locator('#pet3d-random').click();assert.equal(await p.locator('#pet3d-random').isDisabled(),true);
 assert.ok(await p.locator('#pet3d-whale').getAttribute('data-emote'));checks.push('随机按钮可以互动且限制连点');
 await p.locator('#pet3d-paused').check();assert.equal(await p.locator('#pet3d-widget').getAttribute('data-paused'),'true');
 assert.equal(await p.locator('#pet3d-random').isDisabled(),true);await p.locator('#pet3d-paused').uncheck();
 await p.locator('#pet3d-close').click();await p.locator('#motion-toggle').click();await p.waitForTimeout(100);
 assert.equal(await p.locator('html').getAttribute('data-motion'),'reduced');
 assert.equal(await cat.getAttribute('data-near'),null);
 const animations=await p.locator('#pet3d-whale .whale-float').evaluate(el=>getComputedStyle(el).animationName);assert.equal(animations,'none');
 await p.locator('#motion-toggle').click();await p.emulateMedia({reducedMotion:'reduce'});await p.waitForTimeout(100);
 assert.equal(await p.locator('html').getAttribute('data-motion'),'reduced');checks.push('暂停、手动与系统减少动画生效');await p.emulateMedia({reducedMotion:'no-preference'});
 await p.locator('#btn-truth').click();await p.waitForTimeout(200);assert.ok(await p.locator('#question-text').innerText());
 await p.locator('#btn-next').click();await p.locator('#btn-quick-complete').click();await p.locator('#btn-dare').click();await p.locator('#btn-back').click();
 await p.locator('#nav-bank').click();assert.equal(await p.locator('#stat-total').innerText(),'100');
 await p.locator('#nav-agent').click();await p.locator('#agent-input').fill('统计');await p.locator('#agent-send').click();
 await p.locator('#nav-game').click();checks.push('抽题、换题、完成、返回、题库与助手可用');
 await p.setViewportSize({width:390,height:844});await p.waitForTimeout(200);
 assert.equal(await p.evaluate(()=>document.documentElement.scrollWidth>innerWidth),false);
 await p.screenshot({path:'/workspace/output/v3-preview-mobile.png',fullPage:true});checks.push('390px手机布局无横向溢出');
 await p.setViewportSize({width:1280,height:940});await p.waitForTimeout(200);
 await p.evaluate(()=>{gamePet3D.brain.action('idle');gamePet3D.v3Cooldown=0});
 // Place fish in clear space, then drag through the existing hit target.
 await p.evaluate(()=>{gamePet3D.brain.x=760;gamePet3D.brain.y=440;gamePet3D.wake()});await p.waitForTimeout(150);
 const hit=p.locator('#pet3d-hit');const h=await hit.boundingBox();
 const start=await p.evaluate(()=>({x:gamePet3D.brain.x,y:gamePet3D.brain.y}));
 await p.mouse.move(h.x+h.width*.5,h.y+h.height*.6);await p.mouse.down();await p.mouse.move(h.x+h.width*.5+65,h.y+h.height*.6+35,{steps:8});await p.mouse.up();
 const end=await p.evaluate(()=>({x:gamePet3D.brain.x,y:gamePet3D.brain.y,drag:gamePet3D.drag}));assert.ok(Math.hypot(end.x-start.x,end.y-start.y)>20);assert.equal(end.drag,null);checks.push('大肥鱼可拖动且释放后清除拖动状态');
 assert.deepEqual(errors,[]);checks.push('无 JavaScript 运行错误');
 console.log(JSON.stringify({checks,draws,emotes,pageErrors:errors},null,2));await b.close();
})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 11. `/tmp/v3-extra.cjs`

~~~~~~~~~~
const {chromium}=require('playwright'),assert=require('node:assert/strict'),fs=require('node:fs');
(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});
const ctx=await b.newContext({viewport:{width:390,height:844},isMobile:true,hasTouch:true});const p=await ctx.newPage();const errors=[];p.on('pageerror',e=>errors.push(e.message));
await p.goto('http://127.0.0.1:8766/output/truth-or-dare-v3.html');await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);await p.locator('#btn-dare').tap();assert.ok(await p.locator('#question-text').innerText());await p.locator('#btn-back').tap();await p.locator('#pet3d-launcher').tap();await p.locator('#pet3d-random').tap();assert.ok(await p.locator('#pet3d-whale').getAttribute('data-emote'));assert.deepEqual(errors,[]);
await p.locator('#pet3d-close').tap();await p.setViewportSize({width:320,height:780});await p.waitForTimeout(100);assert.equal(await p.evaluate(()=>document.documentElement.scrollWidth>innerWidth),false);
// Serve only the HTML from memory, fail every other request: local CSS/JS/media must suffice.
const offline=await b.newPage();const html=fs.readFileSync('/workspace/output/truth-or-dare-v3.html','utf8');const external=[];
await offline.route('**/*',r=>{if(r.request().isNavigationRequest())return r.fulfill({status:200,contentType:'text/html',body:html});external.push(r.request().url());return r.abort()});
await offline.goto('http://local-preview.invalid');await offline.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);await offline.locator('#btn-truth').click();assert.ok(await offline.locator('#question-text').innerText());assert.deepEqual(external,[]);
console.log(JSON.stringify({checks:['手机触摸抽题与随机互动','320px窄屏无溢出','独立HTML无需外部网络请求'],pageErrors:errors}));await b.close()})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 12. `/tmp/eye-check.cjs`

~~~~~~~~~~
const {chromium}=require('playwright');(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});const p=await b.newPage({viewport:{width:1280,height:940}});await p.goto('http://127.0.0.1:8766/output/truth-or-dare-v3.html');await p.waitForTimeout(200);await p.locator('#btn-truth .choice-pet').evaluate(el=>{el.dataset.reaction='smile';el.dataset.near='true';el.style.setProperty('--pet-tilt','15deg')});await p.locator('#btn-truth').screenshot({path:'/tmp/smile-check.png'});await b.close()})()
~~~~~~~~~~

## 13. `/tmp/visual-verify.cjs`

~~~~~~~~~~
const {chromium}=require('playwright'),assert=require('node:assert/strict');
(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});const p=await b.newPage({viewport:{width:1280,height:940}});await p.goto('http://127.0.0.1:8766/output/truth-or-dare-v3.html');await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);await p.addStyleTag({content:'*{animation:none!important;transition:none!important}'});
const el=p.locator('#btn-truth .choice-pet');await el.screenshot({path:'/tmp/eyes-open.png'});await el.evaluate(e=>e.dataset.reaction='smile');await el.screenshot({path:'/tmp/eyes-smile.png'});
const whale=p.locator('#pet3d-whale');await whale.evaluate(e=>e.dataset.emote='wink');await whale.screenshot({path:'/tmp/whale-wink.png'});
await p.setViewportSize({width:390,height:844});await p.waitForTimeout(200);await p.screenshot({path:'/workspace/output/v3-preview-mobile.png',fullPage:true});
console.log('Visual states captured');await b.close()})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 14. `/workspace/output/watercolor-edition/DESIGN.md`

~~~~~~~~~~
---
version: alpha
name: "今晚，慢慢靠近"
description: "以水彩猫狗插画为主角的离线真心话大冒险"
colors:
  primary: "#3D6254"
  background: "#F5F7F3"
  surface: "#FFFFFF"
  ink: "#293D35"
  muted: "#66736A"
  border: "#DCE4DA"
  truth: "#EDF3E9"
  dare: "#FFF3E2"
  dareInk: "#80551E"
  danger: "#A63D49"
  scrollbar: "#A4B6A7"
typography:
  sans:
    fontFamily: '"PingFang SC", "Microsoft YaHei", "Noto Sans CJK SC", system-ui, sans-serif'
    fontSize: "15px"
    lineHeight: "1.7"
  display:
    fontFamily: '"PingFang SC", "Microsoft YaHei", "Noto Sans CJK SC", system-ui, sans-serif'
    fontSize: "44px"
    lineHeight: "1.3"
rounded:
  DEFAULT: "12px"
  panel: "24px"
  card: "20px"
spacing:
  section: "28px"
  control: "12px"
  page: "1180px"
components:
  button: {}
  field: {}
  choice: {}
  confirmation: {}
---

# 今晚，慢慢靠近

## Overview

A small Chinese-language, offline game for two people or a group of friends. The user supplied a watercolor cat/dog reference and a blue-haired desktop character. These are the visual brief; no PRD, server API, permissions, billing, or other business policy exists in this standalone project. The existing 100-question game, command helper, turn-taking and local question bank remain the behavioral baseline.

The North Star is an illustrated notebook opened together: watercolor gray-tabby kitten and golden puppy, mist-colored paper, leafy green ink and honey-colored challenge cards. The signature is the affectionate cat resting on a sleepy puppy in the header. Utility screens stay quiet and familiar. Restore the upstream blue-haired character as the only floating pet; no whale appearance.

Audience: Chinese-reading users on desktop and phone; locale zh-CN. This is a product/tool register, with no Japan-market requirement. The product contains no cloud sync. Do not promise cross-device storage.

Runtime ownership is Model B: `src/truth-or-dare-watercolor.html` owns the CSS tokens. This document mirrors their accepted values. The standalone release copies this source verbatim; no build-time or network dependency.

## Colors

Primary green is for actions, navigation, focus, and true/false state paired with text. Sage identifies truth; honey identifies dares. Red is limited to destructive actions and validation. White surfaces sit on pale green-gray paper. Warmth comes from the user's animal reference, not from a generic beige/serif theme. Light theme only. Forced colors use system colors.

## Typography

One unified Chinese-capable sans family for all UI, including pet settings. Display changes only size and weight. Body 15px / 1.7; controls at least 14px; annotations at least 12px. No font downloads or swap-induced shifts. Numbers use tabular figures. Technical command samples retain the same family for consistency with the user's request.

## Layout

1180px maximum page width; desktop game uses a flexible main column plus a 282px companion column. At 900px the sidebar moves beneath; at 600px header navigation takes its own row. At 350px card spacing and imagery shrink together. Page owns vertical scrolling; the question list, chat, and pet settings own bounded secondary scrollers. Fixed-size SVG view boxes reserve all artwork geometry. Never add a page-level viewport height or hide page overflow to fit a panel.

## Elevation & Depth

Panels use a subtle green-tinted shadow and a 1px boundary. Choice cards lift by 3px on hover. No stacked block shadows, glossy blue gradients, or full-screen ambient animation. Fixed pet and non-modal settings sit above the page but yield hit testing to controls. On small screens the floating character hides when it would cover reading content.

## Shapes

Panel radius 24px, choice radius 20px, standard control radius 12px. Preserve native select affordances; their OS-owned popups are an intentional exception. Rounded watercolor silhouettes carry expression; do not redraw them as shiny vector animals.

## Components

### Runtime token mapping

| DESIGN token | Runtime owner | Consumers |
|---|---|---|
| primary | --mint-deep / --primary | primary buttons, focus, navigation |
| background | --paper | document and header |
| surface | --white | panels and fields |
| ink / muted / border | --ink / --muted / --line | all screens |
| truth / dare / dareInk | --mint / --apricot / --orange-deep | choice cards and badges |
| danger | --color-danger | delete, error, confirmation |
| scrollbar | --scroll-thumb | global standard and engine scrollbar rules |
| sans / display | --font, --text-display | body and heading |

### Foundational visual states

All buttons have native semantics and explicit hover, pressed, focus-visible, and disabled treatments. `GameActions` owns static action dispatch and registers the same native button handlers for keyboard and pointer. Inputs retain values on invalid submit and expose associated inline errors. Busy/asynchronous dialogs keep button geometry stable.

The native `<dialog>` primitive owns delete confirmation, Escape, initial cancel focus, background isolation, and restored focus. The pet settings are a non-modal dialog and do not trap focus. A fixed shared toast acknowledges routine actions; storage errors and field errors also remain visible in context.

### Forms, search and lists

Native selects intentionally allow OS popup styling. All forms declare `novalidate`. Search is local, composition-safe, and has an explicit clear button; private game content is not persisted in a shareable URL. Bank renders the local dataset in a bounded scroller; no remote paging exists. Clear, tab switches, and errors preserve the search field and list geometry. Global scrollbars inherit tokens with standard properties, WebKit fallback, and a forced-colors path.

### Motion

Watercolor artwork reacts through small rotation, float, and squash transformations. Do not synthesize vector expressions over the supplied faces. Nearby pointer range 64px, exit hysteresis 84px, cooldown 2300ms. Touch and card focus receive the same reaction. Only the existing original character decodes embedded media, with at most two decoder slots. Random actions use a shuffled bag without consecutive repeats. Reduced motion and hidden-page state cancel supplemental reactions.

### Content

Short Chinese action labels describe the result: 抽题、换一题、完成了、删除题目、清空搜索. Do not expose implementation jargon in game copy. Keep original upstream attribution and media terms.

## Do's and Don'ts

- Do preserve the original character and watercolor animal identities.
- Do use one token and behavior system for game, helper, bank, dialogs, and pet settings.
- Don't promise that local browser data syncs across computers.
- Don't sacrifice text contrast or focus visibility for muted colors.
~~~~~~~~~~

## 15. `/workspace/output/watercolor-edition/UX-CONTRACT.md`

~~~~~~~~~~
# Behavioral contract

The current user request and the prior standalone HTML are the product evidence. No remote API, user identity, billing, or legal workflow exists. Local storage is best effort; in-memory operation remains available if it fails. Deletion permanently removes one local question only after app-owned confirmation. These choices preserve the existing product scope.

## Canonical UI Map

| Capability | Canonical owner | Source of truth | Allowed variants | Verification |
|---|---|---|---|---|
| Select/Listbox | Native select | DESIGN.md and current HTML | native OS popup | browser keyboard and open popup |
| Form | UI.handleAdd and shared field error | current HTML | local add and local search | invalid, valid, clear and IME |
| Scrollbar | Global application stylesheet | DESIGN.md | bounded chat/list/settings geometry | computed standard properties |
| Toast | UI.showToast | current HTML | success, info, error | live region and fixed placement |
| CRUD | QuestionService and UI.initBank | existing local-data service | read, create, confirm-delete | create-search-cancel-delete-reload |

## Shared flows

- Tabs are a native-button tablist with arrow/Home/End focus navigation. All three panels share fonts, buttons and feedback. Document title follows the selected panel.
- Quick draw: choose type → show question → complete increments count and returns to choice;换一题 keeps type;返回选择 does not record completion.
- Session: enter at least two names → begin → draw → complete or skip → next player; end keeps the history summary defined by the existing implementation.
- Adding: empty text produces an associated inline error and focuses the field; success preserves bank context and clears only committed fields. No confirmation for reversible input.
- Search: local and immediate on explicit submit/clear; no submission while Chinese IME is composing. Search state stays in memory because it can contain private relationship content; no query-string persistence.
- Delete: read the exact question in a native dialog; initial focus on Cancel; Escape/cancel restores the triggering button; delete updates count and results and focuses the search field.
- Storage failure: continue in memory, retain field contents on validation failure, and show a persistent notice that changes will not survive closing the page.
- Motion: pointer proximity, keyboard focus and touch are alternate triggers. Reduced motion cancels supplemental animation. A recenter button is the non-drag position alternative; hiding and pausing are preserved.
- Author attribution links remain visible. Original media terms remain embedded.
~~~~~~~~~~

## 16. `/workspace/output/watercolor-edition/premium-ui.json`

~~~~~~~~~~
{
 "profile":"product-admin",
 "sourceRoots":["src"],
 "locale":"zh-CN",
 "canonicalMap":"UX-CONTRACT.md",
 "requiredCapabilities":["Select/Listbox","Form","Scrollbar","Toast","CRUD"],
 "ownership":{"Select/Listbox":"native"},
 "requiredCommands":["browser"],
 "commands":{"browser":"node tests/verify.cjs"},
 "evidence":{"crudFullFlow":"tests/verify.cjs","failurePaths":"tests/verify.cjs"}
}
~~~~~~~~~~

## 17. `/tmp/watercolor.css`

~~~~~~~~~~
/* Watercolor product system. Values are owned here and mirrored in DESIGN.md. */
:root{--ink:#293D35;--muted:#66736A;--paper:#F5F7F3;--line:#DCE4DA;--mint:#EDF3E9;--mint-deep:#3D6254;--primary:var(--mint-deep);--apricot:#FFF3E2;--orange-deep:#80551E;--lilac:#EEF2EC;--blue:var(--mint);--white:#FFFFFF;--color-danger:#A63D49;--scroll-thumb:#A4B6A7;--scroll-track:#F0F3ED;--scroll-hover:#7C9583;--scroll-active:#3D6254;--radius-control:12px;--radius-panel:24px;--text-display:44px;--font:"PingFang SC","Microsoft YaHei","Noto Sans CJK SC",system-ui,sans-serif}
html{scrollbar-gutter:stable;-webkit-text-size-adjust:100%}
*{scrollbar-color:var(--scroll-thumb) var(--scroll-track);scrollbar-width:thin}
*::-webkit-scrollbar{width:9px;height:9px}
*::-webkit-scrollbar-track{background:var(--scroll-track)}
*::-webkit-scrollbar-thumb{background:var(--scroll-thumb);border:2px solid var(--scroll-track);border-radius:8px}
*::-webkit-scrollbar-thumb:hover{background:var(--scroll-hover)}
*::-webkit-scrollbar-thumb:active{background:var(--scroll-active)}
body{font-size:15px;line-height:1.7;-webkit-font-smoothing:antialiased;text-rendering:optimizeLegibility}
body,button,input,textarea,select,code{font-family:var(--font)}
button,input,select,textarea{line-height:1.5}
button{transition:background .18s,border-color .18s,box-shadow .18s,transform .18s}
button:focus-visible,a:focus-visible,input:focus-visible,select:focus-visible,summary:focus-visible,[tabindex]:focus-visible{outline:3px solid var(--primary);outline-offset:4px}
button:active:not(:disabled){transform:translateY(1px)}
button:disabled{cursor:not-allowed;opacity:.45;box-shadow:none}
a{color:var(--primary);text-underline-offset:4px}
h1,h2,h3,h4{font-weight:700;letter-spacing:0}
.app-header{background:var(--paper);border-color:var(--line)}
.header-content{max-width:1180px;padding:21px 30px;gap:24px}
.logo-icon{background:var(--mint);color:var(--primary);border-radius:14px;transform:rotate(-5deg);width:42px;height:42px}
.logo-text{font-size:18px;letter-spacing:0;font-weight:700}
.logo-note{font-size:11px;letter-spacing:2px;color:var(--muted)}
.nav-tabs{gap:6px}
.nav-tab{border-radius:10px;padding:11px 19px;font-size:14px}
.nav-tab.active{background:var(--white);box-shadow:0 1px 4px #293D3510;color:var(--primary)}
.motion-toggle{min-height:38px;border-color:var(--line);background:var(--white);font-size:12px}
.motion-dot{background:var(--primary)}
.app-main{max-width:1180px;padding:30px 30px 24px}
.hero{gap:36px;min-height:185px;padding-bottom:25px}
.hero-label{font-size:12px;color:var(--primary);letter-spacing:1px;margin-bottom:13px}
.hero h2{font-size:clamp(30px,3.5vw,var(--text-display));font-weight:700;letter-spacing:-.04em;line-height:1.3}
.hero h2 em{font-style:normal;color:var(--primary)}
.hero p{font-size:14px;line-height:1.8;margin-top:13px}
.hero-note{width:280px;flex-shrink:0;margin:0;transform:none;position:relative;display:flex;flex-direction:column;gap:0}
.hero-note .hero-art{width:235px;height:140px;color:inherit}
.hero-note p{font-size:11px;letter-spacing:2px;margin:0;color:var(--muted)}
.game-layout{grid-template-columns:minmax(0,1fr) 282px;gap:26px}
.game-container,.agent-container,.bank-container{border:1px solid var(--line);background:var(--white);border-radius:var(--radius-panel);box-shadow:0 8px 28px #293D3505}
.game-container{padding:24px 28px 20px}
.game-mode-bar{padding-bottom:20px;border-color:var(--line)}
.mode-selector{border-radius:11px;background:var(--paper);padding:4px}
.mode-btn{font-size:13px;padding:9px 15px;border-radius:8px}
.mode-btn.active{background:var(--primary);box-shadow:none;color:var(--white)}
.round-counter{font-size:12px}
.stage-heading{margin:23px 0 20px}
.stage-heading h3{font-size:20px;letter-spacing:0}
.stage-heading p{font-size:12px;margin-top:6px}
.choice-area{gap:20px;padding-bottom:0;perspective:none}
.choice-btn{padding:18px 20px 22px;border-radius:20px;box-shadow:none;transform-style:flat;border:1px solid var(--card-edge);overflow:visible}
.choice-truth{background:var(--mint);--card-edge:#CDDCC6;--pet-color:var(--primary)}
.choice-dare{background:var(--apricot);--card-edge:#EAD8BA;--pet-color:var(--orange-deep)}
.card-index{letter-spacing:.5px;font-size:11px;font-weight:500}
.card-mark{width:19px;height:19px;top:18px;right:18px}
.choice-pet{width:100%;height:182px;margin:6px 0 15px;transform:none;overflow:visible;transform-origin:50% 90%}
.choice-label{font-size:25px;font-weight:700;letter-spacing:0}
.choice-sublabel{font-size:12px;color:var(--muted);margin-top:6px}
.card-arrow{right:18px;bottom:24px;width:30px;height:30px;font-size:17px;border-color:var(--card-edge);background:var(--white)}
.random-btn{margin-top:21px;padding:10px 16px;min-height:40px;font-size:12px;color:var(--primary);border-radius:10px}
.stage-footer{width:100%;border-top:1px dashed var(--line);font-size:11px;line-height:1.8;margin-top:18px;padding-top:15px}
.game-sidebar{gap:24px}
.buddy-room{background:var(--lilac);border:1px solid var(--line);border-radius:var(--radius-panel);padding:21px 19px 18px}
.buddy-title h3{font-size:14px}
.buddy-title span{background:var(--white);color:var(--muted);font-size:10px}
.buddy-scene{height:151px;margin-top:12px}
.buddy-floor{display:none}
.buddy-pet{width:136px;height:143px;bottom:0;transform-origin:50% 90%;overflow:visible}
.buddy-cat{left:-5px;transform:rotate(-3deg)}
.buddy-dog{right:-6px;transform:rotate(3deg)}
.scene-star{font-size:21px;color:#B56A76;right:10px;top:6px}
.buddy-speech{color:var(--ink);background:var(--white);font-size:12px;line-height:1.8;min-height:72px;border-radius:14px;margin-top:15px;padding:13px 11px}
.buddy-speech::before{background:var(--white)}
.buddy-names{font-size:11px;color:var(--muted);margin-top:12px}
.play-guide{padding:0 6px}
.play-guide h3{font-size:14px;margin-bottom:13px}
.play-guide li{font-size:12px;line-height:1.7}
.guide-dot{background:var(--mint);color:var(--primary)}
.bank-preview{font-size:11px;padding-top:16px;margin-top:17px;border-color:var(--line)}
.bank-preview svg{color:var(--primary);width:18px;height:18px}
.question-card{background:var(--mint);border:1px solid #CDDCC6;box-shadow:none;border-radius:20px;min-height:290px;padding:25px}
.question-card[data-type="dare"]{background:var(--apricot);border-color:#EAD8BA;box-shadow:none}
.question-topline{margin-bottom:27px}
.question-pet{width:49px;height:49px;overflow:visible}
.question-type-badge,.history-item-type,.list-item-type{background:var(--mint);color:var(--primary)}
.question-type-badge.dare,.history-item-type.dare,.list-item-type.dare{background:var(--apricot);color:var(--orange-deep)}
.question-text{font-size:clamp(20px,2.3vw,25px);line-height:1.85;font-weight:600}
.question-tag{font-size:11px;border-color:var(--line);color:var(--muted)}
.question-actions{gap:10px}
.action-btn,.agent-send,.search-btn{border-radius:var(--radius-control);padding:12px 19px;font-size:13px;min-height:44px;box-shadow:none}
.btn-next,.btn-start-session,.btn-add,.agent-send,.search-btn,.btn-complete{background:var(--primary);color:var(--white);box-shadow:none}
.btn-back,.btn-add-player{background:var(--paper);color:var(--ink);border:1px solid var(--line)}
.btn-end-session{background:#F9ECEE;color:var(--color-danger)}
.section-title{font-size:22px;letter-spacing:0;font-weight:700}
.section-desc{font-size:13px;line-height:1.8}
input,select{font-size:14px;min-height:44px;border:1px solid #B6C7BA;border-radius:var(--radius-control);color:var(--ink);background:var(--white)}
input::placeholder{color:#748076}
input[aria-invalid="true"]{border-color:var(--color-danger)}
.field-error{font-size:12px;color:var(--color-danger);margin-top:9px;min-height:20px}
.session-info{background:var(--paper);border-radius:14px}
.player-name{font-size:22px;font-weight:700}
.remove-player{width:40px;height:40px;min-height:40px;background:var(--paper);border:1px solid var(--line);border-radius:10px}
.choice-btn.btn-sm{box-shadow:none;padding:14px 16px;border-radius:12px}
.history-item{border-color:var(--line)}
.agent-container{max-width:850px;gap:22px;padding:30px}
.agent-avatar{width:75px;height:75px;overflow:visible;background:var(--mint);padding:3px;border-radius:18px}
.quick-cmd{background:var(--white);border-color:var(--line);font-size:12px;min-height:40px;border-radius:10px}
.agent-chat{background:var(--paper);padding:22px;border-radius:18px;min-height:280px;max-height:440px;scrollbar-gutter:stable}
.message-content{font-size:14px;line-height:1.8;border-color:var(--line);background:var(--white)}
.chat-message.user .message-content{background:var(--primary);border-color:var(--primary);color:var(--white)}
.chat-message.agent .message-content{background:var(--mint);border-color:#CDDCC6}
.intent-badge{color:var(--primary);font-size:11px}
.agent-input-area{gap:10px}
.agent-input{min-width:0}
.api-info{font-size:12px}
.api-info-content{background:var(--paper);padding:15px;border-radius:12px}
.api-info summary{min-height:40px}
code{background:var(--mint);font-size:12px}
.bank-container{padding:28px;gap:22px}
.bank-heading{align-items:start}
.storage-note{font-size:11px;max-width:240px;text-align:right}
.storage-note[data-error="true"]{color:var(--color-danger);font-weight:600}
.stats-dashboard{background:var(--paper);border-color:var(--line);border-radius:14px}
.stat-card{padding:16px 20px;border-color:var(--line)}
.stat-value{font-size:27px;font-weight:600}
.stat-truth .stat-value{color:var(--primary)}
.stat-dare .stat-value{color:var(--orange-deep)}
.stat-label{font-size:11px}
.add-question-section{background:var(--paper);border-radius:16px;padding:20px}
.add-question-section h3{font-size:14px}
.add-form{grid-template-columns:110px minmax(0,1fr) 165px auto;gap:10px;margin-top:13px;align-items:start}
.search-section{gap:20px}
.search-bar{max-width:520px}
.search-field{flex:1;position:relative;min-width:0}
.search-field input{width:100%;padding-right:42px}
.clear-search{position:absolute;right:4px;top:4px;width:36px;height:36px;display:grid;place-items:center;border-radius:9px;background:var(--paper);color:var(--muted);font-size:18px}
.filter-tab{border-radius:10px;min-height:40px}
.filter-tab.active{background:var(--mint);color:var(--primary)}
.question-list{max-height:560px;overflow-y:auto;scrollbar-gutter:stable;overscroll-behavior:contain}
.list-item{border-color:var(--line);padding:17px 6px;gap:13px;align-items:start}
.list-item-text{font-size:14px;line-height:1.85}
.list-item-meta{font-size:11px;gap:10px;margin-top:5px}
.list-item-type{font-size:11px;padding:5px 8px;border-radius:7px;white-space:nowrap}
.list-item-btn{color:var(--color-danger);background:#F9ECEE;font-size:12px;min-height:40px;padding:9px 13px;border-radius:10px}
.empty-state{min-height:180px;display:grid;place-items:center;color:var(--muted);font-size:14px}
.app-footer{border-top:1px solid var(--line);padding:22px 145px 0 0;margin-top:30px;font-size:11px;line-height:1.9}
.asset-credit{color:var(--primary)}
.toast{background:var(--primary);color:var(--white);font-size:13px;border-radius:12px;line-height:1.7;z-index:110}
.toast.error{background:var(--color-danger)}
.game-confirm{padding:26px;border:1px solid var(--line);border-radius:22px;max-width:min(460px,calc(100vw - 32px));width:460px;color:var(--ink);background:var(--white);box-shadow:0 24px 80px #293D3526}
.game-confirm::backdrop{background:#293D3555}
.game-confirm h2{font-size:20px;margin:0 0 12px}
.game-confirm p{font-size:14px;line-height:1.8;color:var(--muted)}
.game-confirm blockquote{margin:16px 0 22px;padding:14px 16px;background:var(--paper);border-left:3px solid var(--line);font-size:14px;line-height:1.9;max-height:180px;overflow:auto;overflow-wrap:anywhere}
.confirm-actions{display:flex;justify-content:flex-end;gap:10px}
.confirm-delete{background:var(--color-danger);color:var(--white)}
.confirm-cancel{background:var(--paper);border:1px solid var(--line)}
.pet3d-panel{font-family:var(--font);color:var(--ink);background:var(--white);border-color:var(--line);border-radius:22px;box-shadow:0 14px 45px #293D3520}
.pet3d-panel h2{letter-spacing:0}
.pet3d-panel p,.pet3d-slider output,.pet3d-status,.pet3d-stats{color:var(--muted)}
.pet3d-close,.pet3d-variant,.pet3d-action,.pet3d-random,.pet3d-bottom button{background:var(--paper);color:var(--primary);border-color:var(--line);border-radius:10px;min-height:38px}
.pet3d-variant[aria-pressed="true"]{background:var(--mint);border-color:#B6C7BA;color:var(--primary)}
.pet3d-options{border-color:var(--line)}
.pet3d-check input,.pet3d-slider input{accent-color:var(--primary)}
.pet3d-launcher{font-family:var(--font);background:var(--primary);box-shadow:0 4px 16px #293D3520;color:var(--white);border:1px solid var(--white)}
.pet3d-bubble{font-family:var(--font);color:var(--ink);border-color:var(--line);background:var(--white)}
.pet3d-random{width:100%;font-size:12px;margin:9px 0;padding:10px;background:var(--mint)}
.watercolor-pet{transform:var(--watercolor-lean,none);transform-origin:100px 184px;animation:var(--watercolor-motion,none);transition:transform .28s ease-out}
svg[data-near="true"]{--watercolor-lean:translate(var(--pet-lean,0px),-2px) rotate(var(--pet-tilt,0deg))}
svg[data-reaction="rock"]{--watercolor-motion:watercolor-rock 900ms ease-in-out}
svg[data-reaction="bounce"]{--watercolor-motion:watercolor-bounce 850ms ease-in-out}
svg[data-reaction="greet"]{--watercolor-motion:watercolor-greet 1000ms ease-in-out}
@keyframes watercolor-rock{0%,100%{transform:rotate(0)}28%{transform:rotate(-5deg)}70%{transform:rotate(5deg)}}
@keyframes watercolor-bounce{0%,100%{transform:translateY(0)}30%{transform:translateY(2px) scale(1.02,.98)}60%{transform:translateY(-7px)}85%{transform:translateY(0)}}
@keyframes watercolor-greet{0%,100%{transform:rotate(0)}35%{transform:translateY(-3px) rotate(4deg)}65%{transform:translateY(-3px) rotate(-3deg)}}
/* Accessibility overrides intentionally win over all legacy media/motion rules. */
html[data-motion="reduced"] .watercolor-pet{animation:none!important;transform:none!important;transition:none!important}
html[data-pet-visibility="hidden"] .watercolor-pet{animation-play-state:paused}
@media(hover:hover) and (pointer:fine){
 .nav-tab:hover,.quick-cmd:hover,.filter-tab:hover,.mode-btn:not(.active):hover,.btn-back:hover,.btn-add-player:hover,.clear-search:hover,.motion-toggle:hover{background:var(--mint)}
 .choice-btn:hover:not(:disabled){transform:translateY(-3px);box-shadow:0 7px 18px #293D350A}
 .btn-next:hover,.btn-start-session:hover,.btn-add:hover,.agent-send:hover,.search-btn:hover,.btn-complete:hover,.pet3d-launcher:hover{background:#304F43;transform:translateY(-1px)}
 .list-item-btn:hover,.confirm-delete:hover{background:#92333E;color:var(--white)}
 .pet3d-panel button:hover,.random-btn:hover{background:var(--mint)}
 .pet3d-panel .pet3d-variant[data-pet3d-variant=lilac]:hover{background:var(--apricot)}
}
@media(max-width:1050px){.add-form{grid-template-columns:110px minmax(0,1fr) auto}.add-tags{grid-column:2}.btn-add{grid-column:3;grid-row:1/3;align-self:stretch}}
@media(max-width:900px){.game-layout{grid-template-columns:1fr}.game-sidebar{display:grid;grid-template-columns:1fr 1fr;align-items:center;gap:25px}.buddy-scene{height:135px}.buddy-pet{width:130px;height:135px}.hero-note{width:220px}.hero-note .hero-art{width:220px;height:125px}.nav-tab{padding-inline:14px}.header-content{gap:18px}.search-section{flex-wrap:wrap}.search-bar{max-width:none}}
@media(max-width:600px){
 .header-content{padding:16px 18px 12px;gap:12px;flex-wrap:wrap}.logo{gap:9px}.logo-text{font-size:16px}.logo-icon{width:36px;height:36px}.logo-note{font-size:10px;letter-spacing:1px}.motion-toggle{margin-left:auto;padding:8px 10px;font-size:11px;min-height:36px}.nav-tabs{order:3;width:100%;gap:6px;justify-content:space-between}.nav-tab{flex:1;max-width:none;padding:11px 10px;font-size:13px}
 .app-main{padding:25px 16px 20px}.hero{min-height:0;padding:0 0 25px;gap:10px}.hero-label{font-size:10px;margin-bottom:11px;letter-spacing:.3px}.hero-label svg{width:14px;height:14px}.hero h2{font-size:29px;letter-spacing:-.04em}.hero p{font-size:12px;margin-top:11px;max-width:25em}.hero-note{display:none}
 .game-container{padding:18px 15px 18px;border-radius:22px}.game-mode-bar{padding-bottom:16px}.mode-btn{font-size:12px;padding:8px 11px}.round-counter{font-size:10px}.stage-heading{margin:22px 0 20px}.stage-heading h3{font-size:17px}.stage-heading p{font-size:11px;margin-top:7px}.choice-area{gap:12px}.choice-btn{padding:15px 12px 20px;border-radius:17px}.card-index{font-size:10px;letter-spacing:0}.card-mark{width:16px;height:16px;top:15px;right:12px}.choice-pet{height:137px;margin:8px 0 13px}.choice-label{font-size:22px}.choice-sublabel{font-size:10px;max-width:12em;line-height:1.6}.card-arrow{width:23px;height:23px;font-size:14px;right:10px;bottom:25px}.random-btn{font-size:11px;margin-top:18px;padding:10px 8px}.stage-footer{font-size:10px;line-height:1.8;margin-top:15px;padding-top:13px}
 .game-sidebar{grid-template-columns:1fr;gap:22px}.buddy-room{display:grid;grid-template-columns:120px 1fr;gap:0 14px;padding:19px 17px}.buddy-title{grid-column:1/-1}.buddy-scene{grid-column:1;grid-row:2/4;height:104px;margin-top:10px}.buddy-pet{width:83px;height:101px}.buddy-cat{left:-10px}.buddy-dog{right:-9px}.scene-star{font-size:15px;right:4px;top:3px}.buddy-speech{grid-column:2;min-height:62px;font-size:11px;margin-top:13px;padding:10px}.buddy-speech::before{left:-5px;top:22px;width:10px;height:10px}.buddy-names{grid-column:2;font-size:10px;gap:16px}.play-guide{padding:0 5px}.bank-preview{font-size:11px}
 .question-card{padding:18px 16px;min-height:270px}.question-text{font-size:20px}.question-actions{gap:8px}.action-btn{padding:12px 14px;font-size:12px}.section-title{font-size:20px}.section-desc{font-size:12px}.agent-container,.bank-container{padding:21px 16px;border-radius:22px}.agent-container{gap:18px}.agent-avatar{width:59px;height:59px}.agent-header{gap:13px}.agent-chat{padding:15px;min-height:260px}.message-content{font-size:13px;padding:11px 13px}.chat-message{max-width:93%}.quick-cmd{padding:8px 10px;font-size:11px}.agent-send{padding-inline:15px}.agent-input{width:100%}
 .bank-heading{flex-direction:column;gap:10px}.storage-note{text-align:left;max-width:none}.stats-dashboard{grid-template-columns:repeat(4,minmax(0,1fr))}.stat-card{padding:14px 10px}.stat-value{font-size:24px}.stat-label{font-size:10px}.add-question-section{padding:16px}.add-form{grid-template-columns:1fr}.add-tags,.btn-add{grid-column:auto;grid-row:auto}.add-form .btn-add{width:100%}.search-section{gap:13px}.search-bar{width:100%;max-width:none}.filter-tabs{width:100%}.filter-tab{flex:1}.list-item{flex-wrap:wrap;gap:8px}.list-item-type{font-size:10px}.list-item-content{flex:1;min-width:0}.list-item-text{font-size:13px}.list-item-meta{font-size:10px}.list-item-btn{font-size:11px;padding:8px 10px;min-height:36px}.list-item-actions{margin-left:auto}.app-footer{flex-direction:column;text-align:center;padding:20px 0 0;margin-top:26px;font-size:10px;gap:8px}
 .game-confirm{padding:21px}.game-confirm blockquote{max-height:145px}.game-confirm h2{font-size:19px}.game-confirm p{font-size:13px}.pet3d-panel{max-height:calc(100dvh - 100px)}
}
@media(max-width:350px){.header-content{padding-inline:13px;gap:9px}.logo-text{font-size:15px}.logo-note{letter-spacing:0}.app-main{padding-inline:12px}.hero h2{font-size:27px}.choice-pet{height:119px}.choice-btn{padding-inline:10px}.choice-sublabel{font-size:9px}.card-index{font-size:9px}.choice-label{font-size:21px}.game-container{padding-inline:12px}.card-arrow{display:none}.stats-dashboard .stat-card{padding:12px 7px}}
@media(prefers-reduced-motion:reduce){.watercolor-pet{animation:none!important;transform:none!important;transition:none!important}}
@media(forced-colors:active){*{scrollbar-color:auto;forced-color-adjust:auto}*::-webkit-scrollbar-thumb{background:ButtonText}button,input,select,.game-container,.choice-btn,.game-confirm{border:1px solid ButtonText}:focus-visible{outline:3px solid Highlight}.toast{border:1px solid CanvasText}}
~~~~~~~~~~

## 18. `/tmp/watercolor-enhance.js`

~~~~~~~~~~
(()=>{
'use strict';
const dialog=document.querySelector('#delete-dialog');let resolveDelete=null,returnFocus=null;
window.askToDelete=question=>new Promise(resolve=>{
 if(dialog.open){resolve(false);return}
 returnFocus=document.activeElement;resolveDelete=resolve;
 document.querySelector('#delete-question').textContent=question;
 dialog.showModal();document.querySelector('#delete-cancel').focus();
});
function finishDelete(confirmed){
 const resolve=resolveDelete;resolveDelete=null;dialog.close();
 if(!confirmed&&returnFocus?.isConnected)returnFocus.focus({preventScroll:true});
 resolve?.(confirmed);
}
GameActions.register(document.querySelector('#delete-cancel'),()=>finishDelete(false));
GameActions.register(document.querySelector('#delete-commit'),()=>finishDelete(true));
dialog.addEventListener('cancel',e=>{e.preventDefault();finishDelete(false)});
const input=document.querySelector('#search-input'),clear=document.querySelector('#clear-search');
function updateClear(){clear.hidden=!input.value}
GameActions.register(clear,()=>{input.value='';clearTimeout(GameUI.searchTimer);GameUI.renderList();updateClear();input.focus()});
input.addEventListener('input',updateClear);input.addEventListener('compositionend',()=>{clearTimeout(GameUI.searchTimer);GameUI.renderList();updateClear()});
input.addEventListener('keydown',e=>{if(e.isComposing&&e.key==='Enter')e.preventDefault()});updateClear();
const addText=document.querySelector('#add-text'),addError=document.querySelector('#add-error');
addText.addEventListener('input',()=>{addError.hidden=true;addText.removeAttribute('aria-invalid')});
function storageNotice(){
 const note=document.querySelector('.storage-note');
 const ok=window.GameStorageHealthy!==false;note.dataset.error=String(!ok);
 note.textContent=ok?'题库保存在当前浏览器':'当前无法保存；新增和删除仅在本次打开期间有效。';
}
window.addEventListener('game:storage',storageNotice);storageNotice();
// Artwork reacts through transforms so the supplied watercolor faces remain intact.
const reduced=()=>matchMedia('(prefers-reduced-motion: reduce)').matches||document.documentElement.dataset.motion==='reduced';
const pets=[...document.querySelectorAll('svg')].filter(el=>el.querySelector('use[href="#cat-art"],use[href="#dog-art"]')).map(el=>({el,near:false,last:-Infinity,timer:0,lastChoice:-1}));
let pointer=null,frame=0,lastFrame=0;
function reset(s){clearTimeout(s.timer);s.near=false;delete s.el.dataset.near;delete s.el.dataset.reaction;s.el.style.removeProperty('--pet-lean');s.el.style.removeProperty('--pet-tilt')}
function react(s,now){if(reduced()||document.hidden||now-s.last<2300)return;s.last=now;let choice=Math.floor(Math.random()*2);if(choice>=s.lastChoice)choice++;s.lastChoice=choice;s.el.dataset.reaction=['rock','bounce','greet'][choice];clearTimeout(s.timer);s.timer=setTimeout(()=>delete s.el.dataset.reaction,1100)}
function drawPointer(now){
 frame=0;if(!pointer||reduced()||document.hidden)return;
 if(now-lastFrame<32){frame=requestAnimationFrame(drawPointer);return}lastFrame=now;
 const rects=pets.map(s=>s.el.getBoundingClientRect());
 pets.forEach((s,i)=>{
  const r=rects[i];if(!r.width||!r.height||r.bottom<0||r.top>innerHeight){if(s.near)reset(s);return}
  const dx=pointer.x-r.left-r.width/2,dy=pointer.y-r.top-r.height*.55;
  const distance=Math.hypot(Math.max(Math.abs(dx)-r.width*.36,0),Math.max(Math.abs(dy)-r.height*.4,0));
  if(distance<=(s.near?84:64)){
   if(!s.near){s.near=true;s.el.dataset.near='true';react(s,now)}
   s.el.style.setProperty('--pet-lean',Math.max(-2,Math.min(2,dx/60)).toFixed(1)+'px');
   s.el.style.setProperty('--pet-tilt',Math.max(-4,Math.min(4,dx/35)).toFixed(1)+'deg');
  }else if(s.near)reset(s);
 });
}
function schedule(){if(pointer&&!frame&&!reduced())frame=requestAnimationFrame(drawPointer)}
function stop(){pointer=null;cancelAnimationFrame(frame);frame=0;pets.forEach(reset)}
window.addEventListener('pointermove',e=>{if(e.pointerType==='touch')return;pointer={x:e.clientX,y:e.clientY};schedule()},{passive:true});
window.addEventListener('scroll',schedule,{passive:true});window.addEventListener('resize',schedule,{passive:true});
window.addEventListener('blur',stop);window.addEventListener('pointerout',e=>{if(!e.relatedTarget)stop()});
for(const s of pets){s.el.addEventListener('pointerdown',()=>react(s,performance.now()),{passive:true});s.el.closest('button')?.addEventListener('focus',()=>react(s,performance.now()))}
document.addEventListener('visibilitychange',()=>{document.documentElement.dataset.petVisibility=document.hidden?'hidden':'visible';if(document.hidden)stop()});
new MutationObserver(()=>{if(reduced())stop()}).observe(document.documentElement,{attributes:true,attributeFilter:['data-motion']});
// Keep only the upstream blue-haired original character. Random interaction shares its controller.
function installPet(){
 const pet=window.gamePet3D;if(!pet||pet.watercolorInstalled)return;pet.watercolorInstalled=true;
 const random=document.createElement('button');random.id='pet3d-random';random.className='pet3d-random';random.type='button';random.textContent='随机互动';
 document.querySelector('.pet3d-stats').before(random);
 pet.randomInteraction=()=>{if(!pet.diagnostics.ready||!pet.enabled||pet.paused||document.hidden||performance.now()<(pet.randomCooldown||0))return false;pet.randomCooldown=performance.now()+2200;return pet.trigger(pet.brain.nextInteraction())};
 random.addEventListener('click',()=>{pet.unlockAudio();pet.randomInteraction()});
 const sync=pet.syncControls.bind(pet);pet.syncControls=()=>{sync();random.disabled=!pet.enabled||pet.paused};
 const trigger=pet.trigger.bind(pet);pet.trigger=action=>{if(document.hidden)return false;return trigger(action)};
 // Keyboard arrows supply a direct non-drag positioning alternative, alongside recenter.
 document.querySelector('#pet3d-hit').addEventListener('keydown',e=>{
  const delta={ArrowLeft:[-16,0],ArrowRight:[16,0],ArrowUp:[0,-16],ArrowDown:[0,16]}[e.key];
  if(!delta||!pet.brain||!pet.enabled||pet.paused)return;e.preventDefault();pet.brain.action('idle');pet.brain.x+=delta[0];pet.brain.y+=delta[1];pet.brain.clampPosition();pet.wake();pet.scheduleSave();
 });
 sync();
}
if(document.readyState==='loading')document.addEventListener('DOMContentLoaded',installPet,{once:true});else installPet();
})();
~~~~~~~~~~

## 19. `/tmp/build_watercolor.py`

~~~~~~~~~~
from pathlib import Path
import re,base64
base=Path('/tmp/v3-base.html').read_text()
# Replace, rather than layer over, the prior added vector-upgrade stylesheet.
base=re.sub(r'<style id="companion-upgrade">.*?</style>','',base,flags=re.S)
# The media, core storage keys, and question bank are preserved byte for byte.
art=base64.b64encode(Path('/workspace/generated_images/exec-fe577d59-d0bf-435b-ac0f-47bd9e13f53f.png').read_bytes()).decode()
sheet=f'<image id="watercolor-sheet" href="data:image/png;base64,{art}" width="2073" height="758"/>'
for name,view in [('cat','25 130 550 580'),('dog','650 130 580 580')]:
 symbol=f'<symbol id="{name}-art" viewBox="0 0 200 200"><g class="watercolor-pet"><svg width="200" height="200" viewBox="{view}" preserveAspectRatio="xMidYMid meet"><use href="#watercolor-sheet"/></svg></g></symbol>'
 base=re.sub(fr'<symbol id="{name}-art".*?</symbol>',lambda m:symbol,base,flags=re.S)
base=base.replace('<defs>','<defs>'+sheet+'<symbol id="pair-art" viewBox="0 0 400 260"><svg width="400" height="260" viewBox="1305 120 768 590" preserveAspectRatio="xMidYMid meet"><use href="#watercolor-sheet"/></svg></symbol>',1)
# Remove unused blue vector paint definitions; keep semantic heart/paw icons.
base=re.sub(r'\s*<!-- Companion artwork:.*?(?=<symbol id="cat-art")','\n',base,flags=re.S)
# Palette remapping of legacy UI only (not the original upstream media).
first=re.search(r'<style>(.*?)</style>',base,re.S)
css=first.group(1)
color_map={'#263C6C':'var(--ink)','#687795':'var(--muted)','#F5F8FF':'var(--paper)','#DAE2F3':'var(--line)','#E2EBFF':'var(--mint)','#3C5FD5':'var(--primary)','#FCE4EC':'var(--apricot)','#A84F73':'var(--orange-deep)','#FFFFFF':'var(--white)','#F0ECFC':'var(--lilac)','#AF3448':'var(--color-danger)'}
# Root variable values are replaced by the canonical token block below; avoid circular definitions.
css=re.sub(r':root\s*\{.*?\}','',css,count=1,flags=re.S)
for a,b in color_map.items():css=css.replace(a,b)
css=':root{--color-text:var(--ink);--color-text-secondary:var(--muted);--color-text-light:var(--muted);--color-truth:var(--primary);--color-dare:var(--orange-deep);--color-surface:var(--white);--color-surface-alt:var(--paper);--color-success:var(--primary);--color-border:var(--line)}\n'+css
base=base[:first.start()]+'<style id="game-base">'+css+'</style>'+base[first.end():]
base=base.replace('#F5F8FF',' #F5F7F3',1)
base=base.replace('<h2>把心事，说给你听。</h2>','<h2>把心事，<em>说给你听。</em></h2>',1)
base=re.sub(r'<div class="hero-note".*?</div>', '<div class="hero-note" aria-hidden="true"><svg class="hero-art" viewBox="0 0 400 260"><use href="#pair-art"/></svg><p>慢慢聊，轻轻靠近。</p></div>',base,count=1,flags=re.S)
# App-owned confirmation and field/search states.
base=base.replace('<form class="add-form" id="add-form">','<form class="add-form" id="add-form" novalidate>')
base=base.replace('<form class="search-bar" id="search-form">','<form class="search-bar" id="search-form" novalidate>')
base=base.replace('id="add-text"','id="add-text" aria-describedby="add-error"',1)
base=base.replace('</form></div><div class="search-section">','</form><p class="field-error" id="add-error" role="alert" hidden></p></div><div class="search-section">',1)
base=re.sub(r'(<input[^>]*id="search-input"[^>]*>)',r'<div class="search-field">\1<button type="button" id="clear-search" class="clear-search" aria-label="清空搜索" hidden>×</button></div>',base,count=1)
base=base.replace('if (!confirm(\'确定删除这道题吗？\')) return;',"if (!await window.askToDelete(QuestionService.getById(btn.dataset.id)?.text || '这道题目')) return;")
base=base.replace("this.$('#question-list').addEventListener('click', e => {", "this.$('#question-list').addEventListener('click', async e => {")
base=base.replace("this.$('#search-input').addEventListener('input', () => { clearTimeout(this.searchTimer); this.searchTimer = setTimeout(() => this.renderList(), 120); });", "this.$('#search-input').addEventListener('input', e => { clearTimeout(this.searchTimer); if(e.isComposing)return; this.searchTimer = setTimeout(() => this.renderList(), 120); });")
base=base.replace("this.$('#search-form').addEventListener('submit', e => { e.preventDefault(); this.renderList(); });", "this.$('#search-form').addEventListener('submit', e => { e.preventDefault(); this.renderList(); });")
base=base.replace("if (!text) { this.showToast('先写下题目内容吧。', 'error'); this.focus('#add-text'); return; }", "if (!text) { const error=this.$('#add-error');error.textContent='请先写下题目内容，再点击添加。';error.hidden=false;this.$('#add-text').setAttribute('aria-invalid','true');this.focus('#add-text'); return; } this.$('#add-error').hidden=true;this.$('#add-text').removeAttribute('aria-invalid');")
# Explicit persistent failure information accompanies routine acknowledgements.
base=base.replace("localStorage.setItem(this.STORAGE_KEY, JSON.stringify(data));", "localStorage.setItem(this.STORAGE_KEY, JSON.stringify(data));window.GameStorageHealthy=true;window.dispatchEvent(new Event('game:storage'));")
base=base.replace("console.error('保存数据失败', e);", "window.GameStorageHealthy=false;window.dispatchEvent(new Event('game:storage'));")
base=base.replace("this.showToast('专属题目已添加', 'success')", "this.showToast(window.GameStorageHealthy===false?'专属题目已添加，仅本次打开有效':'专属题目已添加', 'success')")
base=base.replace("this.state.currentTab = name;", "this.state.currentTab = name;document.title=({game:'游戏桌',agent:'指令助手',bank:'我的题库'}[name]||'游戏桌')+' · 真心话大冒险';")
base=base.replace("QuestionService.delete(btn.dataset.id); this.loadBankData();", "QuestionService.delete(btn.dataset.id); this.loadBankData();")
# Bind static UI through an explicit shared native-button action registry.
script=re.search(r'<script>(.*?)</script>',base,re.S)
main=script.group(1)
main=re.sub(r"(this\.\$\('[^']+'\)|document\.querySelector\('[^']+'\)|tab|btn|remove)\.addEventListener\('click',\s*",r'GameActions.register(\1, ',main)
main=main.replace('  function init() {','  window.GameUI=UI;\n  function init() {')
base=base[:script.start()]+'<script>'+main+'</script>'+base[script.end():]
registry='''<script id="shared-actions">
window.GameActions=(()=>{const handlers=new WeakMap();return {register(el,handler){handlers.set(el,handler);if(!el.hasAttribute('onclick'))el.onclick=event=>this.handle(event)},handle(event){const el=event.currentTarget;if(el.disabled)return;return handlers.get(el)?.(event)}}})();
</script>'''
base=base.replace('<script>',registry+'\n<script>',1)
dialog='''<dialog id="delete-dialog" class="game-confirm" aria-labelledby="delete-title" aria-describedby="delete-description"><h2 id="delete-title">删除这道题目？</h2><p id="delete-description">删除后无法恢复。你也可以取消，继续保留这道题。</p><blockquote id="delete-question"></blockquote><div class="confirm-actions"><button type="button" class="action-btn confirm-cancel" id="delete-cancel">取消</button><button type="button" class="action-btn confirm-delete" id="delete-commit">删除题目</button></div></dialog>'''
base=base.replace(registry,dialog+'\n'+registry,1)
# Add real action dispatch attributes to literal buttons only, leaving embedded runtime templates untouched.
prefix,rest=base.split('<script id="shared-actions">',1)
def onclick(m):
 tag=m.group(0)
 if 'onclick=' not in tag:tag=tag[:-1]+' onclick="GameActions.handle(event)">'
 return tag
prefix=re.sub(r'<button\b[^>]*>',onclick,prefix)
base=prefix+'<script id="shared-actions">'+rest
# Clicking the upstream pet uses the shared random method with a cooldown.
base=base.replace('this.trigger(this.brain.nextInteraction())','this.randomInteraction()',2)
base=base.replace('&&!this.drag&&i>=(this.showPetUntil||0)', '&&!this.drag')
base=base.replace('</body>','<style id="watercolor-design">'+Path('/tmp/watercolor.css').read_text()+'</style><script id="watercolor-interactions">'+Path('/tmp/watercolor-enhance.js').read_text()+'</script></body>')
# Preserve standalone package and reviewable project source.
out=Path('/workspace/output/watercolor-edition/src/truth-or-dare-watercolor.html');out.write_text(base)
Path('/workspace/output/truth-or-dare-watercolor.html').write_text(base)
print('HTML bytes:',len(base.encode()))
~~~~~~~~~~

## 20. `/tmp/watercolor-preview.cjs`

~~~~~~~~~~
const {chromium}=require('playwright');
(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});const p=await b.newPage({viewport:{width:1280,height:1000}});const errors=[];p.on('pageerror',e=>errors.push(e.stack));await p.goto('http://127.0.0.1:8766/output/truth-or-dare-watercolor.html');await p.waitForTimeout(1500);await p.screenshot({path:'/workspace/output/watercolor-desktop.png',fullPage:true});console.log(JSON.stringify({errors,dialog:await p.locator('#delete-dialog').count(),errorField:await p.locator('#add-error').count(),symbols:await p.locator('#cat-art image').count(),pet:await p.evaluate(()=>!!window.gamePet3D?.diagnostics.ready)}));await p.locator('#nav-bank').click();await p.screenshot({path:'/tmp/watercolor-bank.png',fullPage:true});await p.setViewportSize({width:390,height:844});await p.locator('#nav-game').click();await p.screenshot({path:'/workspace/output/watercolor-mobile.png',fullPage:true});await b.close()})().catch(e=>{console.error(e);process.exit(1)})
~~~~~~~~~~

## 21. `/workspace/output/watercolor-edition/tests/verify.cjs`

~~~~~~~~~~
const { chromium } = require('playwright');
const assert = require('node:assert/strict');
const fs = require('node:fs');
const path = require('node:path');
const http = require('node:http');

(async () => {
 const html = fs.readFileSync(path.join(__dirname,'../src/truth-or-dare-watercolor.html'),'utf8');
 const server = http.createServer((req,res)=>{res.writeHead(200,{'Content-Type':'text/html; charset=utf-8'});res.end(html)});
 await new Promise(resolve=>server.listen(0,'127.0.0.1',resolve));
 const url=`http://127.0.0.1:${server.address().port}`;
 const browser=await chromium.launch({headless:true,executablePath:process.env.CHROMIUM_PATH||'/usr/bin/chromium',args:['--no-sandbox']});
 const context=await browser.newContext({viewport:{width:1280,height:1000}});
 const page=await context.newPage();page.setDefaultTimeout(6000);const errors=[],checks=[];
 page.on('pageerror',e=>errors.push(e.stack));
 try {
  await page.goto(url);await page.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);
  assert.equal(await page.locator('#pet3d-whale').count(),0);
  assert.equal(await page.locator('[data-appearance="whale"]').count(),0);
  assert.ok(await page.evaluate(()=>gamePet3D.renderer.media.clips.idle));
  assert.ok(await page.locator('#watercolor-sheet').getAttribute('href'));
  checks.push('仅恢复蓝发原版角色，水彩猫狗与拥抱插画内嵌且可用');
  const svg=page.locator('#btn-truth .choice-pet'),rect=await svg.boundingBox();
  await page.mouse.move(rect.x+rect.width/2,rect.y-18);await page.waitForTimeout(100);
  assert.equal(await svg.getAttribute('data-near'),'true');assert.ok(await svg.getAttribute('data-reaction'));
  await page.mouse.move(1,100);await page.waitForTimeout(100);assert.equal(await svg.getAttribute('data-near'),null);
  checks.push('图像外64px靠近可触发，离开后复位');
  await page.locator('#btn-truth').click();assert.ok(await page.locator('#question-text').innerText());
  await page.locator('#btn-next').click();await page.locator('#btn-quick-complete').click();assert.equal(await page.locator('#completed-count').innerText(),'1');
  await page.locator('#btn-dare').click();await page.locator('#btn-back').click();checks.push('快速抽题、换题、完成及返回');
  await page.locator('[data-mode="session"]').click();await page.locator('#btn-start-session').click();
  assert.equal(await page.locator('#current-player-name').innerText(),'我');await page.locator('#btn-session-truth').click();await page.locator('#btn-complete').click();
  assert.equal(await page.locator('#current-player-name').innerText(),'你');await page.locator('#btn-end-session').click();await page.locator('[data-mode="quick"]').click();checks.push('双人轮流与结束流程');
  await page.locator('#nav-agent').click();await page.locator('#agent-input').fill('统计');await page.locator('#agent-send').click();
  assert.ok((await page.locator('#agent-chat').innerText()).includes('100'));checks.push('指令助手实际响应');
  await page.locator('#nav-bank').click();assert.ok((await page.title()).includes('我的题库'));
  assert.equal(await page.locator('#stat-total').innerText(),'100');await page.locator('.btn-add').click();
  assert.equal(await page.locator('#add-text').getAttribute('aria-invalid'),'true');assert.equal(await page.locator('#add-error').isVisible(),true);
  assert.equal(await page.locator('#add-text').evaluate(e=>e===document.activeElement),true);
  await page.locator('#add-text').fill('我们一起给小猫起个名字 <测试>');await page.locator('#add-tags').fill('水彩,测试');await page.locator('.btn-add').click();
  assert.equal(await page.locator('#stat-total').innerText(),'101');assert.equal(await page.locator('#add-error').isVisible(),false);
  await page.locator('#search-input').fill('小猫起个名字');await page.locator('.search-btn').click();assert.equal(await page.locator('.list-item').count(),1);
  const deleteButton=page.locator('.list-item-btn.delete');await deleteButton.click();assert.equal(await page.locator('#delete-dialog').evaluate(e=>e.open),true);
  assert.equal(await page.locator('#delete-cancel').evaluate(e=>e===document.activeElement),true);assert.ok((await page.locator('#delete-question').innerText()).includes('<测试>'));
  await page.keyboard.press('Escape');assert.equal(await page.locator('#delete-dialog').evaluate(e=>e.open),false);assert.equal(await deleteButton.evaluate(e=>e===document.activeElement),true);
  await page.reload();await page.locator('#nav-bank').click();assert.equal(await page.locator('#stat-total').innerText(),'101');
  await page.locator('#search-input').fill('小猫起个名字');await page.locator('.search-btn').click();await page.locator('.list-item-btn.delete').click();await page.locator('#delete-commit').click();
  assert.equal(await page.locator('#stat-total').innerText(),'100');assert.equal(await page.locator('.list-item').count(),0);
  await page.locator('#clear-search').click();assert.equal(await page.locator('#search-input').inputValue(),'');assert.equal(await page.locator('.list-item').count(),100);
  assert.equal(await page.locator('#search-input').evaluate(e=>e===document.activeElement),true);checks.push('题库空输入关联错误、新增、转义、搜索、取消、焦点恢复、持久化和删除全流程');
  await page.locator('#search-input').fill('不存在的检索词xyz');await page.locator('.search-btn').click();assert.equal(await page.locator('.empty-state').isVisible(),true);await page.locator('#clear-search').click();checks.push('无结果及一键清空恢复');
  await page.locator('#search-input').evaluate(e=>{e.value='初恋';e.dispatchEvent(new CompositionEvent('compositionstart',{bubbles:true}));e.dispatchEvent(new InputEvent('input',{bubbles:true,isComposing:true,data:'恋'}))});
  await page.waitForTimeout(160);assert.equal(await page.locator('.list-item').count(),100);
  await page.locator('#search-input').dispatchEvent('compositionend');await page.waitForTimeout(160);assert.ok(await page.locator('.list-item').count()<100);await page.locator('#clear-search').click();checks.push('中文输入法组合阶段不提前搜索');
  await page.locator('#add-type').focus();await page.keyboard.press('ArrowDown');assert.equal(await page.locator('#add-type').inputValue(),'dare');
  await page.locator('#add-type').click();await page.keyboard.press('Escape');checks.push('原生选择框键盘选择及弹出层打开/退出');
  const scroll=await page.locator('.question-list').evaluate(e=>({color:getComputedStyle(e).scrollbarColor,width:getComputedStyle(e).scrollbarWidth}));assert.notEqual(scroll.color,'auto');assert.equal(scroll.width,'thin');checks.push('全局标准滚动条覆盖内部题目列表');
  await page.locator('#nav-game').click();await page.locator('#nav-game').focus();await page.keyboard.press('ArrowRight');assert.equal(await page.locator('#nav-agent').getAttribute('aria-selected'),'true');
  await page.keyboard.press('Home');assert.equal(await page.locator('#nav-game').getAttribute('aria-selected'),'true');checks.push('标签页键盘导航');
  await page.locator('#pet3d-launcher').click();await page.locator('#pet3d-random').click();assert.ok(await page.evaluate(()=>gamePet3D.diagnostics.actions>0));
  await page.locator('#pet3d-paused').check();assert.equal(await page.locator('#pet3d-random').isDisabled(),true);await page.locator('#pet3d-paused').uncheck();await page.locator('#pet3d-close').click();
  await page.locator('#motion-toggle').click();assert.equal(await page.locator('html').getAttribute('data-motion'),'reduced');
  assert.equal(await svg.getAttribute('data-near'),null);await page.locator('#motion-toggle').click();await page.emulateMedia({reducedMotion:'reduce'});await page.waitForTimeout(100);
  assert.equal(await page.locator('html').getAttribute('data-motion'),'reduced');await page.emulateMedia({reducedMotion:'no-preference'});checks.push('原角色随机互动、暂停、手动及系统减少动画');
  for(const width of [900,600,390,320]){
   await page.setViewportSize({width,height:844});
   for(const tab of ['game','agent','bank']){await page.locator(`#nav-${tab}`).click();await page.waitForTimeout(260);assert.equal(await page.evaluate(()=>document.documentElement.scrollWidth>innerWidth),false,`${tab} overflow ${width}`)}
  }checks.push('900/600/390/320px全部标签页无横向溢出');
  const fail=await context.newPage();await fail.addInitScript(()=>{Storage.prototype.setItem=()=>{throw new DOMException('Disabled','SecurityError')}});await fail.goto(url);await fail.locator('#nav-bank').click();
  assert.equal(await fail.locator('.storage-note').getAttribute('data-error'),'true');await fail.locator('#add-text').fill('仅内存保存测试');await fail.locator('.btn-add').click();assert.equal(await fail.locator('#stat-total').innerText(),'101');assert.ok((await fail.locator('.storage-note').innerText()).includes('本次打开'));await fail.close();checks.push('存储失败时有持续提示且内存操作可继续');
  const touch=await browser.newContext({viewport:{width:390,height:844},isMobile:true,hasTouch:true});const tp=await touch.newPage();await tp.goto(url);await tp.locator('#btn-truth').tap();assert.ok(await tp.locator('#question-text').innerText());await touch.close();checks.push('手机触摸抽题');
  assert.deepEqual(errors,[]);checks.push('无 JavaScript 运行错误');
  const report={checks,pageErrors:errors,browser:await browser.version()};fs.writeFileSync(path.join(__dirname,'../verification.json'),JSON.stringify(report,null,2));console.log(JSON.stringify(report,null,2));
 }finally{await browser.close();await new Promise(resolve=>server.close(resolve))}
})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 22. `/workspace/output/watercolor-edition/tests/accessibility.cjs`

~~~~~~~~~~
const {chromium}=require('playwright'),fs=require('node:fs'),path=require('node:path'),http=require('node:http');
(async()=>{const html=fs.readFileSync(path.join(__dirname,'../src/truth-or-dare-watercolor.html'),'utf8');const server=http.createServer((req,res)=>{res.writeHead(200,{'Content-Type':'text/html; charset=utf-8'});res.end(html)});await new Promise(r=>server.listen(0,'127.0.0.1',r));const b=await chromium.launch({headless:true,executablePath:process.env.CHROMIUM_PATH||'/usr/bin/chromium',args:['--no-sandbox']});try{const p=await b.newPage({viewport:{width:1280,height:1000},reducedMotion:'reduce'});await p.goto(`http://127.0.0.1:${server.address().port}`);await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);await p.addScriptTag({path:process.env.AXE_PATH||'/tmp/watercolor-a11y/node_modules/axe-core/axe.min.js'});const results=[];for(const tab of ['game','agent','bank']){await p.locator('#nav-'+tab).click();const r=await p.evaluate(()=>axe.run(document,{runOnly:{type:'tag',values:['wcag2a','wcag2aa','wcag21aa','wcag22aa']}}));results.push({surface:tab,violations:r.violations.map(v=>({id:v.id,impact:v.impact,nodes:v.nodes.map(n=>({target:n.target,summary:n.failureSummary}))}))})}await p.locator('.list-item-btn.delete').first().click();const d=await p.evaluate(()=>axe.run(document,{runOnly:{type:'tag',values:['wcag2a','wcag2aa','wcag21aa','wcag22aa']}}));results.push({surface:'delete-dialog',violations:d.violations.map(v=>({id:v.id,impact:v.impact,nodes:v.nodes.map(n=>({target:n.target,summary:n.failureSummary}))}))});fs.writeFileSync(path.join(__dirname,'../accessibility.json'),JSON.stringify(results,null,2));console.log(JSON.stringify(results,null,2));if(results.some(x=>x.violations.length))process.exitCode=1}finally{await b.close();await new Promise(r=>server.close(r))}})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 23. `/tmp/final-watercolor-preview.cjs`

~~~~~~~~~~
const {chromium}=require('playwright');
(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});const p=await b.newPage({viewport:{width:1280,height:1000}});await p.goto('http://127.0.0.1:8766/output/truth-or-dare-watercolor.html');await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);await p.waitForTimeout(550);await p.screenshot({path:'/workspace/output/watercolor-desktop.png',fullPage:true});await p.locator('#nav-agent').click();await p.waitForTimeout(350);await p.screenshot({path:'/workspace/output/watercolor-edition/helper-preview.png',fullPage:true});await p.locator('#nav-bank').click();await p.waitForTimeout(350);await p.screenshot({path:'/workspace/output/watercolor-edition/bank-preview.png',fullPage:true});await p.setViewportSize({width:390,height:844});await p.locator('#nav-game').click();await p.waitForTimeout(700);await p.screenshot({path:'/workspace/output/watercolor-mobile.png',fullPage:true});await b.close()})().catch(e=>{console.error(e);process.exit(1)})
~~~~~~~~~~

## 24. `/workspace/output/watercolor-edition/README.md`

~~~~~~~~~~
# 真心话大冒险 · 水彩版

直接打开 `src/truth-or-dare-watercolor.html` 即可使用。交付目录外的同名单文件是完全相同的可独立分发版本，不需要旁边的图片、服务器或字体文件。

- 恢复蓝发原版 DeepSeek 动画搭子；不再使用大肥鱼外观。
- 按用户提供的水彩猫狗参考适配透明插画，统一游戏桌、助手、题库和桌宠设置样式。
- 鼠标靠近猫狗、键盘聚焦卡片或触摸图片时产生轻柔的变换反馈。
- 原版搭子保留拖动、点击、随机动作、暂停、音效设置和回到角落；聚焦角色后可用方向键移动。
- 题库为本地浏览器存储，没有云同步。浏览器拒绝保存时，会持续显示“仅本次打开有效”的提示。

设计使用 Frontend Design Premium 与 Frontend Design；详见 `DESIGN.md` 和 `UX-CONTRACT.md`。

## 验证

`verification.json` 是实际 Chromium 运行结果；`accessibility.json` 是 axe 对四个界面的自动检查结果；`premium-audit.json` 和 `design-lint.json` 是静态检查结果。自动检查不代表所有浏览器、设备或辅助技术的完整合规认证。

在装有 Node.js、Playwright 与 Chromium 的开发环境中运行：

```sh
node tests/verify.cjs
AXE_PATH=/path/to/axe-core/axe.min.js node tests/accessibility.cjs
```

可用 `CHROMIUM_PATH` 指定本机浏览器路径。测试自行启动仅监听本机的临时 HTTP 服务，无需应用后端。

## 原作者与素材

原版动画角色与动画来自 [PC2005-cloud/dsh-pet](https://github.com/PC2005-cloud/dsh-pet)。保留 HTML 中原有 MIT 代码许可、原作者署名和媒体使用条件（允许开源使用，禁止商用）。页面猫狗为基于用户提供参考图的水彩风格适配插画。
~~~~~~~~~~

## 25. `/tmp/check-watercolor-offline.cjs`

~~~~~~~~~~
const {chromium}=require('playwright'),fs=require('node:fs'),assert=require('node:assert/strict');
(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});try{const p=await b.newPage();const html=fs.readFileSync('/workspace/output/truth-or-dare-watercolor.html','utf8'),external=[];await p.route('**/*',r=>{if(r.request().isNavigationRequest())return r.fulfill({status:200,contentType:'text/html',body:html});external.push(r.request().url());return r.abort()});await p.goto('http://offline-check.invalid');await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);await p.locator('#btn-truth').click();assert.ok(await p.locator('#question-text').innerText());assert.deepEqual(external,[]);const file='/workspace/output/watercolor-edition/verification.json',report=JSON.parse(fs.readFileSync(file,'utf8'));report.checks.push('所有外部资源请求被阻断时，角色加载与抽题仍正常');fs.writeFileSync(file,JSON.stringify(report,null,2));console.log('Offline self-contained HTML: passed')}finally{await b.close()}})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 26. `/tmp/mobile-check.cjs`

~~~~~~~~~~
const {chromium}=require('playwright');(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});const p=await b.newPage({viewport:{width:390,height:844}});await p.goto('http://127.0.0.1:8766/output/truth-or-dare-watercolor.html');await p.waitForTimeout(1000);console.log(await p.locator('.hero').evaluate(el=>[el,...el.querySelectorAll('*')].map(x=>({tag:x.tagName,cls:x.className.baseVal||x.className,rect:x.getBoundingClientRect().toJSON(),display:getComputedStyle(x).display,visibility:getComputedStyle(x).visibility,opacity:getComputedStyle(x).opacity,text:x.textContent.slice(0,30)}))));await p.screenshot({path:'/workspace/output/watercolor-mobile.png',fullPage:true});await b.close()})()
~~~~~~~~~~

## 27. `/tmp/renamed-smoke.cjs`

~~~~~~~~~~
const {chromium}=require('playwright'),fs=require('node:fs'),assert=require('node:assert/strict');
(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});try{const p=await b.newPage();const errors=[];p.on('pageerror',e=>errors.push(e.message));const html=fs.readFileSync('/workspace/output/maogou-xindongju-v4.1.html','utf8');await p.route('**/*',r=>r.fulfill({status:200,contentType:'text/html; charset=utf-8',body:html}));await p.goto('http://local-preview.invalid');await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);assert.equal(await p.locator('.logo-text').innerText(),'猫狗心动局');assert.equal(await p.title(),'猫狗心动局 · 水彩互动版 v4.1');await p.locator('#btn-truth').click();assert.ok(await p.locator('#question-text').innerText());await p.locator('#nav-bank').click();assert.ok((await p.title()).includes('猫狗心动局'));assert.equal(await p.locator('#stat-total').innerText(),'100');assert.deepEqual(errors,[]);console.log(JSON.stringify({name:await p.title(),errors,checked:['页面名称','标签页名称','原版角色','抽题','题库']}))}finally{await b.close()}})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 28. `/workspace/output/maogou-xindongju-web/README.md`

~~~~~~~~~~
# 猫狗心动局 · 在线站点

部署入口：`index.html`。这是可独立部署的静态网站；无构建步骤、无后端、无外部图片或字体依赖。

- GitHub Pages：将 index.html 发布到选定仓库的 Pages 根目录。
- Vercel / Netlify：选择静态站点部署，发布目录为本目录，无需构建命令。
- 保留 HTML 内原版角色署名与素材使用条件。
- 发布状态：尚未发布；当前会话未连接可用的公网托管服务。
~~~~~~~~~~

## 29. `/tmp/compact-html.cjs`

~~~~~~~~~~
const {chromium}=require('playwright');const fs=require('node:fs');
(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});try{const p=await b.newPage();const png=fs.readFileSync('/workspace/generated_images/exec-fe577d59-d0bf-435b-ac0f-47bd9e13f53f.png');const webp=await p.evaluate(async src=>{const image=new Image();image.src=src;await image.decode();const canvas=document.createElement('canvas');canvas.width=image.naturalWidth;canvas.height=image.naturalHeight;canvas.getContext('2d').drawImage(image,0,0);return canvas.toDataURL('image/webp',.95)},'data:image/png;base64,'+png.toString('base64'));let html=fs.readFileSync('/workspace/output/maogou-xindongju-v4.1.html','utf8');const before=Buffer.byteLength(html);html=html.replace(/(<image id="watercolor-sheet" href=")data:image\/png;base64,[^"]+(" width="2073")/,(_,a,z)=>a+webp+z);html=html.replace(/ onclick="GameActions.handle\(event\)"/g,'');html=html.replace(/v4\.1/g,'v4.2');fs.writeFileSync('/workspace/output/maogou-xindongju-v4.2.html',html);console.log(JSON.stringify({before,after:Buffer.byteLength(html),ratio:Buffer.byteLength(html)/before,embeddedImage:webp.slice(0,24),inlineHandlers:(html.match(/ onclick=/g)||[]).length}));}finally{await b.close()}})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 30. `/tmp/compatibility-preview.cjs`

~~~~~~~~~~
const {chromium}=require('playwright'),fs=require('node:fs'),assert=require('node:assert/strict');
(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});try{const p=await b.newPage({viewport:{width:1280,height:1000}});const html=fs.readFileSync('/workspace/output/maogou-xindongju-v4.2.html','utf8');await p.route('**/*',r=>r.fulfill({status:200,contentType:'text/html; charset=utf-8',headers:{'Content-Security-Policy':"default-src 'self' data: blob:; script-src 'unsafe-inline'; script-src-attr 'none'; style-src 'unsafe-inline'; img-src data:; media-src data: blob:"},body:html}));const errors=[];p.on('pageerror',e=>errors.push(e.message));await p.goto('http://compatibility-preview.invalid');await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);await p.waitForTimeout(350);await p.screenshot({path:'/workspace/output/maogou-xindongju-v4.2-preview.png',fullPage:true});await p.locator('#btn-truth').click();assert.ok(await p.locator('#question-text').innerText());await p.locator('#nav-bank').click();assert.equal(await p.locator('#stat-total').innerText(),'100');assert.deepEqual(errors,[]);console.log('Embedded-preview CSP check: passed');}finally{await b.close()}})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 31. `/tmp/sunset.css`

~~~~~~~~~~
/* Sunset theme: canonical color roles, all screens share the same adapters. */
:root{--ink:#FFF2E9;--muted:#D0BEC7;--paper:#111D2A;--white:#1C2A3B;--line:#6B5869;--mint:#352C43;--mint-deep:#F3AB98;--primary:var(--mint-deep);--apricot:#3D2D36;--orange-deep:#FFD0A5;--lilac:#252C40;--blue:var(--mint);--color-danger:#FFB6BE;--scroll-thumb:#897386;--scroll-track:#172334;--scroll-hover:#B79AA9;--scroll-active:#F3AB98;--on-primary:#251D29;--panel:#1B293B;--field:#172334;--field-border:#9C8396;--soft-pink:#FFD3C5;--soft-amber:#FFE2BE;--surface-line:rgba(255,211,197,.23);--text-display:44px}
body{position:relative;isolation:isolate;background:var(--paper);color:var(--ink)}
body::before{content:"";position:fixed;inset:0;z-index:-2;background-image:var(--scene-image);background-size:cover;background-position:center;pointer-events:none}
body::after{content:"";position:fixed;inset:0;z-index:-1;background:linear-gradient(180deg,rgba(12,20,34,.56),rgba(12,22,35,.90) 80%),linear-gradient(90deg,rgba(17,24,39,.67),rgba(17,24,39,.24));pointer-events:none}
.app-header{background:rgba(14,23,37,.80);border-color:var(--surface-line)}
.logo-icon{background:rgba(243,171,152,.13);color:var(--primary);border:1px solid rgba(243,171,152,.24)}
.logo-text{color:var(--ink);font-size:18px}
.logo-note{color:var(--muted);font-size:10px;letter-spacing:1px}
.nav-tab{color:var(--muted)}
.nav-tab.active{color:var(--soft-pink);background:rgba(243,171,152,.13);box-shadow:inset 0 -2px 0 var(--primary)}
.motion-toggle{background:rgba(28,42,59,.80);border-color:var(--surface-line);color:var(--ink)}
.motion-toggle[aria-pressed="true"] .motion-dot{background:var(--muted)}
.app-main{padding-top:26px}
.hero{position:relative;isolation:isolate;min-height:246px;border:1px solid var(--surface-line);border-radius:24px;margin-bottom:27px;padding:28px 32px;gap:25px;overflow:hidden;background-color:var(--paper);background-image:linear-gradient(90deg,rgba(15,23,38,.96) 0%,rgba(15,23,38,.86) 36%,rgba(15,23,38,.12) 80%),var(--scene-image);background-size:cover;background-position:center 56%;box-shadow:0 16px 45px rgba(5,10,20,.17)}
.hero-label{color:var(--soft-pink);font-size:12px;letter-spacing:1.5px;margin-bottom:13px}
.hero h2{color:var(--ink);font-size:43px;line-height:1.35;letter-spacing:.01em;font-weight:650}
.hero h2 em{color:var(--primary)}
.hero p{color:var(--ink);font-size:13px;line-height:1.9;margin-top:12px;letter-spacing:.3px}
.hero-note{flex:none;width:194px;align-self:flex-end;align-items:flex-start;border:1px solid var(--surface-line);background:rgba(20,28,43,.80);border-radius:15px;padding:12px 16px}
.hero-note p{font-size:12px;color:var(--soft-pink);line-height:1.9;letter-spacing:1.4px;margin:0}
.game-container,.agent-container,.bank-container{color:var(--ink);border-color:var(--surface-line);background:rgba(24,35,52,.96);box-shadow:0 12px 40px rgba(4,10,18,.16)}
.game-container{background:rgba(24,35,52,.91)}
.game-mode-bar{border-color:var(--surface-line)}
.mode-selector{background:var(--field);border:1px solid rgba(208,190,199,.10)}
.mode-btn{color:var(--muted)}
.mode-btn.active{background:var(--primary);color:var(--on-primary)}
.round-counter strong{color:var(--soft-pink)}
.stage-heading h3{font-size:20px;color:var(--ink);font-weight:600}
.stage-heading p{color:var(--muted);font-size:12px;letter-spacing:.3px}
.choice-truth{--card-edge:#86697B;--pet-color:var(--soft-pink);background:linear-gradient(145deg,#3F304A,#2C2A40)}
.choice-dare{--card-edge:#93695F;--pet-color:var(--soft-amber);background:linear-gradient(145deg,#49323B,#362A38)}
.choice-btn{position:relative;border-color:var(--card-edge);box-shadow:inset 0 1px 0 rgba(255,244,235,.05);overflow:hidden}
.card-index{color:var(--pet-color);font-size:11px;letter-spacing:1px}
.card-mark{color:var(--pet-color)}
.choice-pet{filter:drop-shadow(0 7px 12px rgba(6,8,19,.19));height:174px}
.choice-label{color:var(--ink);font-weight:600;font-size:25px;letter-spacing:1px}
.choice-sublabel{color:var(--muted)}
.card-arrow{background:rgba(255,216,203,.07);border-color:rgba(255,220,210,.35);color:var(--pet-color)}
.random-btn{color:var(--soft-pink);border:1px solid transparent}
.stage-footer{color:var(--muted);border-color:var(--surface-line);font-size:11px}
.buddy-room{background:rgba(35,37,57,.94);border-color:var(--surface-line);box-shadow:0 12px 30px rgba(5,10,18,.12)}
.buddy-title h3{color:var(--ink);font-size:14px}
.buddy-title span{background:#3C3048;color:var(--soft-pink);font-size:10px}
.buddy-speech{color:var(--ink);background:#3C3048;line-height:1.9}
.buddy-speech::before{background:#3C3048}
.buddy-names{color:var(--muted)}
.scene-star{color:var(--primary)}
.play-guide{background:rgba(24,35,52,.94);border:1px solid var(--surface-line);border-radius:20px;padding:20px}
.play-guide h3{color:var(--soft-pink);font-size:13px;font-weight:600}
.play-guide li{color:var(--muted);font-size:11px}
.guide-dot{background:#352C43;color:var(--soft-pink)}
.bank-preview{border-color:var(--surface-line);color:var(--muted)}
.bank-preview strong,.bank-preview svg{color:var(--soft-pink)}
.question-card{background:linear-gradient(135deg,#382D44,#27293D);border-color:#86697B;color:var(--ink)}
.question-card[data-type="dare"]{background:linear-gradient(135deg,#46313C,#2F2939);border-color:#93695F}
.question-type-badge,.history-item-type,.list-item-type{background:#46334A;color:var(--soft-pink)}
.question-type-badge.dare,.history-item-type.dare,.list-item-type.dare{background:#4A3435;color:var(--soft-amber)}
.question-text{color:var(--ink);line-height:1.9}
.question-id,.question-tag{color:var(--muted)}
.question-tag{border-color:#816A7E}
.btn-next,.btn-start-session,.btn-add,.agent-send,.search-btn,.btn-complete{background:var(--primary);color:var(--on-primary)}
.btn-back,.btn-add-player{background:#2C3448;border-color:var(--surface-line);color:var(--ink)}
.btn-end-session{background:#472F3D;color:var(--color-danger)}
input,select,textarea{background:var(--field);color:var(--ink);border-color:var(--field-border);color-scheme:dark}
input::placeholder{color:#B3A2B0;opacity:1}
input[aria-invalid="true"]{border-color:var(--color-danger)}
.section-title{color:var(--ink);letter-spacing:.3px}
.section-desc,.storage-note{color:var(--muted)}
.player-input-row label,.player-label{color:var(--muted)}
.remove-player{color:var(--ink);background:#2C3448;border-color:var(--surface-line)}
.session-info{background:#242E43;border:1px solid var(--surface-line)}
.session-stats-bar,.history-item-text,.history-title{color:var(--muted)}
.history-item{border-color:var(--surface-line)}
.agent-avatar{background:#352C43;border:1px solid var(--surface-line)}
.quick-cmd{background:#293047;border-color:#776279;color:var(--soft-pink)}
.agent-chat{background:#142032;border:1px solid rgba(208,190,199,.12)}
.message-content{background:#2A3147;border-color:#67556B;color:var(--ink)}
.chat-message.user .message-content{background:#F3AB98;border-color:#F3AB98;color:var(--on-primary)}
.chat-message.agent .message-content{background:#3B3049;border-color:#79617D;color:var(--ink)}
.intent-badge{color:var(--soft-pink)}
.api-info,.api-info summary{color:var(--muted)}
.api-info-content{background:#172334;color:var(--muted)}
code{background:#3C3049;color:var(--soft-pink)}
.stats-dashboard{background:#172334;border-color:var(--surface-line)}
.stat-card{border-color:var(--surface-line)}
.stat-value{color:var(--ink)}
.stat-truth .stat-value{color:var(--soft-pink)}
.stat-dare .stat-value{color:var(--soft-amber)}
.stat-label{color:var(--muted)}
.add-question-section{background:#172334;border:1px solid rgba(208,190,199,.10)}
.add-question-section h3{color:var(--soft-pink)}
.clear-search{background:#303349;color:var(--soft-pink)}
.filter-tab{color:var(--muted)}
.filter-tab.active{background:#493449;color:var(--soft-pink)}
.list-item{border-color:var(--surface-line)}
.list-item-text{color:var(--ink)}
.list-item-meta{color:var(--muted)}
.list-item-btn{background:#472F3D;color:var(--color-danger)}
.empty-state{color:var(--muted)}
.app-footer{background:rgba(15,25,40,.92);border:1px solid var(--surface-line);border-radius:18px;padding:18px 150px 18px 22px;color:var(--muted);margin-top:28px;font-size:10px}
.asset-credit{color:var(--soft-pink)}
.toast{color:var(--on-primary);background:var(--primary)}
.toast.error{background:var(--color-danger);color:var(--on-primary)}
.game-confirm{color:var(--ink);background:#202A3E;border-color:#8E7389;box-shadow:0 24px 80px rgba(0,0,0,.4)}
.game-confirm::backdrop{background:rgba(7,12,24,.75)}
.game-confirm h2{color:var(--ink)}
.game-confirm p{color:var(--muted)}
.game-confirm blockquote{background:#172334;border-color:#86697B;color:var(--ink)}
.confirm-cancel{background:#2C3448;color:var(--ink);border-color:#8E7389}
.confirm-delete{background:var(--color-danger);color:var(--on-primary)}
.pet3d-panel{background:#202A3E;border-color:#8E7389;color:var(--ink);box-shadow:0 14px 45px rgba(0,0,0,.4);color-scheme:dark}
.pet3d-panel h2{color:var(--ink)}
.pet3d-panel p,.pet3d-slider output,.pet3d-status,.pet3d-stats,.pet3d-panel details,.pet3d-panel summary{color:var(--muted)}
.pet3d-panel .pet3d-close,.pet3d-panel .pet3d-variant,.pet3d-panel .pet3d-action,.pet3d-panel .pet3d-random,.pet3d-panel .pet3d-bottom button{background:#303349;color:var(--soft-pink);border-color:#776279}
.pet3d-panel .pet3d-variant[aria-pressed="true"]{background:#493449;border-color:#B78395;color:var(--soft-pink)}
.pet3d-panel .pet3d-variant[data-pet3d-variant="lilac"][aria-pressed="true"]{background:#4A3435;border-color:#AD807B;color:var(--soft-amber)}
.pet3d-options{border-color:var(--surface-line)}
.pet3d-panel .pet3d-quality select{background:var(--field);color:var(--ink);border-color:var(--field-border)}
.pet3d-panel .pet3d-stats{background:#172334;color:var(--muted)}
.pet3d-panel .pet3d-error{background:#472F3D;color:var(--color-danger)}
.pet3d-panel .pet3d-enabled{background:#493449;color:var(--soft-pink)}
.pet3d-launcher{background:var(--primary);color:var(--on-primary);border-color:var(--primary);box-shadow:0 8px 25px rgba(0,0,0,.25)}
.pet3d-launcher .pet3d-live-dot{background:#3A3945}
.pet3d-bubble{background:#352C43;border-color:#99778F;color:var(--ink)}
.pet3d-bubble::after{background:#352C43;border-color:#99778F}
.pet3d-canvas{filter:drop-shadow(0 9px 16px rgba(0,0,0,.3))}
button:focus-visible,a:focus-visible,input:focus-visible,select:focus-visible,summary:focus-visible,[tabindex]:focus-visible{outline-color:var(--soft-amber)}
@media(hover:hover) and (pointer:fine){
 .nav-tab:hover:not(.active),.nav-tab:hover,.quick-cmd:hover,.filter-tab:hover,.mode-btn:not(.active):hover,.btn-back:hover,.btn-add-player:hover,.clear-search:hover,.motion-toggle:hover{background:#413346;color:var(--soft-pink)}
 .choice-btn:hover:not(:disabled){box-shadow:0 9px 24px rgba(0,0,0,.22),0 0 20px rgba(243,171,152,.04);border-color:#D3A0AE}
 .btn-next:hover,.btn-start-session:hover,.btn-add:hover,.agent-send:hover,.search-btn:hover,.btn-complete:hover,.pet3d-launcher:hover{background:#FFC2AD;color:var(--on-primary)}
 .list-item-btn:hover,.confirm-delete:hover{background:#FFD1D5;color:var(--on-primary)}
 .pet3d-panel button:hover,.pet3d-panel .pet3d-variant[data-pet3d-variant=lilac]:hover,.random-btn:hover{background:#493449;color:var(--soft-pink)}
}
@media(max-width:900px){.hero{min-height:231px;padding:26px 28px}.hero h2{font-size:38px}.hero-note{width:174px}.play-guide{padding:20px}.app-footer{padding-right:145px}}
@media(max-width:600px){
 .app-main{padding-top:20px}.hero{min-height:225px;padding:22px 21px;margin-bottom:22px;border-radius:22px;background-image:linear-gradient(90deg,rgba(15,23,38,.96),rgba(15,23,38,.72) 70%,rgba(15,23,38,.48)),var(--scene-image);background-position:65% 50%}.hero h2{font-size:30px;letter-spacing:.01em;line-height:1.4}.hero-label{font-size:10px;letter-spacing:.5px;margin-bottom:10px}.hero p{font-size:11px;line-height:1.8;max-width:26em;margin-top:12px}.hero-note{display:none}
 .logo-note{font-size:9px;letter-spacing:.3px}.logo-text{font-size:16px}.choice-pet{height:137px}.choice-label{font-size:22px}.card-index{font-size:10px;letter-spacing:.3px}.stage-heading h3{font-size:17px}.stage-heading p{font-size:11px}.play-guide{padding:19px}.app-footer{padding:17px 14px;font-size:10px;background:rgba(15,25,40,.95)}.buddy-room{background:rgba(35,37,57,.96)}
}
@media(max-width:350px){.hero{padding:20px 17px;min-height:219px}.hero h2{font-size:28px}.hero p{font-size:11px}.logo-text{font-size:15px}.logo-note{font-size:8px}.choice-pet{height:119px}.card-index{font-size:9px}.choice-label{font-size:21px}}
@media(prefers-reduced-transparency:reduce){.game-container,.buddy-room,.hero-note,.app-header{background-color:#1B293B}}
@media(forced-colors:active){body::before,body::after{display:none}.hero,.app-header,.game-container,.agent-container,.bank-container,.buddy-room,.play-guide,.game-confirm,.pet3d-panel,.choice-btn,.app-footer{background:Canvas;color:CanvasText;border-color:CanvasText}.hero h2,.hero h2 em,.hero p,.hero-label,.choice-label,.choice-sublabel{color:CanvasText}}
~~~~~~~~~~

## 32. `/tmp/prepare-sunset-scene.cjs`

~~~~~~~~~~
const {chromium}=require('playwright'),fs=require('node:fs');
(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});try{const p=await b.newPage();const src=fs.readFileSync('/workspace/generated_images/exec-54e56aef-b345-49ce-a8c7-397b87ef4995.png');const out=await p.evaluate(async src=>{const im=new Image();im.src=src;await im.decode();const c=document.createElement('canvas');c.width=im.naturalWidth;c.height=im.naturalHeight;c.getContext('2d').drawImage(im,0,0);return c.toDataURL('image/webp',.88)},'data:image/png;base64,'+src.toString('base64'));fs.writeFileSync('/tmp/sunset-scene.txt',out);console.log('Scene WebP:',out.length,'bytes encoded')}finally{await b.close()}})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 33. `/tmp/build_sunset.py`

~~~~~~~~~~
from pathlib import Path
import re,shutil,json
s=Path('/workspace/output/maogou-xindongju-v4.2.html').read_text()
s=re.sub(r'<title>.*?</title>','<title>猫狗心动局 · 日落微醺版 v5.0</title>',s,count=1)
s=s.replace('真心话大冒险 · 水彩互动版','真心话大冒险 · 日落微醺版')
s=s.replace("+' · 猫狗心动局 · 水彩互动版';", "+' · 猫狗心动局 · 日落微醺版';")
s=s.replace('猫狗心动局（水彩互动版 v4.2）。','猫狗心动局（日落微醺版 v5.0）。海边日落的双人约会氛围。')
s=s.replace('<meta name="theme-color" content="#F5F7F3">','<meta name="theme-color" content="#111D2A">')
s=s.replace('<h2>把心事，<em>说给你听。</em></h2>','<h2>晚风刚好，<br><em>心事慢慢说。</em></h2>',1)
s=s.replace('给喜欢的人，一点专属的时间','日落之后，留一点时间给彼此',1)
s=s.replace('从悄悄心动到认真喜欢，每张卡都是更了解彼此的机会。','把距离交给晚风，把真心留给彼此。<br>抽一张卡，聊聊那些还没说出口的话。',1)
s=re.sub(r'<div class="hero-note".*?</div>', '<div class="hero-note" aria-hidden="true"><p>日落会落幕，<br>心动可以慢一点。</p></div>',s,count=1,flags=re.S)
changes={
 '从一句真心话，开始靠近':'今晚，想再靠近你一点',
 '聊聊藏在心里的话，或一起制造一个小惊喜':'一张真心话，一点小冒险。听听彼此的心跳。',
 '听见你的心事':'那些没说出口的话',
 '一起心动一下':'一点只给你的勇敢',
 '让我再多了解你一点':'藏在心里的话，今晚慢慢说',
 '收集只属于我们的甜蜜':'把一点点勇敢，留给彼此',
 '你们的心动后援团':'替你保管一点心动',
 '喜欢不必急着说出口。<br>先从一个小问题开始吧。':'晚风已经替你开场。<br>接下来，听听彼此的心事。',
 '今晚的小约会':'今晚，慢慢靠近',
 '把普通的夜晚，变成只有你们懂的小小回忆。':'日落之后，把心动留在今晚。',
}
for a,b in changes.items():s=s.replace(a,b)
css=Path('/tmp/sunset.css').read_text()
css=css.replace(':root{',':root{--scene-image:url("'+Path('/tmp/sunset-scene.txt').read_text()+'");',1)
s=s.replace('</body>','<style id="sunset-design">'+css+'</style></body>')
out=Path('/workspace/output/maogou-xindongju-sunset-v5.html');out.write_text(s)
root=Path('/workspace/output/sunset-edition');(root/'src').mkdir(parents=True,exist_ok=True);(root/'tests').mkdir(exist_ok=True)
(root/'src'/out.name).write_text(s)
for filename in ['verify.cjs','accessibility.cjs']:
 t=Path('/workspace/output/watercolor-edition/tests',filename).read_text().replace('../src/truth-or-dare-watercolor.html','../src/'+out.name)
 (root/'tests'/filename).write_text(t)
for filename in ['premium-ui.json','UX-CONTRACT.md']:
 shutil.copy2('/workspace/output/watercolor-edition/'+filename,root/filename)
print('Sunset HTML:',len(s.encode()),'bytes')
~~~~~~~~~~

## 34. `/tmp/sunset-preview.cjs`

~~~~~~~~~~
const {chromium}=require('playwright'),fs=require('node:fs');
(async()=>{const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});try{const p=await b.newPage({viewport:{width:1440,height:1100}});const html=fs.readFileSync('/workspace/output/maogou-xindongju-sunset-v5.html','utf8'),errors=[];p.on('pageerror',e=>errors.push(e.stack));await p.route('**/*',r=>r.fulfill({status:200,contentType:'text/html; charset=utf-8',body:html}));await p.goto('http://sunset-preview.invalid');await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);await p.waitForTimeout(600);await p.screenshot({path:'/workspace/output/sunset-desktop.png',fullPage:true});await p.locator('#nav-agent').click();await p.waitForTimeout(350);await p.screenshot({path:'/workspace/output/sunset-edition/agent-preview.png',fullPage:true});await p.locator('#nav-bank').click();await p.waitForTimeout(350);await p.screenshot({path:'/workspace/output/sunset-edition/bank-preview.png',fullPage:true});await p.setViewportSize({width:390,height:844});await p.locator('#nav-game').click();await p.waitForTimeout(500);await p.screenshot({path:'/workspace/output/sunset-mobile.png'});console.log(JSON.stringify({pageErrors:errors,title:await p.title()}))}finally{await b.close()}})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 35. `/workspace/output/sunset-edition/tests/actions.cjs`

~~~~~~~~~~
const {chromium}=require('playwright'),fs=require('node:fs'),path=require('node:path'),assert=require('node:assert/strict');
(async()=>{const html=fs.readFileSync(path.join(__dirname,'../src/maogou-xindongju-sunset-v5.html'),'utf8');const b=await chromium.launch({headless:true,executablePath:'/usr/bin/chromium',args:['--no-sandbox']});try{const p=await b.newPage();await p.route('**/*',r=>r.fulfill({status:200,contentType:'text/html; charset=utf-8',body:html}));await p.goto('http://actions-check.invalid');await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);const rows=await p.evaluate(()=>[...document.querySelectorAll('.app-header button:not(.pet3d-launcher),.app-main button,#delete-dialog button')].map(el=>({id:el.id,label:el.textContent.trim(),registered:typeof el.onclick==='function',formSubmit:!!el.form&&el.type==='submit',disabled:el.disabled})));const unbound=rows.filter(x=>!x.registered&&!x.formSubmit&&!x.disabled);assert.deepEqual(unbound,[]);const report={checked:rows.length,unbound,rows,note:'Native JS handlers are active; no inline event attributes are required. The upstream static auditor only detects markup click attributes.'};fs.writeFileSync(path.join(__dirname,'../semantic-actions.json'),JSON.stringify(report,null,2));console.log(JSON.stringify({checked:rows.length,unbound:unbound.length}))}finally{await b.close()}})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 36. `/workspace/output/poker-edition/src/poker-engine.js`

~~~~~~~~~~
/* No-limit Texas Hold'em rules. No DOM, persistence, console output, or network. */
(function(root,factory){
 'use strict';
 if(typeof module==='object'&&module.exports)module.exports=factory();
 else root.PokerRulesForBundle=factory();
})(typeof globalThis!=='undefined'?globalThis:this,function(){
 'use strict';
 const SUITS=['♠','♥','♦','♣'];
 const RANKS={11:'J',12:'Q',13:'K',14:'A'};
 const HAND_NAMES=['高牌','一对','两对','三条','顺子','同花','葫芦','四条','同花顺'];
 function cardInfo(card){
  if(!Number.isInteger(card)||card<0||card>=52)throw new Error('无效的扑克牌。');
  const rank=card%13+2,suit=Math.floor(card/13);
  return {rank,suit,rankText:RANKS[rank]||String(rank),suitText:SUITS[suit],red:suit===1||suit===2};
 }
 function compare(a,b){for(let i=0;i<Math.max(a.length,b.length);i++){const d=(a[i]||0)-(b[i]||0);if(d)return Math.sign(d)}return 0}
 function evaluateFive(cards){
  const ranks=cards.map(c=>c%13+2).sort((a,b)=>b-a);
  const counts=new Map();for(const r of ranks)counts.set(r,(counts.get(r)||0)+1);
  const groups=[...counts].sort((a,b)=>b[1]-a[1]||b[0]-a[0]);
  const unique=[...new Set(ranks)];if(unique[0]===14)unique.push(1);
  let straight=0;for(let i=0;i<=unique.length-5;i++)if(unique[i]-unique[i+4]===4){straight=unique[i];break}
  const flush=cards.every(c=>Math.floor(c/13)===Math.floor(cards[0]/13));
  if(flush&&straight)return [8,straight];
  if(groups[0][1]===4)return [7,groups[0][0],groups[1][0]];
  if(groups[0][1]===3&&groups[1][1]===2)return [6,groups[0][0],groups[1][0]];
  if(flush)return [5,...ranks];
  if(straight)return [4,straight];
  if(groups[0][1]===3)return [3,groups[0][0],...groups.slice(1).map(x=>x[0]).sort((a,b)=>b-a)];
  if(groups[0][1]===2&&groups[1][1]===2)return [2,...groups.slice(0,2).map(x=>x[0]).sort((a,b)=>b-a),groups[2][0]];
  if(groups[0][1]===2)return [1,groups[0][0],...groups.slice(1).map(x=>x[0]).sort((a,b)=>b-a)];
  return [0,...ranks];
 }
 function evaluate(cards){
  if(cards.length<5||cards.length>7||new Set(cards).size!==cards.length)throw new Error('评估牌型需要 5—7 张不同的牌。');
  let score=null,best=[];
  for(let a=0;a<cards.length-4;a++)for(let b=a+1;b<cards.length-3;b++)for(let c=b+1;c<cards.length-2;c++)for(let d=c+1;d<cards.length-1;d++)for(let e=d+1;e<cards.length;e++){
   const five=[cards[a],cards[b],cards[c],cards[d],cards[e]],rank=evaluateFive(five);
   if(!score||compare(rank,score)>0){score=rank;best=five}
  }
  return {score,name:score[0]===8&&score[1]===14?'皇家同花顺':HAND_NAMES[score[0]],best};
 }
 function randomBelow(n){
  const bucket=new Uint32Array(1),limit=Math.floor(4294967296/n)*n;
  do{globalThis.crypto.getRandomValues(bucket)}while(bucket[0]>=limit);
  return bucket[0]%n;
 }
 function shuffledDeck(){const deck=Array.from({length:52},(_,i)=>i);for(let i=51;i>0;i--){const j=randomBelow(i+1);[deck[i],deck[j]]=[deck[j],deck[i]]}return deck}
 function splitPots(players,board,dealer){
  const levels=[...new Set(players.map(p=>p.invested).filter(x=>x>0))].sort((a,b)=>a-b);
  const payouts=players.map(()=>0),returns=players.map(()=>0),pots=[];
  const evaluations=players.map(p=>p.inHand&&!p.folded?evaluate([...p.hole,...board]):null);
  let previous=0;
  for(const level of levels){
   const contributors=players.map((p,i)=>p.invested>=level?i:-1).filter(i=>i>=0);
   const amount=(level-previous)*contributors.length;previous=level;
   if(contributors.length===1){returns[contributors[0]]+=amount;continue}
   const eligible=contributors.filter(i=>players[i].inHand&&!players[i].folded);
   if(!eligible.length)throw new Error('边池缺少有效的参赛玩家。');
   let winners=[eligible[0]];
   for(const i of eligible.slice(1)){const c=compare(evaluations[i].score,evaluations[winners[0]].score);if(c>0)winners=[i];else if(c===0)winners.push(i)}
   const share=Math.floor(amount/winners.length),remainder=amount%winners.length;
   const order=[...winners].sort((a,b)=>(a-dealer-1+players.length)%players.length-(b-dealer-1+players.length)%players.length);
   for(let j=0;j<order.length;j++)payouts[order[j]]+=share+(j<remainder?1:0);
   pots.push({amount,eligible:[...eligible],winners:[...winners]});
  }
  return {payouts,returns,pots,evaluations};
 }
 class Holdem{
  constructor({names,stack=1000,smallBlind=10,stacks=null,deckFactory=shuffledDeck}={}){
   if(!Array.isArray(names)||names.length<2||names.length>6||names.some(n=>typeof n!=='string'||!n.trim()||n.length>18))throw new Error('请填写 2—6 位玩家的名字。');
   if(!Number.isSafeInteger(stack)||stack<1||stack>1000000||!Number.isSafeInteger(smallBlind)||smallBlind<1||smallBlind>100000)throw new Error('筹码和小盲必须是有效的正整数。');
   const chips=stacks||names.map(()=>stack);
   if(chips.length!==names.length||chips.some(x=>!Number.isSafeInteger(x)||x<0||x>1000000)||chips.filter(x=>x>0).length<2)throw new Error('至少两位玩家需要有筹码。');
   this.players=names.map((name,i)=>({name:name.trim(),stack:chips[i],bet:0,invested:0,folded:false,allIn:false,inHand:false,hole:[],hasActed:false,lastActBet:0,lastAction:''}));
   this.smallBlind=smallBlind;this.bigBlind=smallBlind*2;this.deckFactory=deckFactory;
   this.phase='idle';this.street='preflop';this.actor=null;this.dealer=-1;this.handNo=0;this.board=[];this.deck=[];this.pending=new Set();this.result=null;this.handTotal=0;this.currentBet=0;this.lastFullRaise=this.bigBlind;
   this.initialTotal=chips.reduce((a,b)=>a+b,0);this.log=[];
  }
  nextSeat(index,predicate){for(let n=1;n<=this.players.length;n++){const i=(index+n+this.players.length)%this.players.length;if(predicate(this.players[i],i))return i}return null}
  logLine(text){this.log.push(text);if(this.log.length>60)this.log.shift()}
  startHand(){
   if(this.phase==='playing'||this.phase==='showdown')throw new Error('请先完成当前这一手。');
   if(this.players.filter(p=>p.stack>0).length<2)throw new Error('只剩一位玩家有筹码，请重新开桌。');
   this.handNo++;this.dealer=this.nextSeat(this.dealer,p=>p.stack>0);this.board=[];this.deck=[...this.deckFactory()];
   if(this.deck.length!==52||new Set(this.deck).size!==52||this.deck.some(c=>!Number.isInteger(c)||c<0||c>51))throw new Error('牌堆初始化失败，请重新开桌。');
   this.result=null;this.handTotal=0;this.phase='playing';this.street='preflop';this.actor=null;this.currentBet=this.bigBlind;this.lastFullRaise=this.bigBlind;this.log=[];
   for(const p of this.players){p.bet=0;p.invested=0;p.folded=false;p.allIn=false;p.inHand=p.stack>0;p.hole=[];p.hasActed=false;p.lastActBet=0;p.lastAction=p.inHand?'等待行动':'本局休息'}
   const count=this.players.filter(p=>p.inHand).length;
   this.sb=count===2?this.dealer:this.nextSeat(this.dealer,p=>p.inHand);this.bb=this.nextSeat(this.sb,p=>p.inHand);
   let seat=this.sb;for(let round=0;round<2;round++){for(let n=0;n<count;n++){this.players[seat].hole.push(this.deck.pop());seat=this.nextSeat(seat,p=>p.inHand)}}
   this.commit(this.sb,Math.min(this.smallBlind,this.players[this.sb].stack));this.players[this.sb].lastAction='小盲 '+this.players[this.sb].bet;
   this.commit(this.bb,Math.min(this.bigBlind,this.players[this.bb].stack));this.players[this.bb].lastAction='大盲 '+this.players[this.bb].bet;
   this.pending=new Set(this.players.map((p,i)=>p.inHand&&p.stack>0?i:-1).filter(i=>i>=0));
   this.logLine('第 '+this.handNo+' 手开始 · 盲注 '+this.smallBlind+' / '+this.bigBlind);
   this.advance(this.bb);this.assertConservation();return this.publicState();
  }
  commit(index,amount){const p=this.players[index];p.stack-=amount;p.bet+=amount;p.invested+=amount;p.allIn=p.stack===0;this.handTotal+=amount}
  live(){return this.players.map((p,i)=>p.inHand&&!p.folded?i:-1).filter(i=>i>=0)}
  legal(){
   if(this.phase!=='playing'||this.actor===null)return null;
   const p=this.players[this.actor],toCall=Math.max(0,this.currentBet-p.bet),max=p.bet+p.stack;
   const reopened=!p.hasActed||this.currentBet-p.lastActBet>=this.lastFullRaise;
   const responders=this.players.some((q,i)=>i!==this.actor&&q.inHand&&!q.folded&&q.stack>0);
   const canRaise=reopened&&responders&&max>this.currentBet;
   return {actor:this.actor,toCall,call:Math.min(toCall,p.stack),canCheck:toCall===0,canRaise,minRaiseTo:this.currentBet+this.lastFullRaise,maxRaiseTo:max,canAllIn:p.stack>0&&(max<=this.currentBet||canRaise),raiseReopened:reopened};
  }
  validate(type,target){
   const legal=this.legal();if(!legal)throw new Error('当前没有可以行动的玩家。');
   if(!['fold','check','call','raise','allin'].includes(type))throw new Error('未知的行动。');
   if(type==='check'&&!legal.canCheck)throw new Error('需要跟注时不能过牌。');
   if(type==='call'&&legal.canCheck)throw new Error('无需跟注，请选择过牌。');
   if(type==='allin'&&!legal.canAllIn)throw new Error('当前只能跟注或弃牌，尚未重新开放加注。');
   if(type==='raise'){
    if(!legal.canRaise)throw new Error('当前无法加注。');
    if(!Number.isSafeInteger(target)||target<=this.currentBet||target>legal.maxRaiseTo)throw new Error('请填写有效的本轮加注总额。');
    if(target<legal.minRaiseTo&&target!==legal.maxRaiseTo)throw new Error('本次至少加注至 '+legal.minRaiseTo+'，或选择全下。');
   }
   return legal;
  }
  act(type,target){
   const legal=this.validate(type,target),index=this.actor,p=this.players[index],oldBet=this.currentBet;
   this.pending.delete(index);
   if(type==='fold'){p.folded=true;p.lastAction='已弃牌';this.logLine(p.name+' 弃牌')}
   else if(type==='check'){p.lastAction='过牌';this.logLine(p.name+' 过牌')}
   else if(type==='call'){this.commit(index,legal.call);p.lastAction=(p.allIn?'全下跟注 ':'跟注 ')+legal.call;this.logLine(p.name+' '+p.lastAction)}
   else{
    const total=type==='allin'?p.bet+p.stack:target;
    this.commit(index,total-p.bet);p.lastAction=(p.allIn?'全下至 ':'加注至 ')+total;this.logLine(p.name+' '+p.lastAction);
    if(total>oldBet){
     const increment=total-oldBet;this.currentBet=total;
     if(increment>=this.lastFullRaise){this.lastFullRaise=increment;this.pending=new Set(this.players.map((q,i)=>i!==index&&q.inHand&&!q.folded&&q.stack>0?i:-1).filter(i=>i>=0))}
     else for(let i=0;i<this.players.length;i++){const q=this.players[i];if(i!==index&&q.inHand&&!q.folded&&q.stack>0&&q.bet<this.currentBet)this.pending.add(i)}
    }
   }
   p.hasActed=true;p.lastActBet=this.currentBet;
   this.advance(index);this.assertConservation();return this.publicState();
  }
  advance(after){
   const live=this.live();if(live.length===1){this.awardFold(live[0]);return}
   for(const i of [...this.pending]){const p=this.players[i];if(!p.inHand||p.folded||p.stack===0)this.pending.delete(i)}
   const actionable=live.filter(i=>this.players[i].stack>0);
   if(actionable.length<=1){
    if(actionable.length===1){const i=actionable[0];if(this.players[i].bet<this.currentBet){this.pending=new Set([i]);this.actor=i;return}}
    this.runout();return;
   }
   if(this.pending.size){this.actor=this.nextSeat(after,(p,i)=>this.pending.has(i));return}
   if(this.street==='river'){this.beginShowdown();return}
   this.nextStreet();
  }
  nextStreet(){
   this.deck.pop();
   if(this.street==='preflop'){this.street='flop';this.board.push(this.deck.pop(),this.deck.pop(),this.deck.pop())}
   else if(this.street==='flop'){this.street='turn';this.board.push(this.deck.pop())}
   else if(this.street==='turn'){this.street='river';this.board.push(this.deck.pop())}
   for(const p of this.players){p.bet=0;p.hasActed=false;p.lastActBet=0;if(p.inHand&&!p.folded&&!p.allIn)p.lastAction='等待行动'}
   this.currentBet=0;this.lastFullRaise=this.bigBlind;
   this.pending=new Set(this.players.map((p,i)=>p.inHand&&!p.folded&&p.stack>0?i:-1).filter(i=>i>=0));
   this.actor=this.nextSeat(this.dealer,(p,i)=>this.pending.has(i));
   this.logLine({flop:'翻牌',turn:'转牌',river:'河牌'}[this.street]+' · 开始新一轮下注');
  }
  runout(){while(this.board.length<5){if(this.street==='river')break;this.nextStreet()}this.beginShowdown()}
  beginShowdown(){this.phase='showdown';this.actor=null;this.pending.clear();this.logLine('下注结束 · 按座位顺序逐家亮牌')}
  awardFold(winner){
   const pot=this.players.reduce((s,p)=>s+p.invested,0);this.players[winner].stack+=pot;
   this.phase='complete';this.actor=null;this.pending.clear();this.result={kind:'fold',total:pot,payouts:this.players.map((_,i)=>i===winner?pot:0),returns:this.players.map(()=>0),pots:[{amount:pot,winners:[winner]}],names:[]};
   this.logLine(this.players[winner].name+' 收下底池 '+pot+' · 无需亮牌');
  }
  finishShowdown(){
   if(this.phase!=='showdown')throw new Error('尚未进入摊牌阶段。');
   const result=splitPots(this.players,this.board,this.dealer);
   const total=this.players.reduce((s,p)=>s+p.invested,0);
   for(let i=0;i<this.players.length;i++)this.players[i].stack+=result.payouts[i]+result.returns[i];
   this.result={kind:'showdown',total,payouts:result.payouts,returns:result.returns,pots:result.pots,names:result.evaluations.map(x=>x?.name||'已弃牌')};
   this.phase='complete';this.actor=null;this.logLine('逐家亮牌完成 · 筹码已分配');this.assertConservation();return this.publicState();
  }
  cardsFor(index,publicMode=false){
   const p=this.players[index];if(!p||p.hole.length!==2)return [];
   if(publicMode||this.phase==='showdown'||(this.phase==='complete'&&this.result?.kind==='showdown')||(this.phase==='playing'&&this.actor===index))return [...p.hole];
   return [];
  }
  handName(index){if(this.phase!=='showdown'&&!(this.phase==='complete'&&this.result?.kind==='showdown'))return '';const p=this.players[index];return p?.hole.length===2?evaluate([...p.hole,...this.board]).name:''}
  publicState(){
   return {phase:this.phase,street:this.street,actor:this.actor,dealer:this.dealer,sb:this.sb,bb:this.bb,handNo:this.handNo,board:[...this.board],currentBet:this.currentBet,smallBlind:this.smallBlind,bigBlind:this.bigBlind,pot:this.phase==='complete'?0:this.players.reduce((s,p)=>s+p.invested,0),handTotal:this.handTotal,players:this.players.map(({name,stack,bet,invested,folded,allIn,inHand,lastAction},i)=>({index:i,name,stack,bet,invested,folded,allIn,inHand,lastAction})),result:this.result?JSON.parse(JSON.stringify(this.result)):null,log:[...this.log],legal:this.legal()};
  }
  assertConservation(){const total=this.players.reduce((s,p)=>s+p.stack+(this.phase==='complete'?0:p.invested),0);if(total!==this.initialTotal||this.players.some(p=>p.stack<0||!Number.isSafeInteger(p.stack)))throw new Error('筹码校验失败，请重新开桌。')}
 }
 return {Holdem,cardInfo,evaluate,compare,splitPots,shuffledDeck};
});
~~~~~~~~~~

## 37. `/workspace/output/poker-edition/src/poker-panel.html`

~~~~~~~~~~
<section class="tab-panel" id="tab-poker" role="tabpanel" aria-labelledby="nav-poker" hidden>
 <div class="pk-shell" id="poker-app" data-phase="setup" data-view="private">
  <div class="pk-toolbar">
   <div><p class="pk-eyebrow">落日牌局 · 本机轮流</p><h2>德州扑克</h2><p class="pk-subtitle">2—6 人同桌 · 虚拟筹码</p></div>
   <label class="pk-mode-switch" for="pk-spectator"><span><strong>旁观模式</strong><small>开启后公开所有底牌</small></span><input type="checkbox" role="switch" id="pk-spectator" aria-describedby="pk-mode-description"><span class="pk-switch-track" aria-hidden="true"></span></label>
  </div>
  <p id="pk-mode-description" class="pk-mode-message" role="status">私密轮流：只在确认身份后显示当前行动玩家的底牌。</p>
  <div class="pk-exposed-note" id="pk-exposed-note" hidden>本局曾开启旁观模式，底牌已经公开过；关闭后仍会保留此提示。</div>
  <form class="pk-setup" id="pk-setup" novalidate>
   <div class="pk-setup-intro"><span class="pk-seal" aria-hidden="true">♠</span><div><h3>拉把椅子，今晚一起入座。</h3><p>写下名字，确认座位，再把设备交给行动玩家。</p></div></div>
   <div class="pk-config-grid">
    <label>入座人数<select id="pk-count"><option value="2">2 人</option><option value="3">3 人</option><option value="4" selected>4 人</option><option value="5">5 人</option><option value="6">6 人</option></select></label>
    <label>每人初始筹码<input type="number" id="pk-stack" value="1000" min="100" max="100000" step="100" inputmode="numeric" aria-describedby="pk-setup-error"></label>
    <label>小盲 / 大盲<input type="number" id="pk-small-blind" value="10" min="1" max="10000" step="1" inputmode="numeric" aria-describedby="pk-blind-help pk-setup-error"><span id="pk-blind-help" class="pk-field-hint">大盲为小盲的 2 倍</span></label>
   </div>
   <div class="pk-name-grid" id="pk-name-fields"></div>
   <p class="field-error" id="pk-setup-error" role="alert" hidden></p>
   <div class="pk-setup-bottom"><p>筹码仅用于这张桌子的游戏计分。离开页面后，牌局不会保存。</p><button type="submit" class="action-btn pk-primary" id="pk-start">确认座位，开始发牌 <span aria-hidden="true">↗</span></button></div>
  </form>
  <div id="pk-live" hidden>
   <div class="pk-live-header"><div class="pk-round"><strong id="pk-hand-number">第 1 手</strong><span id="pk-street">翻牌前</span></div><div class="pk-table-meta"><span id="pk-blinds"></span><button type="button" id="pk-new-table" class="pk-quiet">重新开桌</button></div></div>
   <div class="pk-table" id="pk-table">
    <div class="pk-board-area"><p class="pk-table-wordmark">SUNSET HOLD’EM</p><div class="pk-pot"><span id="pk-pot-label">底池</span><strong id="pk-pot">0</strong><span class="pk-chip-symbol" aria-hidden="true"></span></div><div class="pk-community" id="pk-community" aria-label="公共牌"></div><p class="pk-round-status" id="pk-round-status" role="status">准备发牌</p></div>
    <div class="pk-seats" id="pk-seats" aria-label="玩家座位"></div>
   </div>
   <section class="pk-action-panel" id="pk-action-panel" aria-labelledby="pk-action-title">
    <div class="pk-action-heading"><div><h3 id="pk-action-title">等待确认身份</h3><p id="pk-action-context"></p></div><button type="button" id="pk-hide" class="pk-quiet">收起底牌 / 交接设备</button></div>
    <div class="pk-action-buttons"><button type="button" class="pk-fold" id="pk-fold">弃牌</button><button type="button" class="pk-secondary" id="pk-check">过牌</button><button type="button" class="pk-primary" id="pk-call">跟注</button><button type="button" class="pk-allin" id="pk-allin">全下</button></div>
    <form id="pk-raise-form" class="pk-raise-form" novalidate><label for="pk-raise">本轮加注至<input type="number" id="pk-raise" inputmode="numeric" step="1" aria-describedby="pk-raise-help pk-action-error"></label><button type="submit" id="pk-raise-button" class="pk-secondary">确认加注</button><p id="pk-raise-help" class="pk-field-hint"></p></form>
    <p id="pk-action-error" class="field-error" role="alert" hidden></p>
   </section>
   <section class="pk-showdown-panel" id="pk-showdown-panel" aria-labelledby="pk-showdown-title" hidden><div class="pk-showdown-icon" aria-hidden="true">✦</div><div><h3 id="pk-showdown-title">逐家揭晓</h3><p id="pk-showdown-progress" role="status" aria-live="polite">即将按照座位顺序翻开底牌。</p></div><span id="pk-reveal-count">0 / 0</span></section>
   <section class="pk-result" id="pk-result" aria-labelledby="pk-result-title" hidden><p class="pk-eyebrow">这一手，落定</p><h3 id="pk-result-title">筹码已分配</h3><div id="pk-payouts"></div><div id="pk-side-pots" class="pk-side-pots"></div><p id="pk-result-help"></p><button type="button" class="action-btn pk-primary" id="pk-next-hand">下一手，轮换庄家</button></section>
   <details class="pk-history"><summary>本手行动记录</summary><ol id="pk-log"></ol></details>
  </div>
  <details class="pk-rules"><summary>玩法与私密交接说明</summary><div><p>每人两张底牌，结合五张公共牌选出最好的五张组合。依次进行翻牌前、翻牌、转牌、河牌下注；支持全下、边池和平局分池。小盲由庄家左手起轮换，双人时庄家为小盲。</p><p>普通模式每次行动结束都会收牌并遮住全屏。下一位玩家确认身份后，才显示其底牌；未确认时也可以暂时离桌。摊牌时包括已弃牌座位在内，按座位顺序逐家公开本手已发的手牌；弃牌玩家不参与底池分配。其余玩家全部弃牌时，直接收下底池，无需亮牌。</p><p>旁观模式会直接公开所有玩家底牌，开启前请确认同桌玩家知情。本机轮流适用于熟人同屏；身份确认是自行确认，不能替代独立设备的私密对局。</p></div></details>
 </div>
</section>
~~~~~~~~~~

## 38. `/workspace/output/poker-edition/src/poker-overlays.html`

~~~~~~~~~~
<dialog class="pk-curtain" id="pk-curtain" aria-labelledby="pk-curtain-title" aria-describedby="pk-curtain-help">
 <div class="pk-curtain-content"><div class="pk-lock-symbol" aria-hidden="true"><svg viewBox="0 0 48 48" fill="none"><rect x="12" y="22" width="24" height="19" rx="5" stroke="currentColor" stroke-width="2"/><path d="M17 22v-7a7 7 0 0 1 14 0v7" stroke="currentColor" stroke-width="2"/><circle cx="24" cy="31" r="2" fill="currentColor"/></svg></div><p class="pk-eyebrow">底牌已收起 · 请交接设备</p><h2 id="pk-curtain-title">请下一位玩家接过设备</h2><p id="pk-curtain-help">请其他玩家暂时移开视线。确认身份后，只会显示你的两张底牌。</p><button type="button" class="action-btn pk-primary" id="pk-confirm-player">确认身份，查看底牌</button><button type="button" class="pk-quiet" id="pk-leave">先离桌，暂不亮牌</button><p class="pk-curtain-tip" id="pk-curtain-tip" aria-live="polite"></p></div>
</dialog>
<dialog class="game-confirm pk-confirm" id="pk-confirm-dialog" aria-labelledby="pk-confirm-title" aria-describedby="pk-confirm-description"><h2 id="pk-confirm-title">开启旁观模式？</h2><p id="pk-confirm-description"></p><div class="confirm-actions"><button type="button" class="action-btn confirm-cancel" id="pk-confirm-cancel">取消</button><button type="button" class="action-btn pk-primary" id="pk-confirm-accept">确认开启</button></div></dialog>
~~~~~~~~~~

## 39. `/workspace/output/poker-edition/src/poker-ui.js`

~~~~~~~~~~
/* Hot-seat controller: private cards are never serialized into HTML, storage, or logs. */
const {Holdem,cardInfo}=PokerRules;
const $=selector=>document.querySelector(selector);
const app=$('#poker-app'),curtain=$('#pk-curtain'),confirmDialog=$('#pk-confirm-dialog');
const modeSwitch=$('#pk-spectator');
const streets={preflop:'翻牌前',flop:'翻牌',turn:'转牌',river:'河牌'};
let engine=null,spectator=false,exposedThisHand=false,locked=true,confirmedSeat=null;
let active=false,windowActive=true,seatNodes=[],faceStamps=new Map(),boardStamp='';
let revealed=new Set(),revealCursor=0,ceremonyEpoch=0,ceremonyRunning=false,ceremonyTimers=new Set();
let confirmResolve=null,confirmFocus=null,actionBusy=false;
function bind(id,fn){GameActions.register($(id),fn)}
function make(tag,className,text){const el=document.createElement(tag);if(className)el.className=className;if(text!==undefined)el.textContent=text;return el}
function state(){return engine?.publicState()||null}
function reduced(){return matchMedia('(prefers-reduced-motion: reduce)').matches||document.documentElement.dataset.motion==='reduced'}
function clearError(id){const el=$(id);el.hidden=true;el.textContent=''}
function error(id,message,field){const el=$(id);el.textContent=message;el.hidden=false;if(field){field.setAttribute('aria-invalid','true');field.focus()}}
function eraseHands(){
 // Synchronous removal occurs BEFORE the opaque handoff dialog opens.
 for(const {holes} of seatNodes)holes.replaceChildren();
 faceStamps.clear();
}
function closeCurtain(){if(curtain.open)curtain.close()}
function showHandoff(){
 if(!engine||spectator||state().phase!=='playing'||!active)return;
 locked=true;confirmedSeat=null;eraseHands();app.dataset.view='curtain';
 const s=state();$('#pk-curtain-title').textContent='请把设备交给 '+s.players[s.actor].name;
 $('#pk-confirm-player').textContent='我是 '+s.players[s.actor].name+'，查看我的底牌';
 $('#pk-curtain-tip').textContent='';
 if(confirmDialog.open)return;
 if(!curtain.open)curtain.showModal();
 $('#pk-confirm-player').focus({preventScroll:true});
 updateActions(s);
}
function cardNode(card,kind,owner){
 const info=cardInfo(card),el=make('div','pk-card '+(kind==='hole'?'pk-hole-card':'pk-community-card')+(info.red?' pk-red':''));
 el.setAttribute('role','img');el.setAttribute('aria-label',info.suitText+' '+info.rankText);
 if(kind==='hole')el.dataset.pkOwner=String(owner);
 const corner=make('span','pk-card-corner');corner.append(make('strong','',info.rankText),make('span','',info.suitText));
 el.append(corner,make('span','pk-card-pip',info.suitText),make('span','pk-card-foot',info.rankText));return el;
}
function renderBacks(index){
 const holes=seatNodes[index].holes;if(holes.children.length&&holes.firstElementChild.classList.contains('pk-back'))return;
 holes.replaceChildren();faceStamps.delete(index);
 for(let i=0;i<2;i++){const back=make('span','pk-back');back.setAttribute('role','img');back.setAttribute('aria-label','底牌未公开');holes.append(back)}
}
function renderFaces(index,{flip=false}={}){
 const s=state(),cards=engine.cardsFor(index,spectator);
 if(cards.length!==2)return;
 if(faceStamps.get(index)===s.handNo&&seatNodes[index].holes.querySelectorAll('.pk-hole-card').length===2)return;
 const holes=seatNodes[index].holes;holes.replaceChildren();
 cards.forEach((card,i)=>{const el=cardNode(card,'hole',index);if(flip&&!reduced()){el.classList.add('pk-flip');el.style.setProperty('--pk-flip-delay',i*100+'ms')}holes.append(el)});
 faceStamps.set(index,s.handNo);
}
function renderHands(){
 if(!engine||!active)return;
 const s=state();
 if(!spectator&&s.phase==='playing'&&(locked||confirmedSeat!==s.actor)){eraseHands();return}
 for(let i=0;i<s.players.length;i++){
  const p=s.players[i];if(!p.inHand){seatNodes[i].holes.replaceChildren();faceStamps.delete(i);continue}
  if(spectator){renderFaces(i);continue}
  if(s.phase==='playing'&&i===confirmedSeat){renderFaces(i);continue}
  if((s.phase==='showdown'&&revealed.has(i))||(s.phase==='complete'&&s.result?.kind==='showdown')){renderFaces(i);continue}
  // No actual face nodes, attributes, titles or labels exist for concealed cards.
  renderBacks(i);
 }
 app.dataset.view=spectator?'spectator':s.phase==='playing'?'private':s.phase==='showdown'?'showdown':'settled';
}
function buildSeats(s){
 $('#pk-seats').replaceChildren();seatNodes=[];faceStamps.clear();app.style.setProperty('--pk-player-count',s.players.length);
 s.players.forEach((p,i)=>{
  const el=make('article','pk-seat');el.dataset.pkSeat=String(i);el.setAttribute('aria-label','座位 '+(i+1)+'，'+p.name);
  const header=make('div','pk-seat-header'),identity=make('div','pk-seat-identity');
  identity.append(make('span','pk-seat-number',String(i+1)),make('h3','pk-seat-name',p.name));
  const roles=make('div','pk-seat-roles');header.append(identity,roles);
  const badge=make('span','pk-observer-badge','观战模式');badge.hidden=true;
  const holes=make('div','pk-hole-area');holes.dataset.pkHoles=String(i);holes.setAttribute('aria-label',p.name+' 的底牌区域');
  const status=make('p','pk-seat-status'),chips=make('div','pk-seat-chips'),stack=make('strong'),bet=make('span');chips.append(stack,bet);
  const hand=make('p','pk-hand-name');hand.textContent='';
  el.append(header,badge,holes,status,chips,hand);$('#pk-seats').append(el);
  seatNodes.push({el,roles,badge,holes,status,stack,bet,hand});
 });
}
function renderBoard(s){
 const key=s.board.join(',');if(boardStamp===key&&$('#pk-community').children.length===5)return;boardStamp=key;
 const nodes=s.board.map(c=>cardNode(c,'board'));
 while(nodes.length<5){const slot=make('span','pk-board-slot');slot.setAttribute('aria-hidden','true');nodes.push(slot)}
 $('#pk-community').replaceChildren(...nodes);
}
function updateModeNotice(){
 modeSwitch.checked=spectator;app.dataset.spectator=String(spectator);
 $('#pk-mode-description').textContent=spectator?'观战模式：所有玩家的底牌持续公开显示；同桌玩家均可查看。':'私密轮流：只在确认身份后显示当前行动玩家的底牌。';
 $('#pk-mode-description').classList.toggle('pk-public-message',spectator);
 $('#pk-exposed-note').hidden=!exposedThisHand||spectator||!engine;
 for(const seat of seatNodes)seat.badge.hidden=!spectator;
}
function renderPublic(){
 updateModeNotice();if(!engine)return;
 const s=state();app.dataset.phase=s.phase;$('#pk-setup').hidden=true;$('#pk-live').hidden=false;
 $('#pk-hand-number').textContent='第 '+s.handNo+' 手';$('#pk-street').textContent=s.phase==='showdown'?'摊牌时刻':s.phase==='complete'?'本手结束':streets[s.street];
 $('#pk-blinds').textContent='盲注 '+s.smallBlind+' / '+s.bigBlind;$('#pk-pot').textContent=String(s.phase==='complete'?s.result.total:s.pot);$('#pk-pot-label').textContent=s.phase==='complete'?'本手已分配':'底池';
 renderBoard(s);
 s.players.forEach((p,i)=>{
  const seat=seatNodes[i];seat.el.classList.toggle('pk-current',s.phase==='playing'&&i===s.actor);seat.el.classList.toggle('pk-folded',p.folded);seat.el.classList.toggle('pk-sitting-out',!p.inHand);
  seat.el.classList.toggle('pk-winner',s.phase==='complete'&&s.result.payouts[i]>0);
  seat.roles.replaceChildren();if(i===s.dealer)seat.roles.append(make('span','pk-dealer','D'));if(i===s.sb)seat.roles.append(make('span','pk-blind','SB'));if(i===s.bb)seat.roles.append(make('span','pk-blind','BB'));
  seat.badge.hidden=!spectator;seat.stack.textContent=p.stack+' 筹码';seat.bet.textContent=p.inHand?'本轮 '+p.bet:'';
  seat.status.textContent=!p.inHand?'本局休息':p.folded?'已弃牌':p.allIn?'已全下':s.phase==='playing'&&i===s.actor?(spectator?'正在行动 · 手牌公开':locked?'等待交接确认':'正在行动'):p.lastAction;
  if(!revealed.has(i)&&s.phase!=='complete')seat.hand.textContent='';
 });
 if(s.phase==='playing')$('#pk-round-status').textContent='轮到 '+s.players[s.actor].name+' · '+streets[s.street];
 else if(s.phase==='showdown')$('#pk-round-status').textContent='下注结束 · 依座位顺序逐家亮牌';
 else $('#pk-round-status').textContent=s.result.kind==='fold'?'其余玩家已弃牌 · 无需亮牌':'全部手牌已揭晓';
 $('#pk-log').replaceChildren(...s.log.slice(-20).map(line=>make('li','',line)));
 updateActions(s);
 $('#pk-showdown-panel').hidden=s.phase!=='showdown';$('#pk-result').hidden=s.phase!=='complete';
 if(s.phase==='complete')renderResult(s);
}
function updateActions(s){
 const playing=s?.phase==='playing',allowed=playing&&!actionBusy&&(spectator||(!locked&&confirmedSeat===s.actor));
 $('#pk-action-panel').hidden=!playing;
 for(const id of ['#pk-fold','#pk-check','#pk-call','#pk-allin','#pk-raise-button','#pk-raise'])$(id).disabled=!allowed;
 $('#pk-hide').hidden=spectator;$('#pk-hide').disabled=!playing;
 if(!playing)return;
 const legal=s.legal;
 $('#pk-action-title').textContent=allowed?'轮到 '+s.players[s.actor].name+(spectator?' · 手牌公开':''):'等待 '+s.players[s.actor].name+' 确认身份';
 $('#pk-action-context').textContent=allowed?(legal.canCheck?'本轮无需跟注，可以过牌或主动下注。':'当前需要跟注 '+legal.call+(legal.call<legal.toCall?'（剩余筹码不足，跟注即全下）。':'。')):'底牌已收起，请先完成全屏交接。';
 $('#pk-check').hidden=!legal.canCheck;$('#pk-call').hidden=legal.canCheck;$('#pk-call').textContent='跟注 '+legal.call;
 $('#pk-allin').disabled=!allowed||!legal.canAllIn;
 const fullRaise=legal.canRaise&&legal.maxRaiseTo>=legal.minRaiseTo;
 $('#pk-raise-button').disabled=!allowed||!fullRaise;$('#pk-raise').disabled=!allowed||!fullRaise;
 $('#pk-raise-button').textContent=s.currentBet?'确认加注':'确认下注';
 $('#pk-raise').min=String(legal.minRaiseTo);$('#pk-raise').max=String(legal.maxRaiseTo);$('#pk-raise').value=String(Math.min(legal.minRaiseTo,legal.maxRaiseTo));
 $('#pk-raise-help').textContent=fullRaise?'填写本轮总投入；最低 '+legal.minRaiseTo+'，最多 '+legal.maxRaiseTo+'。':!legal.raiseReopened?'未重新开放加注，可跟注或弃牌。':legal.canRaise?'筹码不足以完整加注，可选择全下。':'当前没有可继续跟注的对手。';
}
function renderResult(s){
 const gains=s.players.map((p,i)=>({p,i,amount:s.result.payouts[i],returned:s.result.returns[i]})).filter(x=>x.amount||x.returned);
 $('#pk-result-title').textContent=s.result.kind==='fold'?s.players[s.result.payouts.findIndex(x=>x>0)].name+' 收下底池':'逐家揭晓完成';
 $('#pk-payouts').replaceChildren(...gains.map(({p,amount,returned})=>{
  const row=make('div','pk-payout-row');row.append(make('strong','',p.name),make('span','',(amount?'分得 '+amount+' 筹码':'')+(returned?(amount?' · ':'')+'退回未跟注筹码 '+returned:'')));return row;
 }));
 $('#pk-side-pots').replaceChildren(...s.result.pots.map((pot,i)=>make('p','',(i?'边池 '+i:'主池')+' · '+pot.amount+' → '+pot.winners.map(j=>s.players[j].name).join('、'))));
 $('#pk-result-help').textContent=s.result.kind==='fold'?'其他玩家均已弃牌，本手直接结束，不公开底牌。':'已按牌型比较并分配主池、边池；平局均分，零散筹码按庄家左侧顺序分配。';
 const next=s.players.filter(p=>p.stack>0).length>=2;$('#pk-next-hand').disabled=!next;$('#pk-next-hand').textContent=next?'下一手，轮换庄家':'只剩一位玩家有筹码，请重新开桌';
 if(s.result.kind==='showdown')s.players.forEach((p,i)=>{if(p.inHand)seatNodes[i].hand.textContent=(p.folded?'已弃牌 · ':'')+engine.handName(i)});
}
function pauseCeremony(){
 ceremonyEpoch++;ceremonyRunning=false;
 for(const item of ceremonyTimers){clearTimeout(item.timer);item.resolve(false)}ceremonyTimers.clear();
 for(const seat of seatNodes)seat.el.classList.remove('pk-revealing');
}
function waitCeremony(ms,epoch){return new Promise(resolve=>{if(epoch!==ceremonyEpoch){resolve(false);return}const item={resolve,timer:0};item.timer=setTimeout(()=>{ceremonyTimers.delete(item);resolve(epoch===ceremonyEpoch)},ms);ceremonyTimers.add(item)})}
async function runCeremony(){
 if(!engine||state().phase!=='showdown'||!active||document.hidden||!windowActive||confirmDialog.open||ceremonyRunning)return;
 ceremonyRunning=true;const epoch=ceremonyEpoch;
 const sequence=state().players.filter(p=>p.inHand).map(p=>p.index);
 renderHands();
 while(revealCursor<sequence.length){
  if(epoch!==ceremonyEpoch||!active||document.hidden||!windowActive){ceremonyRunning=false;return}
  const index=sequence[revealCursor],p=state().players[index],seat=seatNodes[index];
  $('#pk-showdown-progress').textContent='座位 '+(index+1)+' · '+p.name+'，请揭晓。';$('#pk-reveal-count').textContent=(revealCursor+1)+' / '+sequence.length;
  for(const node of seatNodes)node.el.classList.remove('pk-revealing');seat.el.classList.add('pk-revealing');
  if(!await waitCeremony(reduced()?160:260,epoch))return;
  revealed.add(index);renderFaces(index,{flip:!spectator});seat.el.dataset.pkRevealed='true';
  if(!await waitCeremony(reduced()?400:700,epoch))return;
  seat.hand.textContent=(p.folded?'已弃牌 · ':'')+engine.handName(index);
  $('#pk-showdown-progress').textContent=p.name+' · '+engine.handName(index)+(p.folded?'（已弃牌，不参与分配）':'');
  if(!await waitCeremony(reduced()?280:420,epoch))return;
  revealCursor++;seat.el.classList.remove('pk-revealing');
 }
 if(epoch!==ceremonyEpoch)return;
 ceremonyRunning=false;engine.finishShowdown();renderPublic();renderHands();
 $('#pk-result-title').tabIndex=-1;$('#pk-result-title').focus({preventScroll:true});
}
function displayPhase(){
 if(!engine)return;
 const s=state();renderPublic();
 if(!active)return;
 if(s.phase==='playing'){
  if(spectator){closeCurtain();renderHands()}
  else if(locked||confirmedSeat!==s.actor)showHandoff();else renderHands();
 }else{
  closeCurtain();renderHands();if(s.phase==='showdown')runCeremony();
 }
}
function act(type,target){
 if(!engine||actionBusy||state().phase!=='playing'||(!spectator&&(locked||confirmedSeat!==state().actor)))return;
 try{engine.validate(type,target)}catch(e){error('#pk-action-error',e.message,type==='raise'?$('#pk-raise'):null);return}
 clearError('#pk-action-error');actionBusy=true;
 // On private turns, erase faces and open a fully opaque modal before advancing the state.
 if(!spectator){locked=true;confirmedSeat=null;showHandoff()}
 try{engine.act(type,target)}catch(e){error('#pk-action-error',e.message)}
 actionBusy=false;displayPhase();
}
function nameFields(){
 const previous=[...$('#pk-name-fields').querySelectorAll('input')].map(el=>el.value),count=Number($('#pk-count').value);
 $('#pk-name-fields').replaceChildren();
 for(let i=0;i<count;i++){
  const label=make('label','pk-name-label','座位 '+(i+1));const input=document.createElement('input');input.id='pk-name-'+i;input.value=previous[i]||'玩家'+(i+1);input.maxLength=18;input.autocomplete='off';input.setAttribute('aria-describedby','pk-setup-error');label.htmlFor=input.id;label.append(input);$('#pk-name-fields').append(label);
 }
}
function startTable(){
 const names=[...$('#pk-name-fields').querySelectorAll('input')].map(el=>el.value.trim());
 const stack=Number($('#pk-stack').value),smallBlind=Number($('#pk-small-blind').value);
 clearError('#pk-setup-error');$('#pk-setup').querySelectorAll('[aria-invalid]').forEach(el=>el.removeAttribute('aria-invalid'));
 const empty=names.findIndex(n=>!n);if(empty>=0){error('#pk-setup-error','请填写每位玩家的名字。',$('#pk-name-'+empty));return}
 if(!Number.isSafeInteger(stack)||stack<100||stack>100000){error('#pk-setup-error','初始筹码请填写 100—100000 之间的整数。',$('#pk-stack'));return}
 if(!Number.isSafeInteger(smallBlind)||smallBlind<1||smallBlind>10000||stack<smallBlind*4){error('#pk-setup-error','请填写有效小盲；初始筹码至少为小盲的 4 倍。',$('#pk-small-blind'));return}
 try{const candidate=new Holdem({names,stack,smallBlind});candidate.startHand();pauseCeremony();eraseHands();engine=candidate;revealed.clear();revealCursor=0;exposedThisHand=spectator;confirmedSeat=null;locked=!spectator;boardStamp='';buildSeats(state());displayPhase()}catch(e){error('#pk-setup-error',e.message)}
}
function nextHand(){
 if(!engine||state().phase!=='complete')return;
 pauseCeremony();eraseHands();revealed.clear();revealCursor=0;confirmedSeat=null;locked=!spectator;exposedThisHand=spectator;boardStamp='';
 try{engine.startHand();for(const seat of seatNodes)delete seat.el.dataset.pkRevealed;displayPhase()}catch(e){error('#pk-action-error',e.message)}
}
function ask({title,description,accept}){
 if(confirmDialog.open)return Promise.resolve(false);
 pauseCeremony();confirmFocus=document.activeElement;$('#pk-confirm-title').textContent=title;$('#pk-confirm-description').textContent=description;$('#pk-confirm-accept').textContent=accept;
 return new Promise(resolve=>{confirmResolve=resolve;confirmDialog.showModal();$('#pk-confirm-cancel').focus({preventScroll:true})});
}
function answer(value){const resolve=confirmResolve;confirmResolve=null;confirmDialog.close();if(confirmFocus?.isConnected)confirmFocus.focus({preventScroll:true});resolve?.(value)}
async function toggleSpectator(){
 const requested=modeSwitch.checked;modeSwitch.checked=spectator;if(requested===spectator)return;
 if(!requested){
  spectator=false;locked=true;confirmedSeat=null;eraseHands();pauseCeremony();updateModeNotice();displayPhase();return;
 }
 if(engine){
  const accepted=await ask({title:'开启旁观模式？',description:'所有玩家的两张底牌会立即公开，并持续显示“观战模式”标识。请确认同桌所有玩家已经知情；关闭后也无法撤回已看过的信息。',accept:'所有玩家知情，公开手牌'});
  if(!accepted){displayPhase();return}
 }
 spectator=true;locked=false;confirmedSeat=null;if(engine)exposedThisHand=true;closeCurtain();updateModeNotice();displayPhase();
}
async function newTable(){
 const accepted=await ask({title:'重新开一桌？',description:'当前牌局、筹码和行动记录会清空，返回座位设置。其他三个功能页和题库不会改变。',accept:'重新开桌'});
 if(!accepted){displayPhase();return}
 pauseCeremony();eraseHands();closeCurtain();engine=null;seatNodes=[];revealed.clear();revealCursor=0;confirmedSeat=null;locked=true;exposedThisHand=false;$('#pk-seats').replaceChildren();$('#pk-live').hidden=true;$('#pk-setup').hidden=false;app.dataset.phase='setup';app.dataset.view='private';updateModeNotice();$('#pk-count').focus();
}
bind('#pk-confirm-player',()=>{
 if(!engine||spectator||state().phase!=='playing'||!active)return;
 confirmedSeat=state().actor;locked=false;closeCurtain();renderPublic();renderHands();$('#pk-action-title').tabIndex=-1;$('#pk-action-title').focus({preventScroll:true});
});
bind('#pk-leave',()=>{locked=true;confirmedSeat=null;eraseHands();closeCurtain();window.GameUI.switchTab('game');$('#nav-game').focus({preventScroll:true})});
curtain.addEventListener('cancel',e=>{e.preventDefault();$('#pk-curtain-tip').textContent='请确认身份后再查看底牌，或选择先离桌。'});
bind('#pk-confirm-cancel',()=>answer(false));bind('#pk-confirm-accept',()=>answer(true));confirmDialog.addEventListener('cancel',e=>{e.preventDefault();answer(false)});
$('#pk-count').addEventListener('change',nameFields);$('#pk-setup').addEventListener('submit',e=>{e.preventDefault();startTable()});
$('#pk-setup').addEventListener('input',e=>{if(e.isComposing)return;e.target.removeAttribute('aria-invalid');clearError('#pk-setup-error')});
modeSwitch.addEventListener('change',toggleSpectator);
bind('#pk-fold',()=>act('fold'));bind('#pk-check',()=>act('check'));bind('#pk-call',()=>act('call'));bind('#pk-allin',()=>act('allin'));
$('#pk-raise-form').addEventListener('submit',e=>{e.preventDefault();act('raise',Number($('#pk-raise').value))});
$('#pk-raise').addEventListener('input',()=>{$('#pk-raise').removeAttribute('aria-invalid');clearError('#pk-action-error')});
bind('#pk-hide',showHandoff);bind('#pk-next-hand',nextHand);bind('#pk-new-table',newTable);
document.addEventListener('app:tab-change',e=>{
 const next=e.detail==='poker';
 if(!next&&active){pauseCeremony();if(!spectator){eraseHands();locked=true;confirmedSeat=null}closeCurtain()}
 active=next;if(active)displayPhase();
});
function suspend(){
 if(!engine||!active)return;
 if(state().phase==='showdown'){pauseCeremony();if(!spectator)eraseHands()}
 if(state().phase==='playing'&&!spectator)showHandoff();
}
window.addEventListener('blur',()=>{windowActive=false;suspend()});
window.addEventListener('focus',()=>{windowActive=true;if(active&&engine)displayPhase()});
document.addEventListener('visibilitychange',()=>{if(document.hidden)suspend();else if(active&&engine)displayPhase()});
window.addEventListener('pagehide',()=>{pauseCeremony();if(!spectator){eraseHands();locked=true;confirmedSeat=null}closeCurtain()});
window.addEventListener('pageshow',e=>{if(e.persisted&&active&&engine)displayPhase()});
nameFields();updateModeNotice();
~~~~~~~~~~

## 40. `/workspace/output/poker-edition/src/poker.css`

~~~~~~~~~~
/* Poker uses the established sunset colors and native app controls. */
html[data-active-tab="poker"] .hero{display:none}
html[data-active-tab="poker"] #pet3d-system,html[data-active-tab="poker"] .pet3d-launcher{display:none}
html[data-active-tab="poker"] .app-main{padding-top:28px}
html[data-active-tab="poker"] .nav-tabs{gap:4px}
.pk-shell{--pk-felt:#15313D;--pk-line:#856D7B;--pk-text:var(--ink);color:var(--pk-text)}
.pk-shell button,.pk-curtain button{min-height:44px;font-family:var(--font)}
.pk-toolbar{position:sticky;top:0;z-index:65;display:flex;justify-content:space-between;align-items:center;gap:20px;padding:21px 26px;background:#1B293B;border:1px solid var(--surface-line);border-radius:22px;box-shadow:0 8px 25px #070E1919}
.pk-toolbar h2{font-size:28px;font-weight:650;letter-spacing:2px;line-height:1.4}
.pk-eyebrow{font-size:11px;color:var(--soft-pink);letter-spacing:1.4px;margin-bottom:7px}
.pk-subtitle{font-size:12px;color:var(--muted);margin-top:6px}
.pk-mode-switch{position:relative;display:flex;align-items:center;gap:14px;cursor:pointer;padding:12px 15px;background:#283046;border:1px solid var(--pk-line);border-radius:14px;min-height:68px;user-select:none}
.pk-mode-switch strong{display:block;font-size:14px;font-weight:600}
.pk-mode-switch small{display:block;font-size:11px;color:var(--muted);margin-top:4px}
.pk-mode-switch input{position:absolute;right:15px;width:44px;height:28px;opacity:0;min-height:0;padding:0;margin:0}
.pk-switch-track{width:44px;height:26px;border-radius:16px;background:#3F4355;border:1px solid #A38D9D;position:relative;pointer-events:none;flex:none}
.pk-switch-track::after{content:"";position:absolute;top:3px;left:3px;width:18px;height:18px;border-radius:50%;background:#E9D6D9;transition:transform .18s,background .18s}
.pk-mode-switch input:checked+.pk-switch-track{background:#F3AB98;border-color:#F3AB98}
.pk-mode-switch input:checked+.pk-switch-track::after{transform:translateX(18px);background:#251D29}
.pk-mode-switch input:focus-visible+.pk-switch-track{outline:3px solid var(--soft-amber);outline-offset:5px}
.pk-mode-message{font-size:12px;line-height:1.9;color:var(--muted);padding:13px 4px;min-height:48px}
.pk-mode-message.pk-public-message{color:var(--soft-amber);font-weight:600}
.pk-exposed-note{font-size:12px;line-height:1.8;padding:11px 15px;background:#453343;border:1px solid #B38C9F;border-radius:12px;color:#FFE0CC;margin-bottom:16px}
.pk-setup{background:#1B293B;border:1px solid var(--surface-line);border-radius:22px;padding:27px}
.pk-setup-intro{display:flex;align-items:center;gap:18px;margin-bottom:26px}
.pk-seal{display:grid;place-items:center;flex:none;width:68px;height:68px;background:#352C43;border:1px solid #86697B;border-radius:20px;font-family:Georgia,serif;font-size:40px;color:var(--soft-pink);transform:rotate(-5deg)}
.pk-setup-intro h3{font-size:21px;font-weight:600}
.pk-setup-intro p{font-size:12px;color:var(--muted);margin-top:7px}
.pk-config-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:18px;padding-bottom:22px;border-bottom:1px solid var(--surface-line)}
.pk-config-grid label,.pk-name-grid label{display:flex;flex-direction:column;gap:8px;font-size:12px;color:var(--muted)}
.pk-config-grid input,.pk-config-grid select,.pk-name-grid input{width:100%;min-width:0;font-size:14px;min-height:46px}
.pk-name-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:18px;margin-top:22px}
.pk-field-hint{font-size:11px;color:var(--muted);line-height:1.8;margin:0}
.pk-setup-bottom{display:flex;align-items:center;justify-content:space-between;gap:24px;margin-top:25px;padding-top:22px;border-top:1px solid var(--surface-line)}
.pk-setup-bottom p{font-size:12px;color:var(--muted);max-width:430px;line-height:1.9}
.pk-primary,.pk-shell .pk-primary{background:var(--primary);color:var(--on-primary);font-weight:650;border-radius:12px;padding:11px 18px;border:1px solid var(--primary)}
.pk-secondary{background:#3A3248;color:var(--soft-pink);border:1px solid #9A7B90;border-radius:12px;padding:11px 18px;font-weight:600}
.pk-quiet{background:transparent;color:var(--soft-pink);font-size:12px;border:1px solid var(--pk-line);border-radius:10px;padding:9px 13px;min-height:40px}
.pk-live-header{display:flex;justify-content:space-between;align-items:center;gap:15px;padding:17px 5px 19px}
.pk-round{display:flex;align-items:center;gap:12px}
.pk-round strong{font-size:17px;font-weight:600}
.pk-round>span{font-size:11px;padding:5px 10px;background:#433248;color:var(--soft-pink);border:1px solid #8B6C81;border-radius:7px}
.pk-table-meta{display:flex;gap:14px;align-items:center;font-size:12px;color:var(--muted)}
.pk-table{position:relative;background:linear-gradient(155deg,#193846,#112A36);border:1px solid #917480;border-radius:32px;padding:24px;box-shadow:inset 0 0 0 6px #0C1C2B,0 16px 40px #03081226;overflow:hidden}
.pk-table::before{content:"";position:absolute;inset:14px;border:1px solid #9E809033;border-radius:23px;pointer-events:none}
.pk-board-area{position:relative;display:flex;align-items:center;flex-direction:column;padding:1px 0 20px;min-height:238px}
.pk-table-wordmark{font-size:10px;letter-spacing:4px;color:#C6ADB8;margin:0 0 13px}
.pk-pot{display:flex;align-items:center;gap:10px;color:#E7C6C1;margin-bottom:17px}
.pk-pot>span:first-child{font-size:12px}
.pk-pot strong{font-size:29px;color:#FFE1C9;font-weight:650;font-variant-numeric:tabular-nums;line-height:1}
.pk-chip-symbol{width:16px;height:16px;border:3px dashed #F3AB98;outline:1px solid #F3AB98;border-radius:50%;margin-left:3px}
.pk-community{display:flex;justify-content:center;gap:10px;width:100%;min-height:90px}
.pk-card{position:relative;display:block;flex:none;width:62px;height:88px;border:1px solid #D9CBBF;border-radius:9px;background:#FFF4E8;color:#23304B;box-shadow:0 4px 9px #07121F33;overflow:hidden;font-family:var(--font);font-variant-numeric:tabular-nums;transform-origin:50% 50%;backface-visibility:hidden}
.pk-card.pk-red{color:#A53E53}
.pk-card-corner{position:absolute;left:7px;top:5px;display:flex;flex-direction:column;align-items:center;line-height:1.1}
.pk-card-corner strong{font-size:18px;font-weight:750}
.pk-card-corner span{font-size:14px}
.pk-card-pip{position:absolute;left:50%;top:54%;transform:translate(-50%,-50%);font-size:31px;line-height:1}
.pk-card-foot{position:absolute;right:7px;bottom:5px;font-size:13px;transform:rotate(180deg);font-weight:700}
.pk-board-slot{display:block;width:62px;height:88px;border:1px dashed #AC8D9B;border-radius:9px;background:#122A3666;flex:none}
.pk-round-status{font-size:12px;line-height:1.7;color:#E8CED0;text-align:center;min-height:21px;margin-top:14px}
.pk-seats{position:relative;display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:17px}
.pk-seat{position:relative;min-width:0;background:#1B2839;border:1px solid #726275;border-radius:18px;padding:15px 15px 13px;transition:border-color .18s;min-height:244px;box-shadow:0 5px 14px #07111D24}
.pk-seat.pk-current{border-color:#F3AB98;box-shadow:0 0 0 1px #F3AB9866}
.pk-seat.pk-folded{background:#232735}
.pk-seat.pk-sitting-out{background:#1C2634}
.pk-seat.pk-revealing{border-color:#FFE2BE;box-shadow:0 0 0 2px #FFE2BE66}
.pk-seat.pk-winner{border-color:#E9C37D}
.pk-seat-header{display:flex;justify-content:space-between;align-items:center;gap:7px;min-height:28px}
.pk-seat-identity{display:flex;gap:8px;align-items:center;min-width:0}
.pk-seat-number{color:#D0BEC7;font-size:11px;flex:none;display:grid;place-items:center;border-radius:50%;width:23px;height:23px;border:1px solid #8B748B}
.pk-seat-name{font-size:14px;font-weight:650;overflow-wrap:anywhere;line-height:1.5}
.pk-seat-roles{display:flex;gap:5px;flex:none;align-items:center}
.pk-dealer{font-size:11px;background:#E2D8CB;color:#243048;border:1px solid #EEE2D6;border-radius:50%;width:22px;height:22px;display:grid;place-items:center;font-weight:750}
.pk-blind{font-size:9px;letter-spacing:.3px;padding:3px 5px;color:#FFE1C9;background:#423349;border:1px solid #94748A;border-radius:5px}
.pk-observer-badge{display:block;position:relative;margin-top:9px;text-align:center;background:#F3AB98;color:#251D29;border-radius:6px;font-size:11px;font-weight:750;line-height:1.5;padding:4px 7px;letter-spacing:1px}
.pk-hole-area{display:flex;justify-content:center;align-items:center;gap:9px;min-height:101px;margin:9px 0 2px}
.pk-back{position:relative;display:block;flex:none;width:59px;height:84px;box-sizing:border-box;border:1px solid #AF899E;border-radius:8px;background:repeating-linear-gradient(40deg,#47364F 0px,#47364F 3px,#342E46 3px,#342E46 7px);box-shadow:inset 0 0 0 4px #242B3F}
.pk-back::after{content:"✦";position:absolute;inset:0;display:grid;place-items:center;color:#E4B7C5;font-size:22px}
.pk-seat-status{font-size:11px;line-height:1.7;color:#E5BBC2;text-align:center;min-height:19px;margin:4px 0 7px}
.pk-seat-chips{display:flex;align-items:center;justify-content:space-between;gap:7px;border-top:1px solid #66566A;padding-top:10px;font-variant-numeric:tabular-nums}
.pk-seat-chips strong{font-size:13px;color:#FFE2BE;font-weight:650}
.pk-seat-chips>span{font-size:11px;color:var(--muted)}
.pk-hand-name{font-size:12px;color:#FFE2BE;text-align:center;min-height:21px;margin-top:6px;line-height:1.7}
.pk-action-panel{margin-top:20px;background:#1B293B;border:1px solid var(--surface-line);border-radius:20px;padding:22px}
.pk-action-heading{display:flex;justify-content:space-between;align-items:flex-start;gap:20px;margin-bottom:19px}
.pk-action-heading h3{font-size:18px;font-weight:650;line-height:1.7}
.pk-action-heading p{font-size:12px;line-height:1.8;color:var(--muted);margin-top:4px}
.pk-action-heading>.pk-quiet{font-size:11px;flex:none}
.pk-action-buttons{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:11px}
.pk-action-buttons button{min-width:0;font-size:13px;padding:12px 10px}
.pk-fold{background:#49303F;color:#FFCFD6;border:1px solid #A1758D;border-radius:12px}
.pk-allin{background:#413348;color:#FFE2BE;border:1px solid #B6939E;border-radius:12px;font-weight:700}
.pk-raise-form{display:grid;grid-template-columns:minmax(0,1fr) auto;align-items:end;gap:10px 14px;margin-top:18px;border-top:1px solid var(--surface-line);padding-top:16px}
.pk-raise-form label{font-size:12px;color:var(--muted);display:flex;align-items:center;gap:13px;min-width:0}
.pk-raise-form input{width:145px;min-width:0;font-size:14px;flex:1;max-width:280px}
.pk-raise-form .pk-field-hint{grid-column:1/-1;min-height:20px}
.pk-raise-form button{font-size:12px;min-width:105px}
.pk-showdown-panel{display:flex;align-items:center;gap:16px;margin-top:20px;padding:22px;border:1px solid #B18B9E;border-radius:20px;background:#3A2F44;min-height:100px}
.pk-showdown-icon{display:grid;place-items:center;border:1px solid #C89FAD;border-radius:50%;width:47px;height:47px;flex:none;color:#FFE2BE;font-size:25px}
.pk-showdown-panel h3{font-size:20px;line-height:1.6;color:#FFE2BE}
.pk-showdown-panel p{font-size:12px;line-height:1.9;color:#F1D9DD}
#pk-reveal-count{margin-left:auto;font-size:14px;white-space:nowrap;color:#FFE2BE;font-variant-numeric:tabular-nums}
.pk-result{background:#2A2F43;border:1px solid #BE9698;border-radius:22px;padding:25px;margin-top:20px}
.pk-result h3{font-size:23px;color:#FFE2BE;line-height:1.6;margin-bottom:13px}
.pk-payout-row{display:flex;align-items:center;justify-content:space-between;gap:15px;font-size:14px;padding:10px 0;border-bottom:1px solid #756174;line-height:1.8}
.pk-payout-row strong{font-weight:600}
.pk-payout-row>span{color:#FFD3C5;font-variant-numeric:tabular-nums;text-align:right}
.pk-side-pots{margin-top:13px;font-size:12px;color:var(--muted);line-height:1.9}
#pk-result-help{font-size:12px;color:var(--muted);line-height:1.9;margin:12px 0 18px}
.pk-history,.pk-rules{margin-top:20px;background:#1A2639;border:1px solid var(--surface-line);border-radius:16px;padding:12px 17px;font-size:12px;color:var(--muted);line-height:1.9}
.pk-history summary,.pk-rules summary{cursor:pointer;color:var(--soft-pink);min-height:30px;padding:4px 0}
.pk-history ol{padding-left:22px;margin:10px 0}
.pk-history li{margin:5px 0}
.pk-rules>div{margin-top:9px}
.pk-rules p+p{margin-top:9px}
.pk-curtain{position:fixed;inset:0;margin:0;width:100vw;height:100vh;height:100dvh;max-width:none;max-height:none;box-sizing:border-box;border:0;border-radius:0;padding:max(30px,env(safe-area-inset-top)) 24px max(30px,env(safe-area-inset-bottom));background:#0D1524;color:#FFF2E9;overflow:auto;overscroll-behavior:contain;font-family:var(--font);outline:none}
.pk-curtain::backdrop{background:#0D1524}
.pk-curtain[open]{display:grid;place-items:center}
.pk-curtain-content{width:min(100%,480px);text-align:center;display:flex;flex-direction:column;align-items:center;gap:18px;margin:auto}
.pk-lock-symbol{width:80px;height:80px;border:1px solid #8A6B7F;border-radius:26px;background:#2B263C;display:grid;place-items:center;color:#FFD3C5;margin-bottom:5px}
.pk-lock-symbol svg{width:46px;height:46px}
.pk-curtain .pk-eyebrow{color:#FFD3C5;margin:0;font-size:12px}
.pk-curtain h2{font-size:29px;line-height:1.7;font-weight:650;overflow-wrap:anywhere;letter-spacing:.4px}
#pk-curtain-help{font-size:14px;color:#D0BEC7;line-height:1.9;max-width:29em}
.pk-curtain .pk-primary{width:100%;margin-top:10px;min-height:52px;white-space:normal;overflow-wrap:anywhere;line-height:1.8;padding:13px 18px;font-size:15px}
.pk-curtain .pk-quiet{font-size:13px;color:#FFD3C5;min-height:44px;padding:10px 16px;background:#0D1524}
.pk-curtain-tip{font-size:12px;color:#E3BAC8;min-height:22px;line-height:1.9}
.pk-confirm{color:var(--ink)}
.pk-confirm::backdrop{background:#0D1524}
.pk-confirm .confirm-actions{margin-top:22px;flex-wrap:wrap}
.pk-confirm .confirm-actions button{min-height:44px;font-size:13px}
.pk-flip{animation:pk-flip 460ms cubic-bezier(.18,.72,.22,1) both;animation-delay:var(--pk-flip-delay,0ms);will-change:transform,opacity}
.pk-seat.pk-revealing::after{content:"";position:absolute;inset:0;border:1px solid #FFE2BE;border-radius:18px;pointer-events:none;animation:pk-seat-glow 1380ms ease-out both}
.pk-shell[data-spectator="true"] .pk-seat.pk-revealing .pk-hole-card{animation:pk-observer-lift 1000ms ease-in-out both}
@keyframes pk-flip{0%{transform:perspective(700px) rotateY(90deg) translateY(5px);opacity:0}25%{opacity:1}100%{transform:perspective(700px) rotateY(0deg) translateY(0);opacity:1}}
@keyframes pk-seat-glow{0%,100%{opacity:.25}35%,65%{opacity:1}}
@keyframes pk-observer-lift{0%,100%{transform:translateY(0)}45%{transform:translateY(-4px)}}
@media(hover:hover) and (pointer:fine){.pk-primary:hover:not(:disabled){background:#FFC2AD;color:var(--on-primary)}.pk-secondary:hover:not(:disabled),.pk-quiet:hover:not(:disabled),.pk-allin:hover:not(:disabled){background:#493449;color:#FFE2BE}.pk-fold:hover:not(:disabled){background:#644052;color:#FFE1E5}.pk-mode-switch:hover{border-color:#E1B4BF}}
@media(max-width:950px){.pk-toolbar{padding:19px 22px}.pk-seats{grid-template-columns:repeat(2,minmax(0,1fr))}.pk-table{padding:22px}.pk-seat{min-height:241px}.pk-board-area{min-height:235px}}
@media(max-width:600px){
 .header-content .nav-tabs{gap:3px}.header-content .nav-tab{font-size:12px;padding:11px 7px;min-width:0}.pk-toolbar{padding:18px 16px;gap:10px;border-radius:19px;align-items:flex-start;position:relative;top:auto}.pk-toolbar h2{font-size:23px;letter-spacing:1px}.pk-eyebrow{font-size:10px;letter-spacing:.5px}.pk-subtitle{font-size:10px;line-height:1.8;max-width:12em}.pk-mode-switch{padding:10px 9px;gap:8px;border-radius:12px;min-height:66px}.pk-mode-switch strong{font-size:12px}.pk-mode-switch small{font-size:9px;max-width:9em;line-height:1.7}.pk-switch-track{width:38px;height:24px}.pk-switch-track::after{width:16px;height:16px;top:3px;left:3px}.pk-mode-switch input{right:9px;width:38px;height:28px}.pk-mode-switch input:checked+.pk-switch-track::after{transform:translateX(14px)}
 .pk-mode-message{font-size:11px;padding:11px 3px;min-height:56px}.pk-exposed-note{font-size:11px;padding:10px 12px}.pk-setup{padding:20px 16px;border-radius:20px}.pk-setup-intro{gap:12px;align-items:flex-start;margin-bottom:22px}.pk-seal{width:46px;height:51px;border-radius:14px;font-size:30px}.pk-setup-intro h3{font-size:17px;line-height:1.7}.pk-setup-intro p{font-size:11px;line-height:1.9}.pk-config-grid{grid-template-columns:1fr 1fr;gap:14px}.pk-config-grid label:last-child{grid-column:1/-1}.pk-name-grid{grid-template-columns:1fr 1fr;gap:14px}.pk-config-grid label,.pk-name-grid label{font-size:11px;gap:7px}.pk-config-grid input,.pk-config-grid select,.pk-name-grid input{font-size:13px;padding:11px}.pk-setup-bottom{flex-direction:column;align-items:stretch;gap:16px;margin-top:20px;padding-top:18px}.pk-setup-bottom p{font-size:11px}.pk-setup-bottom .pk-primary{font-size:13px;width:100%}
 .pk-live-header{gap:10px;padding:13px 2px 15px}.pk-round{gap:7px}.pk-round strong{font-size:14px}.pk-round>span{font-size:10px;padding:4px 7px}.pk-table-meta{gap:8px;font-size:10px}.pk-table-meta .pk-quiet{padding:8px;font-size:10px;min-height:36px}.pk-table{padding:17px 12px;border-radius:23px;box-shadow:inset 0 0 0 4px #0C1C2B,0 12px 30px #03081226}.pk-table::before{inset:9px;border-radius:17px}.pk-board-area{min-height:206px;padding-bottom:18px}.pk-table-wordmark{font-size:9px;letter-spacing:3px;margin-bottom:12px}.pk-pot{margin-bottom:14px;gap:8px}.pk-pot>span:first-child{font-size:11px}.pk-pot strong{font-size:25px}.pk-chip-symbol{width:14px;height:14px}.pk-community{gap:6px;min-height:76px}.pk-community .pk-card,.pk-board-slot{width:48px;height:69px;border-radius:7px}.pk-community .pk-card-corner{top:4px;left:5px}.pk-community .pk-card-corner strong{font-size:15px}.pk-community .pk-card-corner span{font-size:11px}.pk-community .pk-card-pip{font-size:23px}.pk-community .pk-card-foot{font-size:10px;right:5px;bottom:4px}.pk-round-status{font-size:11px;line-height:1.8;margin-top:9px;min-height:20px}.pk-seats{gap:11px}.pk-seat{padding:11px 9px 10px;border-radius:14px;min-height:221px}.pk-seat-header{gap:4px;align-items:flex-start;min-height:27px}.pk-seat-identity{gap:5px;align-items:flex-start}.pk-seat-number{width:18px;height:18px;font-size:9px;margin-top:1px}.pk-seat-name{font-size:12px;line-height:1.65}.pk-seat-roles{gap:3px;flex-wrap:wrap;max-width:44px;justify-content:flex-end}.pk-dealer{width:17px;height:17px;font-size:9px}.pk-blind{font-size:8px;padding:2px 3px}.pk-observer-badge{font-size:10px;letter-spacing:.5px;padding:4px;margin-top:6px}.pk-hole-area{gap:6px;min-height:87px;margin-top:7px}.pk-hole-area .pk-card{width:48px;height:71px;border-radius:6px}.pk-hole-area .pk-card-corner{left:5px;top:4px}.pk-hole-area .pk-card-corner strong{font-size:15px}.pk-hole-area .pk-card-corner span{font-size:10px}.pk-hole-area .pk-card-pip{font-size:23px}.pk-hole-area .pk-card-foot{font-size:10px;right:4px;bottom:3px}.pk-back{width:46px;height:68px;border-radius:6px}.pk-back::after{font-size:19px}.pk-seat-status{font-size:10px;min-height:18px;line-height:1.7}.pk-seat-chips{gap:5px;flex-wrap:wrap;padding-top:8px}.pk-seat-chips strong{font-size:11px}.pk-seat-chips>span{font-size:9px}.pk-hand-name{font-size:10px;line-height:1.7;min-height:18px;margin-top:4px}
 .pk-action-panel{padding:18px 14px;border-radius:18px;margin-top:17px}.pk-action-heading{gap:10px;flex-direction:column;margin-bottom:16px}.pk-action-heading h3{font-size:16px}.pk-action-heading p{font-size:11px}.pk-action-heading>.pk-quiet{min-height:36px;padding:8px 10px;font-size:10px}.pk-action-buttons{grid-template-columns:1fr 1fr;gap:9px}.pk-action-buttons button{font-size:12px;min-height:44px}.pk-raise-form{gap:10px;grid-template-columns:minmax(0,1fr) auto;margin-top:16px;padding-top:14px}.pk-raise-form label{font-size:10px;display:flex;flex-direction:column;align-items:flex-start;gap:6px}.pk-raise-form input{width:100%;max-width:none;padding:11px;font-size:13px}.pk-raise-form button{font-size:11px;min-width:88px;padding:11px 12px}.pk-field-hint{font-size:10px}.pk-showdown-panel{padding:18px 13px;gap:11px;margin-top:17px}.pk-showdown-icon{width:34px;height:34px;font-size:19px}.pk-showdown-panel h3{font-size:17px}.pk-showdown-panel p{font-size:10px}.pk-showdown-panel #pk-reveal-count{font-size:12px}.pk-result{padding:20px 16px;border-radius:19px;margin-top:17px}.pk-result h3{font-size:21px}.pk-payout-row{font-size:12px;align-items:start}.pk-payout-row>span{max-width:70%}.pk-side-pots,#pk-result-help{font-size:11px}.pk-result .pk-primary{font-size:12px;width:100%}.pk-history,.pk-rules{font-size:11px;margin-top:17px;padding:11px 14px}.pk-curtain{padding-left:22px;padding-right:22px}.pk-curtain h2{font-size:24px}.pk-curtain .pk-primary{font-size:13px}.pk-curtain #pk-curtain-help{font-size:12px;line-height:1.9}.pk-lock-symbol{width:69px;height:69px;border-radius:21px}.pk-curtain-content{gap:16px}.pk-curtain .pk-eyebrow{font-size:11px}
}
@media(max-width:350px){.header-content .nav-tab{font-size:11px;padding-inline:5px}.pk-toolbar{padding:16px 12px;gap:7px}.pk-toolbar h2{font-size:21px}.pk-mode-switch{padding:9px 7px;gap:6px}.pk-mode-switch strong{font-size:11px}.pk-mode-switch small{font-size:8px}.pk-mode-switch input{right:7px}.pk-subtitle{font-size:9px}.pk-table{padding-left:10px;padding-right:10px}.pk-community{gap:4px}.pk-community .pk-card,.pk-board-slot{width:42px;height:64px}.pk-seats{gap:8px}.pk-seat{padding-inline:7px}.pk-hole-area{gap:5px}.pk-hole-area .pk-card{width:43px;height:66px}.pk-back{width:42px;height:64px}.pk-seat-name{font-size:11px}.pk-blind{font-size:7px;padding:2px}.pk-seat-chips strong{font-size:10px}.pk-table-meta{gap:6px}.pk-table-meta .pk-quiet{font-size:9px;padding:7px}.pk-round strong{font-size:12px}.pk-round>span{font-size:9px}}
/* Honor motion preference while preserving the JS-controlled seat-by-seat ceremony. */
@media(prefers-reduced-motion:reduce){.pk-flip,.pk-seat.pk-revealing::after,.pk-shell[data-spectator="true"] .pk-seat.pk-revealing .pk-hole-card{animation:none!important}}
html[data-motion="reduced"] .pk-flip,html[data-motion="reduced"] .pk-seat.pk-revealing::after{animation:none!important}
@media(forced-colors:active){.pk-toolbar,.pk-setup,.pk-table,.pk-seat,.pk-action-panel,.pk-result,.pk-showdown-panel,.pk-curtain,.pk-confirm{background:Canvas;color:CanvasText;border:1px solid CanvasText}.pk-card{background:Canvas;color:CanvasText;border:2px solid CanvasText}.pk-card.pk-red{color:LinkText}.pk-back{background:Canvas;border:1px dashed CanvasText}.pk-curtain::backdrop,.pk-confirm::backdrop{background:Canvas}.pk-observer-badge{background:Highlight;color:HighlightText}.pk-board-slot{border-color:CanvasText}.pk-switch-track{background:Canvas;border-color:CanvasText}.pk-switch-track::after{background:CanvasText}.pk-primary,.pk-secondary,.pk-quiet,.pk-fold,.pk-allin{border:1px solid ButtonText}.pk-seat-name,.pk-seat-status,.pk-seat-chips strong,.pk-seat-chips>span{color:CanvasText}}
~~~~~~~~~~

## 41. `/tmp/build_poker.py`

~~~~~~~~~~
from pathlib import Path
import shutil,re
root=Path('/workspace/output/poker-edition');src=root/'src'
s=Path('/workspace/output/maogou-xindongju-sunset-v5.html').read_text()
s=s.replace('<html lang="zh-CN">','<html lang="zh-CN" data-active-tab="game">',1)
newtab='        <button class="nav-tab" id="nav-poker" role="tab" aria-selected="false" aria-controls="tab-poker" tabindex="-1" data-tab="poker">德州扑克</button>\n'
s=s.replace('      </nav>',newtab+'      </nav>',1)
s=s.replace('<footer class="app-footer">',(src/'poker-panel.html').read_text()+'\n<footer class="app-footer">',1)
s=s.replace('<script id="shared-actions">',(src/'poker-overlays.html').read_text()+'\n<script id="shared-actions">',1)
s=s.replace("this.state.currentTab = name;document.title=", "this.state.currentTab = name;document.documentElement.dataset.activeTab=name;document.dispatchEvent(new CustomEvent('app:tab-change',{detail:name}));document.title=",1)
s=s.replace("bank:'我的题库'}", "bank:'我的题库',poker:'德州扑克'}",1)
s=s.replace('日落微醺版 v5.0','日落微醺版 v6.0')
s=s.replace('</head>','<style id="poker-design">'+(src/'poker.css').read_text()+'</style></head>',1)
engine=(src/'poker-engine.js').read_text();marker="})(typeof globalThis!=='undefined'?globalThis:this,function(){";body=engine.split(marker,1)[1].rsplit('\n});',1)[0]
script="(()=>{\n'use strict';\nconst PokerRules=(()=>{"+body+'\n})();\n'+(src/'poker-ui.js').read_text()+'\n})();'
s=s.replace('</body>','<script id="poker-runtime">'+script+'</script></body>',1)
(src/'maogou-xindongju-poker-v6.html').write_text(s)
Path('/workspace/output/maogou-xindongju-poker-v6.html').write_text(s)
for n in ['verify.cjs','accessibility.cjs','actions.cjs']:
 if not (root/'tests'/n).exists():
  test=Path('/workspace/output/sunset-edition/tests',n).read_text().replace('../src/maogou-xindongju-sunset-v5.html','../src/maogou-xindongju-poker-v6.html')
  (root/'tests'/n).write_text(test)
for n in ['DESIGN.md','UX-CONTRACT.md','premium-ui.json']:
 if not (root/n).exists():shutil.copy2('/workspace/output/sunset-edition/'+n,root/n)
print('Built poker standalone:',len(s.encode()),'bytes')
~~~~~~~~~~

## 42. `/workspace/output/poker-edition/tests/poker-engine.cjs`

~~~~~~~~~~
const assert=require('node:assert/strict'),fs=require('node:fs'),path=require('node:path');
const {Holdem,evaluate,compare,splitPots,shuffledDeck}=require('../src/poker-engine.js');
const checks=[];
const C=(r,s=0)=>s*13+r-2;
const score=cards=>evaluate(cards).score;
const royal=[C(10,1),C(11,1),C(12,1),C(13,1),C(14,1),C(2),C(3)];
assert.deepEqual(score(royal),[8,14]);assert.equal(evaluate(royal).name,'皇家同花顺');
assert.deepEqual(score([C(14),C(2,1),C(3,2),C(4,3),C(5),C(9),C(13)]),[4,5]);
assert.deepEqual(score([C(14),C(14,1),C(14,2),C(13),C(13,1),C(13,2),C(2)]),[6,14,13]);
assert.ok(compare(score(royal),score([C(9),C(9,1),C(9,2),C(9,3),C(14),C(2),C(3)]))>0);checks.push('七选五、皇家同花顺、A2345、双三条葫芦和牌型比较');
const board=[C(2),C(3,1),C(7,2),C(9,3),C(11)];
const ps=[{hole:[C(14),C(14,1)],invested:50},{hole:[C(13),C(13,1)],invested:100},{hole:[C(12),C(12,1)],invested:150}].map(p=>({...p,inHand:true,folded:false}));
const pots=splitPots(ps,board,0);assert.deepEqual(pots.payouts,[150,100,0]);assert.deepEqual(pots.returns,[0,0,50]);assert.deepEqual(pots.pots.map(x=>x.amount),[150,100]);checks.push('主池、边池和未跟注筹码退回');
const tieBoard=[10,11,12,13,14].map(r=>C(r,1));
const tiePlayers=[{hole:[C(2),C(3)],invested:1,folded:true},{hole:[C(4),C(5)],invested:5},{hole:[C(6),C(7)],invested:5}].map(p=>({inHand:true,folded:false,...p}));
const tied=splitPots(tiePlayers,tieBoard,2);assert.deepEqual(tied.payouts,[0,6,5]);checks.push('平局按庄家左侧顺序分配零散筹码，弃牌者不参与');
const two=new Holdem({names:['甲','乙']});two.startHand();let s=two.publicState();assert.equal(s.dealer,0);assert.equal(s.sb,0);assert.equal(s.bb,1);assert.equal(s.actor,0);assert.equal(two.cardsFor(1).length,0);assert.ok(!('hole' in s.players[0]));two.act('call');two.act('check');assert.equal(two.publicState().street,'flop');assert.equal(two.publicState().actor,1);checks.push('双人庄家/盲注/行动顺序；公开快照不含底牌');
while(two.publicState().phase==='playing'){const legal=two.legal();two.act(legal.canCheck?'check':'call')}
assert.equal(two.publicState().phase,'showdown');assert.equal(two.publicState().board.length,5);assert.equal(two.publicState().result,null);two.finishShowdown();assert.equal(two.publicState().players.reduce((a,p)=>a+p.stack,0),2000);checks.push('四轮下注完整流转，摊牌仪式前不提前分配筹码');
const three=new Holdem({names:['甲','乙','丙']});three.startHand();assert.equal(three.publicState().actor,0);three.act('call');three.act('call');assert.equal(three.legal().canCheck,true);three.act('check');assert.equal(three.publicState().actor,1);checks.push('三人盲注、大盲选项与翻牌后行动顺序');
const short=new Holdem({names:['甲','乙','丙'],stacks:[1000,150,1000]});short.startHand();short.act('raise',100);short.act('allin');short.act('call');assert.equal(short.publicState().actor,0);assert.equal(short.legal().canRaise,false);assert.equal(short.legal().toCall,50);assert.throws(()=>short.act('raise',230));short.act('call');checks.push('不足一个完整加注的全下不重新开放已行动玩家的加注权');
const cumulative=new Holdem({names:['甲','乙','丙','丁'],stacks:[150,200,1000,1000]});cumulative.startHand();assert.equal(cumulative.publicState().actor,3);cumulative.act('raise',100);cumulative.act('allin');cumulative.act('allin');cumulative.act('call');assert.equal(cumulative.publicState().actor,3);assert.equal(cumulative.legal().canRaise,true);assert.equal(cumulative.legal().minRaiseTo,280);checks.push('多次短码全下累积达到完整加注后重新开放加注');
const checked=new Holdem({names:['甲','乙','丙'],stacks:[1000,1000,30]});checked.startHand();checked.act('call');checked.act('call');checked.act('check');checked.act('check');checked.act('allin');checked.act('call');assert.equal(checked.publicState().actor,1);assert.equal(checked.legal().canRaise,true);checked.act('raise',30);checks.push('过牌后面对短码首次下注仍可加注');
const tiny=new Holdem({names:['甲','乙'],stacks:[1000,5]});tiny.startHand();assert.equal(tiny.publicState().phase,'showdown');tiny.finishShowdown();assert.equal(tiny.publicState().players.reduce((a,p)=>a+p.stack,0),1005);checks.push('盲注不足、自动发完公共牌和未跟注退回');
const folded=new Holdem({names:['甲','乙']});folded.startHand();folded.act('fold');assert.equal(folded.publicState().phase,'complete');assert.equal(folded.publicState().result.kind,'fold');assert.equal(folded.cardsFor(1).length,0);assert.equal(folded.publicState().result.returns[1],10);checks.push('弃牌结束不公开手牌，并退回未跟注部分');
for(let run=0;run<180;run++){
 const count=2+run%5,game=new Holdem({names:Array.from({length:count},(_,i)=>'座位'+i),stack:1000,smallBlind:10});game.startHand();let moves=0;
 while(game.publicState().phase==='playing'){
  if(++moves>250)throw new Error('牌局未终止');
  const legal=game.legal(),roll=Math.random();
  if(roll<.1)game.act('fold');else if(roll<.23&&legal.canAllIn)game.act('allin');else if(roll<.4&&legal.canRaise&&legal.maxRaiseTo>=legal.minRaiseTo)game.act('raise',legal.minRaiseTo);else game.act(legal.canCheck?'check':'call');
 }
 if(game.publicState().phase==='showdown')game.finishShowdown();
 assert.equal(game.publicState().players.reduce((a,p)=>a+p.stack,0),count*1000);assert.ok(game.publicState().players.every(p=>Number.isInteger(p.stack)&&p.stack>=0));
 const deck=shuffledDeck();assert.equal(new Set(deck).size,52);
}
checks.push('180组随机牌局的筹码守恒、终止性和牌堆无重复');
const report={checks,randomHands:180};fs.writeFileSync(path.join(__dirname,'../poker-engine-verification.json'),JSON.stringify(report,null,2));console.log(JSON.stringify(report,null,2));
~~~~~~~~~~

## 43. `/workspace/output/poker-edition/tests/poker-browser.cjs`

~~~~~~~~~~
const {chromium}=require('playwright');
const assert=require('node:assert/strict'),fs=require('node:fs'),path=require('node:path'),http=require('node:http');
(async()=>{
 const root=path.resolve(__dirname,'..'),html=fs.readFileSync(path.join(root,'src/maogou-xindongju-poker-v6.html'),'utf8');
 const server=http.createServer((req,res)=>{res.writeHead(200,{'Content-Type':'text/html; charset=utf-8'});res.end(html)});await new Promise(r=>server.listen(0,'127.0.0.1',r));
 const browser=await chromium.launch({executablePath:'/usr/bin/chromium',args:['--no-sandbox']}),checks=[],errors=[];
 const context=await browser.newContext({viewport:{width:1280,height:1000}}),p=await context.newPage();p.setDefaultTimeout(7000);p.on('pageerror',e=>errors.push(e.stack));
 const $=s=>p.locator(s),faces=()=>$('.pk-hole-card').count(),phase=()=>$('#poker-app').getAttribute('data-phase');
 const shot=async name=>{await p.screenshot({path:path.join(root,'screenshots',name+'.png'),fullPage:true})};
 const confirm=async()=>{await $('#pk-confirm-player').click();assert.equal(await $('#pk-curtain').evaluate(e=>e.open),false)};
 const covered=async()=>{
  assert.equal(await $('#pk-curtain').evaluate(e=>e.open),true);assert.equal(await faces(),0);assert.equal(await $('.pk-back').count(),0);
  const r=await $('#pk-curtain').evaluate(e=>{const b=e.getBoundingClientRect(),s=getComputedStyle(e);return {x:b.x,y:b.y,w:b.width,h:b.height,vw:innerWidth,vh:innerHeight,bg:s.backgroundColor,opacity:s.opacity,position:s.position}});
  assert.equal(r.x,0);assert.equal(r.y,0);assert.equal(r.w,r.vw);assert.equal(r.h,r.vh);assert.equal(r.bg,'rgb(13, 21, 36)');assert.equal(r.opacity,'1');assert.equal(r.position,'fixed');
 };
 const fresh=async(count=2,spectator=false)=>{
  await p.reload();await $('#nav-poker').click();await $('#pk-count').selectOption(String(count));if(spectator)await $('#pk-spectator').check();await $('#pk-start').click();
 };
 try{
  await p.goto(`http://127.0.0.1:${server.address().port}`);await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);
  assert.equal(await p.locator('[role=tab]').count(),4);await $('#nav-game').focus();await p.keyboard.press('End');assert.equal(await $('#nav-poker').getAttribute('aria-selected'),'true');assert.ok((await p.title()).includes('德州扑克'));
  checks.push('第四个独立标签、标题及键盘 End 导航');
  await $('#pk-name-0').fill('');await $('#pk-start').click();assert.equal(await $('#pk-name-0').getAttribute('aria-invalid'),'true');assert.equal(await $('#pk-setup-error').isVisible(),true);assert.equal(await $('#pk-name-0').evaluate(e=>e===document.activeElement),true);
  await $('#pk-name-0').fill('<玩家一>');await $('#pk-stack').fill('99');await $('#pk-start').click();assert.equal(await $('#pk-stack').getAttribute('aria-invalid'),'true');await $('#pk-stack').fill('1000');await $('#pk-count').selectOption('2');
  await shot('setup-desktop');await $('#pk-start').click();await covered();await p.keyboard.press('Escape');await covered();assert.ok((await $('#pk-curtain-tip').innerText()).includes('请确认'));
  for(let i=0;i<5;i++){await p.keyboard.press('Tab');assert.equal(await p.evaluate(()=>document.activeElement.closest('#pk-curtain')!==null),true)}
  await p.mouse.wheel(0,1500);await covered();await shot('curtain-desktop');checks.push('表单错误与安全文本；交接弹层全屏不透明、焦点隔离，Escape/滚动不泄露');
  await confirm();assert.equal(await faces(),2);assert.equal(await $('[data-pk-holes="1"] .pk-hole-card').count(),0);assert.equal(await $('[data-pk-holes="1"] .pk-back').count(),2);assert.equal(await $('[data-pk-seat="0"] h3').innerText(),'<玩家一>');
  await $('#pk-raise').fill('21');await $('#pk-raise-button').click();assert.equal(await $('#pk-action-error').isVisible(),true);assert.equal(await faces(),2);assert.equal(await $('#pk-curtain').evaluate(e=>e.open),false);
  await p.evaluate(()=>{window.__previousCards=[...document.querySelectorAll('.pk-hole-card')];window.__afterAction=null;document.querySelector('#pk-call').addEventListener('click',()=>{window.__afterAction={count:document.querySelectorAll('.pk-hole-card').length,removed:window.__previousCards.every(n=>!n.isConnected),covered:document.querySelector('#pk-curtain').open}},{once:true})});
  await $('#pk-call').click();assert.deepEqual(await p.evaluate(()=>window.__afterAction),{count:0,removed:true,covered:true});await covered();await confirm();assert.equal(await faces(),2);assert.equal(await $('[data-pk-holes="1"] .pk-hole-card').count(),2);assert.equal(await $('[data-pk-holes="0"] .pk-hole-card').count(),0);
  await p.evaluate(()=>{delete window.__previousCards;delete window.__afterAction});checks.push('仅当前玩家两张底牌；非法加注保留输入；行动同一任务内原节点断开且新底牌未出现');
  await $('#nav-bank').click();assert.equal(await faces(),0);await $('#nav-poker').click();await covered();await confirm();
  await p.evaluate(()=>window.dispatchEvent(new Event('blur')));await covered();await p.evaluate(()=>window.dispatchEvent(new Event('focus')));await covered();await confirm();
  await $('#pk-hide').click();await covered();await $('#pk-leave').click();assert.equal(await $('#nav-game').getAttribute('aria-selected'),'true');assert.equal(await faces(),0);await $('#nav-poker').click();await covered();await confirm();
  checks.push('离开标签页、失焦、手动收牌和离桌均清空底牌；回来需重新确认');
  await p.evaluate(()=>window.scrollTo(0,0));await shot('active-desktop');await $('#pk-fold').click();assert.equal(await phase(),'complete');assert.equal(await faces(),0);assert.equal(await $('#pk-result').isVisible(),true);assert.ok((await $('#pk-result-help').innerText()).includes('不公开'));
  await $('#pk-next-hand').click();await covered();await confirm();assert.equal(await $('#pk-hand-number').innerText(),'第 2 手');assert.equal(await $('[data-pk-seat="1"] .pk-dealer').count(),1);checks.push('弃牌获胜不亮牌；下一手轮换庄家并重新交接');
  // Record first DOM appearance of each owner's faces, plus completion time.
  await fresh();await confirm();await $('#pk-allin').click();await covered();await confirm();
  await p.evaluate(()=>{window.__reveal={t0:0,owners:[],times:[]};window.__revealObserver=new MutationObserver(records=>{for(const r of records)for(const n of r.addedNodes){if(n.nodeType!==1||!n.matches('.pk-hole-card'))continue;const owner=Number(n.dataset.pkOwner);if(!window.__reveal.owners.includes(owner)){window.__reveal.owners.push(owner);window.__reveal.times.push(performance.now()-window.__reveal.t0)}}});window.__revealObserver.observe(document.querySelector('#pk-seats'),{childList:true,subtree:true})});
  await p.evaluate(()=>window.__reveal.t0=performance.now());await $('#pk-call').click();assert.equal(await phase(),'showdown');assert.equal(await $('.pk-community-card').count(),5);assert.equal(await faces(),0);assert.equal(await $('#pk-result').isVisible(),false);
  await p.waitForFunction(()=>document.querySelectorAll('.pk-hole-card').length===2);assert.equal(await $('#poker-app').getAttribute('data-phase'),'showdown');assert.equal(await $('[data-pk-holes="1"] .pk-hole-card').count(),0);assert.ok(await $('.pk-flip').count());
  const fps=await p.evaluate(()=>new Promise(resolve=>{const frames=[];let previous=performance.now();function f(t){frames.push(t-previous);previous=t;if(frames.length<30)requestAnimationFrame(f);else resolve(frames.slice(1))}requestAnimationFrame(f)}));
  await shot('showdown-first-seat');await p.waitForFunction(()=>document.querySelector('#poker-app').dataset.phase==='complete');
  const reveal=await p.evaluate(()=>{window.__revealObserver.disconnect();return {...window.__reveal,duration:performance.now()-window.__reveal.t0}});
  assert.deepEqual(reveal.owners,[0,1]);assert.ok(reveal.times[1]-reveal.times[0]>1100);assert.ok(reveal.duration>2500);assert.equal(await faces(),4);assert.equal(await $('#pk-result').isVisible(),true);await shot('showdown-complete');checks.push('逐家揭晓按 1→2 顺序创建牌面，首家翻牌时次家未渲染；完整动画后才结算');
  // Switch spectator mode on only after explicit in-table disclosure confirmation.
  await fresh();await confirm();await $('#pk-spectator').check();assert.equal(await $('#pk-spectator').isChecked(),false);assert.equal(await $('#pk-confirm-dialog').evaluate(e=>e.open),true);assert.equal(await faces(),2);await p.keyboard.press('Escape');assert.equal(await $('#pk-spectator').isChecked(),false);assert.equal(await faces(),2);
  await $('#pk-spectator').check();await $('#pk-confirm-accept').click();assert.equal(await faces(),4);assert.equal(await $('.pk-observer-badge:visible').count(),2);assert.equal(await $('#pk-curtain').evaluate(e=>e.open),false);
  await p.evaluate(()=>{window.__spectatorNodes=[...document.querySelectorAll('.pk-hole-card')];window.__removedFaces=0;window.__spectatorObserver=new MutationObserver(rs=>{for(const r of rs)for(const n of r.removedNodes){if(n.nodeType===1&&(n.matches('.pk-hole-card')||n.querySelector('.pk-hole-card')))window.__removedFaces++}});window.__spectatorObserver.observe(document.querySelector('#pk-seats'),{childList:true,subtree:true})});
  await $('#pk-call').click();await $('#pk-check').click();assert.equal(await $('#pk-street').innerText(),'翻牌');assert.equal(await $('#pk-curtain').evaluate(e=>e.open),false);assert.equal(await p.evaluate(()=>window.__spectatorNodes.every(n=>n.isConnected)&&window.__removedFaces===0),true);
  await p.evaluate(()=>window.dispatchEvent(new Event('blur')));assert.equal(await faces(),4);await p.evaluate(()=>window.dispatchEvent(new Event('focus')));await $('#nav-agent').click();assert.equal(await faces(),4);await $('#nav-poker').click();assert.equal(await p.evaluate(()=>window.__spectatorNodes.every(n=>n.isConnected)),true);
  await p.evaluate(()=>window.scrollTo(0,0));await shot('spectator-desktop');
  await $('#pk-allin').click();await $('#pk-call').click();assert.equal(await phase(),'showdown');assert.equal(await faces(),4);await p.waitForFunction(()=>document.querySelector('#poker-app').dataset.phase==='complete');assert.equal(await p.evaluate(()=>window.__spectatorNodes.every(n=>n.isConnected)&&window.__removedFaces===0),true);await p.evaluate(()=>{window.__spectatorObserver.disconnect();delete window.__spectatorNodes});
  checks.push('旁观开启确认、取消、所有座位标识；跨行动/失焦/标签/摊牌全程保留同一批牌面 DOM');
  await fresh(2,true);assert.equal(await faces(),4);await $('#pk-spectator').uncheck();await covered();assert.equal(await $('.pk-observer-badge:visible').count(),0);await confirm();assert.equal(await faces(),2);assert.equal(await $('#pk-exposed-note').isVisible(),true);
  checks.push('退出旁观立即清空全部牌面并遮罩，身份确认后恢复私密模式；保留本局曾公开提示');
  // Pausing a ceremony cannot silently finish it in another app tab.
  await fresh();await confirm();await $('#pk-allin').click();await confirm();await $('#pk-call').click();await p.waitForFunction(()=>document.querySelectorAll('.pk-hole-card').length===2);await $('#nav-game').click();assert.equal(await faces(),0);await p.waitForTimeout(2850);assert.equal(await phase(),'showdown');await $('#nav-poker').click();await p.waitForFunction(()=>document.querySelector('#poker-app').dataset.phase==='complete');assert.equal(await faces(),4);checks.push('摊牌期间离开即暂停、普通模式清牌，回来后继续逐家揭晓而非跳过');
  // Six seats on narrow screens and reduced motion retain every reveal step.
  await p.setViewportSize({width:390,height:844});await p.emulateMedia({reducedMotion:'reduce'});await fresh(6);
  await covered();await confirm();assert.equal(await $('.pk-seat').count(),6);assert.equal(await faces(),2);await p.evaluate(()=>window.scrollTo(0,0));await shot('active-mobile');
  for(const width of [320,390,600,900,1280]){await p.setViewportSize({width,height:844});assert.equal(await p.evaluate(()=>document.documentElement.scrollWidth>innerWidth),false,'live horizontal overflow '+width);await $('#pk-hide').click();await covered();await confirm()}
  await p.setViewportSize({width:320,height:844});await $('#pk-spectator').check();await $('#pk-confirm-accept').click();assert.equal(await faces(),12);assert.equal(await $('.pk-observer-badge:visible').count(),6);assert.equal(await p.evaluate(()=>document.documentElement.scrollWidth>innerWidth),false);await p.evaluate(()=>window.scrollTo(0,0));await shot('spectator-mobile-320');
  await p.evaluate(()=>{window.__reducedSequence=[];window.__reducedObserver=new MutationObserver(rs=>{for(const r of rs){if(r.target.classList.contains('pk-revealing')){const i=Number(r.target.dataset.pkSeat);if(window.__reducedSequence.at(-1)!==i)window.__reducedSequence.push(i)}}});window.__reducedObserver.observe(document.querySelector('#pk-seats'),{attributes:true,attributeFilter:['class'],subtree:true})});
  for(let i=0;i<6;i++){if(await $('#pk-allin').isEnabled())await $('#pk-allin').click();else await $('#pk-call').click()}
  assert.equal(await phase(),'showdown');assert.equal(await faces(),12);await p.waitForFunction(()=>document.querySelector('#poker-app').dataset.phase==='complete');const reducedSeq=await p.evaluate(()=>{window.__reducedObserver.disconnect();return window.__reducedSequence});assert.deepEqual(reducedSeq,[0,1,2,3,4,5]);assert.equal(await p.evaluate(()=>document.documentElement.scrollWidth>innerWidth),false);await shot('showdown-mobile-320');checks.push('320/390/600/900/1280px 6 人可访问且无横向溢出；减少动画仍逐家处理 6 席');
  await $('#pk-new-table').click();assert.equal(await $('#pk-confirm-dialog').evaluate(e=>e.open),true);await $('#pk-confirm-cancel').click();assert.equal(await phase(),'complete');await $('#pk-new-table').click();await $('#pk-confirm-accept').click();assert.equal(await phase(),'setup');assert.equal(await faces(),0);assert.equal(await $('#pk-setup').isVisible(),true);
  for(const width of [320,390,600,900,1280]){await p.setViewportSize({width,height:844});assert.equal(await p.evaluate(()=>document.documentElement.scrollWidth>innerWidth),false,'setup overflow '+width)}
  checks.push('重新开桌取消/确认、清除牌局且返回设置；设置页各尺寸无横向溢出');
  const storage=await p.evaluate(()=>({local:{...localStorage},session:{...sessionStorage}}));assert.ok(!Object.keys({...storage.local,...storage.session}).some(k=>/poker|holdem/i.test(k)));assert.deepEqual(errors,[]);
  checks.push('底牌未写入 localStorage/sessionStorage，完整流程无 JavaScript 错误');
  const sorted=fps.slice().sort((a,b)=>a-b),report={checks,pageErrors:errors,reveal,animationFrameSample:{medianMs:sorted[Math.floor(sorted.length/2)],p95Ms:sorted[Math.floor(sorted.length*.95)],note:'Headless Chromium sample only; not a universal hardware frame-rate guarantee.'},browser:await browser.version()};fs.writeFileSync(path.join(root,'poker-browser-verification.json'),JSON.stringify(report,null,2));console.log(JSON.stringify(report,null,2));
 }finally{await browser.close();await new Promise(r=>server.close(r))}
})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 44. `/workspace/output/poker-edition/tests/accessibility.cjs`

~~~~~~~~~~
const {chromium}=require('playwright'),fs=require('node:fs'),path=require('node:path'),http=require('node:http');
(async()=>{
 const html=fs.readFileSync(path.join(__dirname,'../src/maogou-xindongju-poker-v6.html'),'utf8');
 const server=http.createServer((req,res)=>{res.writeHead(200,{'Content-Type':'text/html; charset=utf-8'});res.end(html)});await new Promise(r=>server.listen(0,'127.0.0.1',r));
 const b=await chromium.launch({headless:true,executablePath:process.env.CHROMIUM_PATH||'/usr/bin/chromium',args:['--no-sandbox']});
 try{
  const p=await b.newPage({viewport:{width:1280,height:1000},reducedMotion:'reduce'});await p.goto(`http://127.0.0.1:${server.address().port}`);await p.waitForFunction(()=>window.gamePet3D?.diagnostics.ready);
  await p.addScriptTag({path:process.env.AXE_PATH||'/tmp/watercolor-a11y/node_modules/axe-core/axe.min.js'});const results=[];
  async function audit(surface){const r=await p.evaluate(()=>axe.run(document,{runOnly:{type:'tag',values:['wcag2a','wcag2aa','wcag21aa','wcag22aa']}}));results.push({surface,violations:r.violations.map(v=>({id:v.id,impact:v.impact,nodes:v.nodes.map(n=>({target:n.target,summary:n.failureSummary}))}))})}
  for(const tab of ['game','agent','bank']){await p.locator('#nav-'+tab).click();await audit(tab)}
  await p.locator('.list-item-btn.delete').first().click();await audit('delete-dialog');await p.locator('#delete-cancel').click();
  await p.locator('#nav-poker').click();await audit('poker-setup');await p.locator('#pk-count').selectOption('2');await p.locator('#pk-start').click();await audit('poker-curtain');
  await p.locator('#pk-confirm-player').click();await audit('poker-private-turn');await p.locator('#pk-spectator').click();await audit('poker-public-disclosure');await p.locator('#pk-confirm-accept').click();await audit('poker-spectator');
  await p.locator('#pk-allin').click();await p.locator('#pk-call').click();await audit('poker-showdown');await p.waitForFunction(()=>document.querySelector('#poker-app').dataset.phase==='complete');await audit('poker-result');
  await p.setViewportSize({width:320,height:844});await audit('poker-mobile-320');
  fs.writeFileSync(path.join(__dirname,'../accessibility.json'),JSON.stringify(results,null,2));console.log(JSON.stringify(results,null,2));if(results.some(x=>x.violations.length))process.exitCode=1;
 }finally{await b.close();await new Promise(r=>server.close(r))}
})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 45. `/workspace/output/poker-edition/README.md`

~~~~~~~~~~
# 猫狗心动局 · 德州扑克 v6

打开 `src/maogou-xindongju-poker-v6.html` 即可使用，不依赖服务器、外部字体、图片 CDN 或安装过程。德州扑克是与原有“游戏桌”“指令助手”“我的题库”平行的第四个标签。

## 使用

填写 2—6 个座位的姓名、初始虚拟筹码和盲注，开始发牌。普通模式需要把设备交给当前行动玩家，再按座位号确认身份。每次行动、离桌或窗口失焦都会收起底牌。其他人的底牌没有实际牌面 DOM。

摊牌时按座位顺序逐家揭晓。最后一位展示完成后才分配筹码。其他人全部弃牌的牌局直接结束，无需亮牌。

右上方“旁观模式”开关始终位于滚动工具栏。开启后所有手牌持续公开，每个座位标记“观战模式”。牌局中开启前需要确认公开；关闭后恢复私密交接，并保留本手曾公开的提示。

牌局只保存在运行时内存，刷新或关闭页面后清空。既有题库仍按原版规则本地保存。身份按钮是同屏自我确认；单文件 DOM 隔离不能防止使用 JavaScript 调试器读取运行时内存，不等同于多人联网私密对局。

## 维护与验证

- `base/`：保留的 v5 原版，未覆盖。
- `src/poker-engine.js`：下注、牌型、主/边池与筹码规则。
- `src/poker-ui.js`：私密交接、旁观、逐家动画。
- `src/poker.css`、`poker-panel.html`、`poker-overlays.html`：独立界面。
- `python build.py`：将原版与上述源文件合成为独立 HTML。
- `node tests/poker-engine.cjs`：规则和随机筹码守恒。
- `node tests/poker-browser.cjs`：真实 DOM 隐私、动画顺序、旁观节点持续性、触屏和响应式。
- `node tests/verify.cjs`：原有三个标签与动画角色的回归验证。
- `node tests/accessibility.cjs`：四个标签及各弹窗/牌局状态的 axe 检查。
- `node tests/actions.cjs`：真实浏览器中的原生操作绑定检查。

浏览器测试需 Node.js、Playwright 和 Chromium。可用 `CHROMIUM_PATH` 设置通用回归和 axe 测试的浏览器位置，用 `AXE_PATH` 指向 axe-core 脚本。此次实际验证使用 Chromium 154；实现使用现代 Chrome、Edge、Firefox、Safari 支持的原生 dialog、CSS 动画和标准 DOM API。动画仅使用 transform/opacity；测试帧率样本不代表所有硬件上的帧率保证。

设计及行为约定见 `DESIGN.md`、`UX-CONTRACT.md`。自动测试报告和截图保留在本目录。静态审计原始结果及其局限见 `AUDIT-NOTES.md`。
~~~~~~~~~~

## 46. `/workspace/output/linked-edition/src/link-core.js`

~~~~~~~~~~
/* Shared, DOM-free linking rules and queue. Public poker summaries only. */
(function(root,factory){
 if(typeof module==='object'&&module.exports)module.exports=factory();
 else root.XindongLinkRules=factory();
})(typeof globalThis!=='undefined'?globalThis:this,function(){
 'use strict';
 const DEFAULTS=Object.freeze({enabled:true,perHand:true,lossEnabled:true,threshold2:20,threshold3:50,specialEnabled:true,specialMinCategory:5,specialBonus:1,maxLevel:3});
 const LEVELS=['','轻松','心动','默契'];
 const clone=value=>JSON.parse(JSON.stringify(value));
 function validateRules(input){
  const r={};
  for(const k of ['enabled','perHand','lossEnabled','specialEnabled']){if(typeof input[k]!=='boolean')throw Object.assign(new Error('请选择有效的开关状态。'),{field:k});r[k]=input[k]}
  const limits={threshold2:[1,99],threshold3:[2,100],specialMinCategory:[4,8],specialBonus:[1,2],maxLevel:[1,3]};
  for(const [k,[min,max]] of Object.entries(limits)){const n=Number(input[k]);if(!Number.isInteger(n)||n<min||n>max)throw Object.assign(new Error(k==='threshold2'||k==='threshold3'?'亏损阈值需填写 1—100 之间的整数，且二级小于三级。':'请选择有效的等级或牌型。'),{field:k});r[k]=n}
  if(r.threshold2>=r.threshold3)throw Object.assign(new Error('三级亏损阈值必须大于二级阈值。'),{field:'threshold3'});
  return r;
 }
 function selectQuestion(questions,{type,level,excludeId=null,random=Math.random}){
  let pool=questions.filter(q=>q.type===type&&Number.isInteger(q.linkDifficulty)&&q.linkDifficulty>=1&&q.linkDifficulty<=level&&q.id!==excludeId);
  if(!pool.length)return null;
  const best=Math.max(...pool.map(q=>q.linkDifficulty));pool=pool.filter(q=>q.linkDifficulty===best);
  const minUsed=Math.min(...pool.map(q=>q.usedCount||0));pool=pool.filter(q=>(q.usedCount||0)===minUsed);
  const q=pool[Math.min(pool.length-1,Math.floor(random()*pool.length))];
  return {id:q.id,text:q.text,type:q.type,category:q.category,tags:[...(q.tags||[])],linkDifficulty:q.linkDifficulty};
 }
 function planChallenges(settlement,rules){
  if(!rules.enabled)return [];
  const players=settlement.players.filter(p=>p.inHand),losers=players.filter(p=>p.netDelta<0),winners=players.filter(p=>p.netDelta>0);
  if(!losers.length||!winners.length)return [];
  const worst=Math.min(...losers.map(p=>p.netDelta)),best=Math.max(...winners.map(p=>p.netDelta));
  const count=settlement.players.length;
  const chooser=winners.filter(p=>p.netDelta===best).sort((a,b)=>(a.seat-settlement.dealer-1+count)%count-(b.seat-settlement.dealer-1+count)%count)[0];
  const special=rules.specialEnabled&&settlement.kind==='showdown'&&winners.some(p=>!p.folded&&Number.isInteger(p.handCategory)&&p.handCategory>=rules.specialMinCategory);
  return losers.filter(p=>p.netDelta===worst).sort((a,b)=>a.seat-b.seat).flatMap(p=>{
   const reasons=[];let level=1;
   if(rules.perHand)reasons.push('本手净亏损最多');
   if(rules.lossEnabled){if(-p.netDelta*100>=p.startChips*rules.threshold3){level=3;reasons.push('净亏损达到 '+rules.threshold3+'%')}else if(-p.netDelta*100>=p.startChips*rules.threshold2){level=2;reasons.push('净亏损达到 '+rules.threshold2+'%')}}
   if(special){level+=rules.specialBonus;reasons.push('赢家公开达成'+['高牌','一对','两对','三条','顺子','同花','葫芦','四条','同花顺'][rules.specialMinCategory]+'及以上')}
   if(!reasons.length)return [];
   return [{participantId:p.id,chooserId:chooser.id,level:Math.min(level,rules.maxLevel),reasons,netDelta:p.netDelta,startChips:p.startChips,endChips:p.endChips}];
  });
 }
 class LinkService{
  constructor({pickQuestion,loadRules=()=>null,saveRules=()=>{},idFactory=()=>globalThis.crypto.randomUUID()}={}){
   this.pickQuestion=pickQuestion;this.saveRules=saveRules;this.idFactory=idFactory;this.listeners=new Set();this.seen=new Set();this.handRules=null;this.handKey=null;
   let rules={...DEFAULTS},storageNote='',version=1;
   try{const saved=loadRules();if(saved){if(saved.schemaVersion!==1)throw Error('旧设置');rules=validateRules(saved.rules);version=Number.isSafeInteger(saved.version)&&saved.version>0?saved.version:1}}catch{storageNote='联动设置未能读取，本次使用默认规则。'}
   this.value={revision:0,tableId:null,live:{phase:'setup',handNo:0,players:[]},lastSettlement:null,rules,rulesVersion:version,storageNote,tasks:[],selectedId:null};
  }
  snapshot(){return clone(this.value)}
  subscribe(fn){this.listeners.add(fn);fn(this.snapshot());return ()=>this.listeners.delete(fn)}
  emit(){this.value.revision++;const snapshot=this.snapshot();for(const listener of this.listeners)listener(snapshot)}
  canWork(){return this.value.live.phase==='complete'}
  canConfigure(){return ['setup','complete'].includes(this.value.live.phase)}
  startTable(){this.seen.clear();this.handRules=null;this.handKey=null;this.value={...this.value,tableId:this.idFactory(),live:{phase:'setup',handNo:0,players:[]},lastSettlement:null,tasks:[],selectedId:null};this.emit();return this.value.tableId}
  reset(){this.seen.clear();this.handRules=null;this.handKey=null;Object.assign(this.value,{tableId:null,live:{phase:'setup',handNo:0,players:[]},lastSettlement:null,tasks:[],selectedId:null});this.emit()}
  sync(input){
   if(!this.value.tableId||input.tableId!==this.value.tableId)return false;
   if(!['playing','showdown','complete'].includes(input.phase)||!Number.isInteger(input.handNo)||input.handNo<1)return false;
   if(input.handNo<this.value.live.handNo)return false;
   const key=input.tableId+':'+input.handNo;
   if(key!==this.handKey){this.handKey=key;this.handRules={rules:clone(this.value.rules),version:this.value.rulesVersion}}
   // Explicit projection prevents accidentally copying private engine fields.
   const live={phase:input.phase,handNo:input.handNo,actor:input.actor??null,players:input.players.map(p=>({id:p.id,seat:p.seat,name:p.name,endChips:p.endChips,inHand:!!p.inHand,folded:!!p.folded}))};
   let changed=JSON.stringify(live)!==JSON.stringify(this.value.live);this.value.live=live;
   if(input.phase==='complete'&&!this.seen.has(key)){
    const players=input.players.map(p=>({id:p.id,seat:p.seat,name:p.name,startChips:p.startChips,endChips:p.endChips,netDelta:p.endChips-p.startChips,inHand:!!p.inHand,folded:!!p.folded,handCategory:input.kind==='showdown'&&!p.folded&&Number.isInteger(p.handCategory)?p.handCategory:null}));
    if(players.some(p=>!Number.isSafeInteger(p.startChips)||p.startChips<0||!Number.isSafeInteger(p.endChips)||p.endChips<0)||players.reduce((sum,p)=>sum+p.netDelta,0)!==0)throw Error('联动结算的筹码变化不一致。');
    const settlement={tableId:input.tableId,handNo:input.handNo,kind:input.kind,dealer:input.dealer,players,rulesVersion:this.handRules.version};
    const tasks=planChallenges(settlement,this.handRules.rules).map(t=>({...t,id:key+':'+t.participantId,tableId:input.tableId,handNo:input.handNo,rulesVersion:this.handRules.version,roster:players.map(({id,seat,name})=>({id,seat,name})),status:'pending',type:null,partnerId:null,question:null,error:'',createdAt:Date.now(),resolvedAt:null}));
    this.seen.add(key);this.value.lastSettlement=settlement;this.value.tasks.push(...tasks);if(!this.value.selectedId&&tasks.length)this.value.selectedId=tasks[0].id;changed=true;
   }
   if(changed)this.emit();return changed;
  }
  task(id){return this.value.tasks.find(t=>t.id===id)||null}
  requireTask(id){if(!this.canWork())throw Error('本手结束后再处理挑战。');const t=this.task(id);if(!t||t.tableId!==this.value.tableId||!['pending','ready'].includes(t.status))throw Error('这项挑战已经处理，或不属于当前牌桌。');return t}
  select(id){if(!this.task(id))return false;if(this.value.selectedId===id)return true;this.value.selectedId=id;this.emit();return true}
  fillQuestion(t,replace=false){
   if(!t.type||!t.partnerId)return;
   const q=this.pickQuestion({type:t.type,level:t.level,excludeId:replace?t.question?.id:null});
   if(!q){t.error=replace?'没有其他符合当前类型与难度的题目，可保留本题或跳过。':'当前类型没有适合的已分级题目，可改选类型、给题库分级或跳过。';return}
   t.question=clone(q);t.status='ready';t.error='';
  }
  chooseType(id,type){const t=this.requireTask(id);if(!['truth','dare'].includes(type))throw Error('请选择真心话或大冒险。');if(t.type===type)return false;t.type=type;t.question=null;t.status='pending';t.error='';this.fillQuestion(t);this.emit();return true}
  choosePartner(id,partnerId){const t=this.requireTask(id);if(!t.roster.some(p=>p.id===partnerId&&p.id!==t.participantId))throw Error('请选择本桌另一位玩家。');if(t.partnerId===partnerId)return false;t.partnerId=partnerId;t.error='';if(!t.question)this.fillQuestion(t);this.emit();return true}
  redraw(id){const t=this.requireTask(id);if(!t.type||!t.partnerId)throw Error('请先选择类型和搭档。');this.fillQuestion(t,!!t.question);this.emit();return !!t.question}
  resolve(id,skipped=false){const t=this.requireTask(id);if(!skipped&&(!t.question||!t.partnerId))throw Error('请先抽取题目，或选择跳过。');t.status=skipped?'skipped':'completed';t.resolvedAt=Date.now();t.error='';const done=this.value.tasks.filter(x=>['completed','skipped'].includes(x.status));if(done.length>100){const ids=new Set(done.slice(0,-100).map(x=>x.id));this.value.tasks=this.value.tasks.filter(x=>!ids.has(x.id))}this.emit();return true}
  updateRules(input){
   if(!this.canConfigure())throw Error('本手结束后再调整联动规则。');
   const rules=validateRules(input);this.value.rules=rules;this.value.rulesVersion++;this.value.storageNote='';
   try{this.saveRules({schemaVersion:1,version:this.value.rulesVersion,rules})}catch{this.value.storageNote='当前无法保存联动设置，修改仅本次打开有效。'}
   this.emit();return true;
  }
 }
 return {DEFAULTS,LEVELS,validateRules,selectQuestion,planChallenges,LinkService};
});
~~~~~~~~~~

## 47. `/tmp/patch_link_core_game.py`

~~~~~~~~~~
from pathlib import Path
p=Path('/workspace/output/linked-edition/src/core-game.html');s=p.read_text()
levels='''  // Reviewed per-question grades; custom legacy questions stay ungraded.
  const LINK_DEFAULT_LEVELS = {
    truth: [1,2,2,2,1,1,2,1,1,2,1,3,2,2,1,2,3,1,1,1,2,2,2,2,3,2,3,3,2,3,2,1,2,1,2,1,2,1,2,1,3,1,2,1,2,1,2,3,2,2,1,2,2,1,1,1,2,2,1,1,2,1,1,1,3,3],
    dare: [3,1,2,3,3,2,2,3,3,2,3,3,3,1,1,1,2,2,2,3,3,3,2,1,1,2,2,1,2,2,2,3,3,2]
  };
'''
s=s.replace('  const DataManager = {',levels+'\n  const DataManager = {',1)
s=s.replace("          usedCount: 0, lastUsed: null,", "          linkDifficulty: LINK_DEFAULT_LEVELS.truth[i], usedCount: 0, lastUsed: null,",1)
pos=s.index("DEFAULT_QUESTIONS.dare.forEach")
a=s[:pos];b=s[pos:].replace("          usedCount: 0, lastUsed: null,", "          linkDifficulty: LINK_DEFAULT_LEVELS.dare[i], usedCount: 0, lastUsed: null,",1);s=a+b
s=s.replace('    init() { this.data = DataManager.load(); },','''    init() {
      this.data = DataManager.load(); let changed=false;
      for(const q of this.getAll()) {
        if(Object.prototype.hasOwnProperty.call(q,'linkDifficulty')) {
          if(q.linkDifficulty!==null&&![1,2,3].includes(q.linkDifficulty)){q.linkDifficulty=null;changed=true}
          continue;
        }
        const index=DEFAULT_QUESTIONS[q.type].indexOf(q.text);
        q.linkDifficulty=index>=0?LINK_DEFAULT_LEVELS[q.type][index]:null;changed=true;
      }
      if(changed)DataManager.save(this.data);
    },
    pickLinked(options) {
      const q=LinkRules.selectQuestion(this.getAll(),options);
      if(q)this.markAsUsed(q.id);
      return q;
    },
    setLinkDifficulty(id,value) {
      const q=this.getById(id);if(!q||!(value===null||[1,2,3].includes(value)))return false;
      q.linkDifficulty=value;DataManager.save(this.data);return true;
    },''',1)
s=s.replace('    add(type, text, tags = []) {','    add(type, text, tags = [], linkDifficulty = null) {',1)
s=s.replace('        tags, usedCount: 0, lastUsed: null,','        tags, linkDifficulty: [1,2,3].includes(linkDifficulty)?linkDifficulty:null, usedCount: 0, lastUsed: null,',1)
s=s.replace('QuestionService.add(type, text, tags); this.$',"QuestionService.add(type, text, tags, Number(this.$('#add-link-difficulty').value)||null); this.$",1)
s=s.replace('    initBank() {', '''    initBank() {
      this.$('#question-list').addEventListener('change',e=>{
        const select=e.target.closest('[data-link-grade]');if(!select)return;
        if(QuestionService.setLinkDifficulty(select.dataset.linkGrade,Number(select.value)||null))this.showToast(window.GameStorageHealthy===false?'难度已更新，仅本次打开有效':'联动难度已更新','success');
      });''',1)
s=s.replace("        fragment.appendChild(item);",'''        const label=document.createElement('label');label.className='link-grade-field';label.textContent='联动难度';
        const grade=document.createElement('select');grade.dataset.linkGrade=q.id;grade.setAttribute('aria-label','题目 '+q.id+' 的联动难度');
        for(const [value,text] of [['','未分级'],['1','轻松'],['2','心动'],['3','默契']]){const option=document.createElement('option');option.value=value;option.textContent=text;grade.append(option)}
        grade.value=q.linkDifficulty?String(q.linkDifficulty):'';label.append(grade);item.querySelector('.list-item-actions').prepend(label);
        fragment.appendChild(item);''',1)
s=s.replace('</select><label class="sr-only" for="add-text">','</select><label class="link-add-grade" for="add-link-difficulty">联动难度<select id="add-link-difficulty"><option value="">未分级</option><option value="1">轻松</option><option value="2">心动</option><option value="3">默契</option></select></label><label class="sr-only" for="add-text">',1)
s=s.replace('轮流心动</button></div>','轮流心动</button><button type="button" class="mode-btn" id="mode-linked-button" data-mode="linked" aria-pressed="false" aria-controls="mode-linked">德扑联动 <span class="link-count" data-link-count hidden></span></button></div>',1)
s=s.replace('          <p class="stage-footer">','          <div class="game-mode" id="mode-linked"><section id="link-game" class="link-panel" aria-labelledby="link-game-title"></section></div>\n          <p class="stage-footer">',1)
s=s.replace('游戏桌</button>','游戏桌 <span class="link-count" data-link-count hidden></span></button>',1)
s=s.replace('日落微醺版 v5.0','联动版 v7.0')
s=s.replace("+' · 猫狗心动局 · 日落微醺版';","+' · 猫狗心动局 · 联动版 v7';",1)
p.write_text(s)
~~~~~~~~~~

## 48. `/workspace/output/linked-edition/src/link-settings.html`

~~~~~~~~~~
<div id="link-announcement" class="sr-only" role="status" aria-live="polite"></div>
<dialog id="link-settings-dialog" class="game-confirm link-settings-dialog" aria-labelledby="link-settings-title" aria-describedby="link-settings-help">
 <h2 id="link-settings-title">德扑联动设置</h2><p id="link-settings-help">保存后从下一手生效，已排队的挑战保留原规则。规则保存在本机，牌局与挑战不保存。</p>
 <form id="link-settings-form" novalidate>
  <div class="link-rule-switches">
   <label><input id="lr-enabled" type="checkbox" name="enabled"> 开启德扑联动</label>
   <label><input id="lr-perHand" type="checkbox" name="perHand"> 每手为净输最多者生成挑战</label>
   <label><input id="lr-lossEnabled" type="checkbox" name="lossEnabled"> 按净亏损比例升级</label>
  </div>
  <div class="link-rule-grid">
   <label for="lr-threshold2">二级亏损阈值（%）<input id="lr-threshold2" name="threshold2" type="number" min="1" max="99" step="1" inputmode="numeric" aria-describedby="link-settings-error"></label>
   <label for="lr-threshold3">三级亏损阈值（%）<input id="lr-threshold3" name="threshold3" type="number" min="2" max="100" step="1" inputmode="numeric" aria-describedby="link-settings-error"></label>
  </div>
  <p class="link-hint">以该玩家本手开手筹码为基数，退款不算亏损。</p>
  <label class="link-rule-check"><input id="lr-specialEnabled" type="checkbox" name="specialEnabled"> 赢家公开达成特殊牌型时升级</label>
  <div class="link-rule-grid">
   <label for="lr-specialMinCategory">特殊牌型门槛<select id="lr-specialMinCategory" name="specialMinCategory"><option value="4">顺子及以上</option><option value="5">同花及以上</option><option value="6">葫芦及以上</option><option value="7">四条及以上</option><option value="8">同花顺及以上</option></select></label>
   <label for="lr-specialBonus">特殊牌型提升<select id="lr-specialBonus" name="specialBonus"><option value="1">提升一级</option><option value="2">提升两级</option></select></label>
   <label for="lr-maxLevel">挑战最高等级<select id="lr-maxLevel" name="maxLevel"><option value="1">一级 · 轻松</option><option value="2">二级 · 心动</option><option value="3">三级 · 默契</option></select></label>
  </div>
  <p class="link-hint">多条规则合并为一张挑战。接受者自行选择搭档，随时可以换题或跳过。</p>
  <p id="link-settings-error" class="field-error" role="alert" hidden></p><p id="link-storage-note" class="link-storage-note" role="status" hidden></p>
  <div class="link-rule-actions"><button type="button" id="link-defaults" class="pk-quiet">恢复默认值</button><div><button type="button" id="link-settings-cancel" class="action-btn confirm-cancel">取消</button><button type="submit" id="link-settings-save" class="action-btn pk-primary">保存规则</button></div></div>
 </form>
</dialog>
~~~~~~~~~~

## 49. `/workspace/output/linked-edition/src/link-ui.js`

~~~~~~~~~~
/* One shared store; two persistent view projections. No poker hand access. */
const LINK_STORAGE_KEY='xindong_link_rules_v1';
const linked=new LinkRules.LinkService({
 pickQuestion:options=>QuestionService.pickLinked(options),
 loadRules:()=>{const raw=localStorage.getItem(LINK_STORAGE_KEY);return raw?JSON.parse(raw):null},
 saveRules:value=>localStorage.setItem(LINK_STORAGE_KEY,JSON.stringify(value))
});
const linkUI=(()=>{
 const levels=LinkRules.LEVELS,dialog=document.querySelector('#link-settings-dialog'),form=document.querySelector('#link-settings-form');
 const roots=[...document.querySelectorAll('#link-game,#link-poker')];
 let current=linked.snapshot(),settingsFocus=null,knownPending=0,knownTable=null;
 const text=(el,value)=>{if(el.textContent!==String(value))el.textContent=String(value)};
 const prop=(el,key,value)=>{if(el[key]!==value)el[key]=value};
 const make=(tag,label)=>{const el=document.createElement(tag);if(label!==undefined)el.textContent=label;return el};
 const bind=(el,handler)=>GameActions.register(el,handler);
 function notifyError(e){window.GameUI.showToast(e.message,'error')}
 function command(fn){try{fn()}catch(e){notifyError(e)}}
 function option(value,label){const el=make('option',label);el.value=value;return el}
 const pending=t=>['pending','ready'].includes(t.status);
 roots.forEach(root=>{
  const id=root.id;
  root.innerHTML=`<div class="link-panel-heading"><div><p class="link-kicker">牌局之外，再靠近一点</p><h3 id="${id}-title">心动待办 <span class="link-count" data-role="count"></span></h3></div><button type="button" class="pk-quiet" data-role="settings">联动设置</button></div>
   <p class="link-phase" data-role="phase"></p><p class="link-summary" data-role="summary"></p>
   <div class="link-empty" data-role="empty"><span aria-hidden="true">♡</span><p data-role="empty-text">打完一手，心动挑战会自动排队。你可以继续打牌，之后再来慢慢完成。</p></div>
   <div data-role="work" hidden>
    <label class="link-task-picker" for="${id}-task">选择挑战<select id="${id}-task" data-role="task"></select></label>
    <article class="link-task" data-role="detail" aria-labelledby="${id}-target">
     <div class="link-task-heading"><h4 id="${id}-target" data-role="target"></h4><span class="link-level" data-role="level"></span></div>
     <p class="link-reasons" data-role="reasons"></p><p class="link-task-money" data-role="money"></p>
     <p class="link-chooser" data-role="chooser"></p>
     <div class="link-type-buttons" role="group" aria-label="赢家选择挑战类型"><button type="button" class="link-truth" data-role="truth" aria-pressed="false">真心话</button><button type="button" class="link-dare" data-role="dare" aria-pressed="false">大冒险</button></div>
     <label class="link-partner-field" for="${id}-partner"><span data-role="partner-label">接受者选择搭档</span><select id="${id}-partner" data-role="partner"><option value="">请选择另一位玩家</option></select></label>
     <p class="link-pair" data-role="pair"></p>
     <div class="link-question" data-role="question" hidden><p class="link-question-meta" data-role="question-meta"></p><p class="link-question-text" data-role="question-text"></p></div>
     <p class="link-question-placeholder" data-role="placeholder">选好类型和搭档后，就会抽出这一张挑战。</p>
     <p class="field-error" data-role="error" role="status" hidden></p>
     <div class="link-task-actions"><button type="button" class="pk-secondary" data-role="redraw">抽取挑战</button><button type="button" class="pk-primary" data-role="complete">完成了</button><button type="button" class="pk-quiet" data-role="skip">跳过这一项</button></div>
     <p class="link-resolved" data-role="resolved" tabindex="-1" hidden></p><button type="button" class="pk-secondary link-next" data-role="next" hidden>处理下一项待办</button>
    </article>
   </div>
   <details class="link-history"><summary data-role="history-label">联动记录</summary><ol data-role="history"></ol></details>`;
  const ui=Object.fromEntries([...root.querySelectorAll('[data-role]')].map(el=>[el.dataset.role,el]));root.linkElements=ui;root.linkKeys={};
  bind(ui.settings,()=>openSettings());ui.task.addEventListener('change',()=>linked.select(ui.task.value));
  ui.partner.addEventListener('change',()=>command(()=>linked.choosePartner(current.selectedId,ui.partner.value)));
  for(const type of ['truth','dare'])bind(ui[type],()=>command(()=>linked.chooseType(current.selectedId,type)));
  bind(ui.redraw,()=>command(()=>linked.redraw(current.selectedId)));
  for(const [role,skipped] of [['complete',false],['skip',true]])bind(ui[role],()=>command(()=>{linked.resolve(current.selectedId,skipped);const resolved=ui.resolved;resolved.focus({preventScroll:true});window.GameUI.showToast(skipped?'这一项已跳过':'挑战完成，留住这一点心动。','success')}));
  bind(ui.next,()=>{const next=current.tasks.find(pending);if(next){linked.select(next.id);ui.task.focus({preventScroll:true})}});
 });
 function showRules(rules){
  for(const [key,value] of Object.entries(rules)){const input=form.elements.namedItem(key);if(!input)continue;if(input.type==='checkbox')input.checked=value;else input.value=String(value)}
  form.querySelectorAll('[aria-invalid]').forEach(el=>el.removeAttribute('aria-invalid'));form.querySelector('#link-settings-error').hidden=true;
 }
 function openSettings(){
  if(!linked.canConfigure()){window.GameUI.showToast('本手结束后再调整联动规则。');return}
  settingsFocus=document.activeElement;showRules(current.rules);dialog.showModal();document.querySelector('#link-settings-cancel').focus({preventScroll:true});
 }
 function closeSettings(){dialog.close();if(settingsFocus?.isConnected)settingsFocus.focus({preventScroll:true})}
 bind(document.querySelector('#link-settings-cancel'),closeSettings);dialog.addEventListener('cancel',e=>{e.preventDefault();closeSettings()});
 bind(document.querySelector('#link-defaults'),()=>showRules(LinkRules.DEFAULTS));
 form.addEventListener('input',e=>{if(e.isComposing)return;e.target.removeAttribute('aria-invalid');document.querySelector('#link-settings-error').hidden=true});
 form.addEventListener('change',e=>{e.target.removeAttribute('aria-invalid');document.querySelector('#link-settings-error').hidden=true});
 form.addEventListener('submit',e=>{
  e.preventDefault();const rules={};for(const key of Object.keys(LinkRules.DEFAULTS)){const el=form.elements.namedItem(key);rules[key]=el.type==='checkbox'?el.checked:Number(el.value)}
  try{linked.updateRules(rules);closeSettings();window.GameUI.showToast(current.storageNote||'规则已保存，从下一手生效。',current.storageNote?'error':'success')}
  catch(error){const message=document.querySelector('#link-settings-error');message.textContent=error.message;message.hidden=false;const el=form.elements.namedItem(error.field);if(el){el.setAttribute('aria-invalid','true');el.setAttribute('aria-describedby','link-settings-error');el.focus()}}
 });
 for(const el of document.querySelectorAll('[data-link-settings]'))bind(el,openSettings);
 for(const el of document.querySelectorAll('[data-link-scroll]'))bind(el,()=>document.querySelector('#link-poker').scrollIntoView({block:'start',behavior:document.documentElement.dataset.motion==='reduced'?'auto':'smooth'}));
 function renderRoot(root,s){
  const ui=root.linkElements,keys=root.linkKeys,queue=s.tasks.filter(pending),done=s.tasks.filter(t=>!pending(t));
  const canWork=s.live.phase==='complete',canConfigure=['setup','complete'].includes(s.live.phase);
  text(ui.count,queue.length+' 项');prop(ui.settings,'disabled',!canConfigure);
  text(ui.phase,s.live.phase==='setup'?'联动'+(s.rules.enabled?'已开启':'已关闭')+' · 在德扑结算后生成挑战':canWork?'第 '+s.live.handNo+' 手已结束 · 可以处理待办，也可以继续下一手':'第 '+s.live.handNo+' 手'+(s.live.phase==='showdown'?'正在逐家揭晓':'进行中')+' · 挑战暂存，本手结束后处理');
  text(ui.summary,'待办 '+queue.length+' · 已完成 '+done.filter(t=>t.status==='completed').length+' · 已跳过 '+done.filter(t=>t.status==='skipped').length+(s.rules.enabled?'':' · 已停止新增挑战'));
  prop(ui.empty,'hidden',s.tasks.length>0);prop(ui.work,'hidden',!s.tasks.length);
  text(ui['empty-text'],s.lastSettlement?'本手没有新增挑战。净变化为零的平局不会生成任务。你可以继续下一手。':'打完一手，心动挑战会自动排队。你可以继续打牌，之后再来慢慢完成。');
  const listKey=s.tasks.map(t=>t.id+':'+t.status).join('|');
  if(keys.list!==listKey){
   const groups=[];for(const [label,tasks] of [['待办',queue],['已处理',done.slice().reverse()]]){if(!tasks.length)continue;const group=make('optgroup');group.label=label;for(const t of tasks){const person=t.roster.find(p=>p.id===t.participantId);group.append(option(t.id,'第 '+t.handNo+' 手 · 座位 '+(person.seat+1)+' '+person.name+' · '+levels[t.level]+(t.status==='completed'?' · 已完成':t.status==='skipped'?' · 已跳过':'')))}groups.push(group)}
   ui.task.replaceChildren(...groups);keys.list=listKey;
  }
  const t=s.tasks.find(t=>t.id===s.selectedId);if(t){
   prop(ui.task,'value',t.id);const person=t.roster.find(p=>p.id===t.participantId),chooser=t.roster.find(p=>p.id===t.chooserId),partner=t.roster.find(p=>p.id===t.partnerId),open=pending(t);
   text(ui.target,'座位 '+(person.seat+1)+' · '+person.name+' 的挑战');text(ui.level,t.level+' 级 · '+levels[t.level]);
   text(ui.reasons,'第 '+t.handNo+' 手 · '+t.reasons.join(' · '));text(ui.money,'开手 '+t.startChips+' → 结算 '+t.endChips+' · 净变化 '+t.netDelta+' 筹码');
   text(ui.chooser,'奖励选择权：座位 '+(chooser.seat+1)+' · '+chooser.name+'，请选择真心话或大冒险。');
   for(const type of ['truth','dare']){prop(ui[type],'disabled',!open||!canWork);ui[type].setAttribute('aria-pressed',String(t.type===type))}
   const rosterKey=t.id;if(keys.roster!==rosterKey){ui.partner.replaceChildren(option('','请选择另一位玩家'),...t.roster.filter(p=>p.id!==t.participantId).map(p=>option(p.id,'座位 '+(p.seat+1)+' · '+p.name)));keys.roster=rosterKey}
   prop(ui.partner,'value',t.partnerId||'');prop(ui.partner,'disabled',!open||!canWork);text(ui['partner-label'],person.name+' 选择互动搭档');
   text(ui.pair,partner?'题目里的“你”＝'+person.name+'（座位 '+(person.seat+1)+'），“我”＝'+partner.name+'（座位 '+(partner.seat+1)+'）。':'搭档由接受挑战者自行选择，双方都愿意再开始。');
   prop(ui.question,'hidden',!t.question);prop(ui.placeholder,'hidden',!!t.question);
   if(t.question){text(ui['question-meta'],t.question.category+' · '+levels[t.question.linkDifficulty]+' · #'+t.question.id+(t.question.linkDifficulty<t.level?' · 本级题目不足，已选较低难度':''));text(ui['question-text'],t.question.text)}
   text(ui.error,t.error);prop(ui.error,'hidden',!t.error);text(ui.redraw,t.question?'换一题':'抽取挑战');
   prop(ui.redraw,'disabled',!open||!canWork||!t.type||!t.partnerId);prop(ui.complete,'disabled',!open||!canWork||!t.question);prop(ui.skip,'disabled',!open||!canWork);
   prop(ui.resolved,'hidden',open);text(ui.resolved,t.status==='completed'?'这一项已完成。':t.status==='skipped'?'这一项已跳过。':'');prop(ui.next,'hidden',open||!queue.length);prop(ui.next,'disabled',!canWork);
  }
  text(ui['history-label'],'联动记录 · 已处理 '+done.length+' 项');
  const historyKey=done.map(t=>t.id+':'+t.status).join('|');if(keys.history!==historyKey){ui.history.replaceChildren(...done.slice(-10).reverse().map(t=>make('li','第 '+t.handNo+' 手 · '+t.roster.find(p=>p.id===t.participantId).name+' · '+(t.status==='completed'?'已完成':'已跳过'))));if(!done.length)ui.history.append(make('li','还没有处理记录。'));keys.history=historyKey}
 }
 linked.subscribe(s=>{
  current=s;const count=s.tasks.filter(pending).length;
  for(const el of document.querySelectorAll('[data-link-count]')){text(el,count>99?'99+':count);prop(el,'hidden',count===0)}
  for(const el of document.querySelectorAll('[data-link-settings]'))prop(el,'disabled',!['setup','complete'].includes(s.live.phase));
  const liveCount=document.querySelector('#link-pending-label');if(liveCount)text(liveCount,'联动'+(s.rules.enabled?'已开启':'已关闭')+' · 待办 '+count);
  for(const root of roots)renderRoot(root,s);
  const note=document.querySelector('#link-storage-note');text(note,s.storageNote);prop(note,'hidden',!s.storageNote);
  if(s.tableId===knownTable&&count>knownPending)text(document.querySelector('#link-announcement'),'第 '+s.live.handNo+' 手结算完成，新增 '+(count-knownPending)+' 项心动挑战，已加入待办。');
  knownPending=count;knownTable=s.tableId;
 });
 return {pendingCount:()=>current.tasks.filter(pending).length};
})();
~~~~~~~~~~

## 50. `/workspace/output/linked-edition/src/link.css`

~~~~~~~~~~
/* Linked challenges inherit the sunset palette and the existing Chinese sans. */
.link-count{display:inline-grid;place-items:center;min-width:22px;height:22px;padding:0 6px;background:#F3AB98;color:#251D29;border-radius:8px;font-size:11px;font-weight:750;font-variant-numeric:tabular-nums;line-height:1}
.nav-tab .link-count,.mode-btn .link-count{position:absolute;top:-4px;right:-3px;min-width:17px;height:17px;border-radius:6px;font-size:9px;padding:0 4px;box-shadow:0 0 0 2px #172132}
.nav-tab,.mode-btn{position:relative}
.link-toolbar{display:flex;justify-content:space-between;gap:12px;align-items:center;padding:0 4px 12px;margin-top:-3px}
.link-toolbar button{font-family:var(--font);font-size:12px;min-height:44px}
.link-toolbar [data-link-scroll]{color:#FFD3C5;text-align:left;padding:8px 0}
.link-panel{width:100%;min-width:0;padding:23px;background:#1B293B;border:1px solid var(--surface-line);border-radius:22px;margin-top:22px;color:var(--ink);scroll-margin-top:155px}
#mode-linked .link-panel{margin-top:24px}
.link-panel-heading{display:flex;justify-content:space-between;gap:14px;align-items:center}
.link-panel-heading h3{font-size:22px;font-weight:650;line-height:1.6;display:flex;gap:10px;align-items:center}
.link-kicker{color:#E8B4BE;font-size:10px;letter-spacing:1px;margin-bottom:5px}
.link-panel .pk-quiet,.link-panel .pk-secondary,.link-panel .pk-primary{min-height:44px;font-family:var(--font)}
.link-phase{margin:17px 0 7px;padding:10px 13px;background:#293248;border:1px solid #756276;border-radius:10px;color:#FFE1CE;font-size:12px;line-height:1.9}
.link-summary{color:var(--muted);font-size:11px;line-height:1.9;margin:6px 0 17px}
.link-empty{padding:24px 18px;text-align:center;border:1px dashed #846D80;border-radius:17px;background:#222A3D}
.link-empty>span{display:block;color:#F3AB98;font-size:36px;line-height:1.5;margin-bottom:6px}
.link-empty p{font-size:13px;color:var(--muted);line-height:1.9;max-width:31em;margin:auto}
.link-task-picker,.link-partner-field{display:flex;flex-direction:column;gap:8px;color:var(--muted);font-size:12px;line-height:1.8}
.link-task-picker select,.link-partner-field select{width:100%;min-width:0;min-height:46px;font-size:13px;font-family:var(--font)}
.link-task{margin-top:17px;padding:22px;background:#292B40;border:1px solid #9A7A8A;border-radius:18px;min-width:0}
.link-task-heading{display:flex;justify-content:space-between;gap:12px;align-items:flex-start}
.link-task h4{font-size:19px;line-height:1.7;overflow-wrap:anywhere;font-weight:650}
.link-level{font-size:10px;color:#FFE2BE;background:#4A3545;border:1px solid #AE8495;padding:5px 8px;border-radius:7px;white-space:nowrap}
.link-reasons,.link-task-money{font-size:11px;line-height:1.9;color:#DEC5CC;overflow-wrap:anywhere;margin-top:5px;font-variant-numeric:tabular-nums}
.link-task-money{color:#FFE2BE;margin-top:8px}
.link-chooser{font-size:12px;line-height:1.9;margin:18px 0 10px;color:#FFE1CE;overflow-wrap:anywhere}
.link-type-buttons{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:18px}
.link-type-buttons button{min-height:46px;border:1px solid #9D8297;border-radius:11px;font:600 13px var(--font);padding:10px 12px;background:#352C43;color:#FFD3DB}
.link-type-buttons .link-dare{background:#433239;color:#FFE2BE}
.link-type-buttons button[aria-pressed="true"]{background:var(--primary);color:var(--on-primary);border-color:var(--primary)}
.link-pair{font-size:11px;line-height:1.9;color:var(--muted);margin-top:10px;overflow-wrap:anywhere}
.link-question{margin-top:17px;padding:22px 20px;border-radius:15px;border:1px solid #C18D9B;background:linear-gradient(150deg,#493449,#302D45);min-height:145px}
.link-question-meta{font-size:10px;line-height:1.9;color:#FFD0C7;margin-bottom:13px;overflow-wrap:anywhere}
.link-question-text{font-size:20px;line-height:1.9;letter-spacing:.3px;color:#FFF2E9;overflow-wrap:anywhere}
.link-question-placeholder{padding:20px 0;font-size:12px;line-height:1.9;color:var(--muted)}
.link-task-actions{display:flex;flex-wrap:wrap;gap:10px;margin-top:18px}
.link-task-actions button{flex:1;white-space:normal;font-size:12px;min-width:85px}
.link-resolved{font-size:14px;color:#FFE2BE;line-height:1.9;margin-top:17px}
.link-next{margin-top:12px;font-size:12px}
.link-history{border-top:1px solid var(--surface-line);margin-top:20px;padding-top:12px;color:var(--muted);font-size:11px;line-height:1.9}
.link-history summary{min-height:36px;padding:6px 0;cursor:pointer;color:#FFD3C5}
.link-history ol{padding-left:20px;margin-top:8px}
.link-history li{padding:5px 0;overflow-wrap:anywhere}
.link-settings-dialog{width:min(640px,calc(100vw - 30px));max-width:640px;max-height:90vh;max-height:90dvh;overflow:auto;padding:27px;color:var(--ink);border-color:#98788D;overscroll-behavior:contain}
.link-settings-dialog::backdrop{background:#0D1524E8}
.link-settings-dialog h2{font-size:23px;line-height:1.7}
#link-settings-help{font-size:12px;line-height:1.9;color:var(--muted);margin:9px 0 17px}
.link-rule-switches{display:flex;flex-direction:column;gap:8px;margin-bottom:17px}
.link-rule-switches label,.link-rule-check{display:flex;align-items:center;gap:10px;font-size:13px;line-height:1.8;min-height:40px}
.link-settings-dialog input[type=checkbox]{width:18px;height:18px;min-height:18px;padding:0;margin:0;flex:none;accent-color:#F3AB98}
.link-rule-grid{display:grid;grid-template-columns:1fr 1fr;gap:15px 14px;margin:12px 0}
.link-rule-grid label{display:flex;flex-direction:column;gap:7px;font-size:12px;line-height:1.8;color:var(--muted)}
.link-rule-grid input,.link-rule-grid select{width:100%;min-width:0;min-height:44px;font-size:13px;font-family:var(--font)}
.link-hint{font-size:11px;line-height:1.9;color:var(--muted);margin:9px 0 15px}
.link-rule-actions{display:flex;justify-content:space-between;gap:15px;flex-wrap:wrap;align-items:center;margin-top:20px}
.link-rule-actions>div{display:flex;gap:10px}
.link-rule-actions button{min-height:44px;font-size:12px;font-family:var(--font)}
.link-storage-note{color:#FFD3C5;background:#493343;border:1px solid #AF8A9F;border-radius:10px;font-size:12px;padding:10px 13px;line-height:1.9;margin-top:12px}
.link-grade-field{display:flex;flex-direction:column;gap:4px;font-size:10px;color:var(--muted)}
.link-grade-field select{width:104px;min-height:37px;font-size:11px;padding:8px;font-family:var(--font)}
.list-item-actions{display:flex;flex-direction:column;gap:8px;align-items:flex-end}
.link-add-grade{display:flex;align-items:center;gap:12px;font-size:11px;color:var(--muted)}
.link-add-grade select{min-width:120px;min-height:40px;font-size:12px;font-family:var(--font)}
.link-bank-form .add-type{grid-column:1;grid-row:1}.link-bank-form .add-text{grid-column:2;grid-row:1}.link-bank-form .add-tags{grid-column:3;grid-row:1}.link-bank-form .btn-add{grid-column:4;grid-row:1}.link-bank-form .link-add-grade{grid-column:2/4;grid-row:2}
@media(hover:hover) and (pointer:fine){.link-type-buttons button:not(:disabled):not([aria-pressed=true]):hover{background:#504058;color:#FFE2BE}}
@media(max-width:1050px){.link-bank-form{grid-template-columns:110px minmax(0,1fr) auto}.link-bank-form .add-tags{grid-column:2;grid-row:2}.link-bank-form .btn-add{grid-column:3;grid-row:1/3}.link-bank-form .link-add-grade{grid-column:2;grid-row:3}}
@media(max-width:600px){
 .game-mode-bar{flex-wrap:wrap;gap:12px}.mode-selector{width:100%}.mode-selector .mode-btn{flex:1;font-size:11px;padding:10px 7px;min-height:42px}.round-counter{margin-left:auto}
 .link-toolbar{gap:10px}.link-toolbar button{font-size:10px}.link-panel{padding:18px 14px;border-radius:18px;margin-top:18px}.link-panel-heading{gap:8px}.link-panel-heading h3{font-size:19px;gap:8px}.link-panel-heading .pk-quiet{padding:8px 10px;font-size:10px}.link-kicker{font-size:9px;letter-spacing:.5px}.link-phase{font-size:11px;padding:9px 10px;margin-top:14px}.link-summary{font-size:10px}.link-empty{padding:20px 12px}.link-empty p{font-size:12px}.link-task{padding:17px 12px;border-radius:14px}.link-task-heading{flex-wrap:wrap;gap:7px}.link-task h4{font-size:16px}.link-reasons,.link-task-money,.link-pair{font-size:10px}.link-chooser{font-size:11px;margin-top:15px}.link-task-picker,.link-partner-field{font-size:11px}.link-task-picker select,.link-partner-field select{font-size:12px;padding:10px 8px}.link-question{padding:18px 13px;min-height:145px}.link-question-text{font-size:17px;line-height:1.95}.link-task-actions{gap:8px}.link-task-actions button{font-size:11px;min-width:72px;padding:10px 8px}.link-task-actions .pk-quiet{flex-basis:100%}.link-history{font-size:10px}.link-settings-dialog{padding:22px 17px}.link-settings-dialog h2{font-size:21px}.link-rule-grid{gap:13px 10px}.link-rule-grid label{font-size:11px}.link-rule-grid input,.link-rule-grid select{font-size:12px;padding:10px 8px}.link-rule-switches label,.link-rule-check{font-size:12px}.link-rule-actions{gap:12px}.link-rule-actions>div{margin-left:auto}.link-rule-actions button{font-size:11px}
 .link-bank-form{grid-template-columns:105px minmax(0,1fr)}.link-bank-form .add-type{grid-column:1;grid-row:1}.link-bank-form .add-text{grid-column:2;grid-row:1}.link-bank-form .add-tags{grid-column:1/-1;grid-row:2}.link-bank-form .link-add-grade{grid-column:1/-1;grid-row:3}.link-bank-form .btn-add{grid-column:1/-1;grid-row:4}.list-item-actions{flex-direction:row;align-items:flex-end;gap:12px}.link-grade-field select{min-height:40px}
}
@media(max-width:350px){.link-panel-heading h3{font-size:17px}.link-panel .link-count{font-size:10px}.link-panel{padding:17px 12px}.link-task{padding:16px 10px}.link-task-money{font-size:9px}.link-panel-heading .pk-quiet{font-size:9px}.link-bank-form{grid-template-columns:1fr}.link-bank-form .add-type{grid-column:1;grid-row:1}.link-bank-form .add-text{grid-column:1;grid-row:2}.link-bank-form .add-tags{grid-column:1;grid-row:3}.link-bank-form .link-add-grade{grid-column:1;grid-row:4}.link-bank-form .btn-add{grid-column:1;grid-row:5}.link-rule-actions>div{width:100%}.link-rule-actions>div button{flex:1}}
@media(prefers-reduced-motion:reduce){.link-new-task{animation:none!important}}
@keyframes link-arrive{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
html:not([data-motion=reduced]) .link-new-task{animation:link-arrive 240ms ease-out both}
@media(forced-colors:active){.link-panel,.link-task,.link-phase,.link-question,.link-empty,.link-settings-dialog{background:Canvas;color:CanvasText;border:1px solid CanvasText}.link-type-buttons button,.link-level{background:Canvas;color:CanvasText;border:1px solid CanvasText}.link-type-buttons button[aria-pressed=true],.link-count{background:Highlight;color:HighlightText}.link-question-text,.link-question-meta,.link-chooser,.link-phase,.link-task-money{color:CanvasText}.link-settings-dialog::backdrop{background:Canvas}}
~~~~~~~~~~

## 51. `/workspace/output/linked-edition/build.py`

~~~~~~~~~~
from pathlib import Path
root=Path(__file__).resolve().parent;src=root/'src'
s=(src/'core-game.html').read_text()
s=s.replace('<html lang="zh-CN">','<html lang="zh-CN" data-active-tab="game">',1)
newtab='        <button class="nav-tab" id="nav-poker" role="tab" aria-selected="false" aria-controls="tab-poker" tabindex="-1" data-tab="poker">德州扑克 <span class="link-count" data-link-count hidden></span></button>\n'
s=s.replace('      </nav>',newtab+'      </nav>',1)
s=s.replace('<footer class="app-footer">',(src/'poker-panel.html').read_text()+'\n<footer class="app-footer">',1)
s=s.replace('<script id="shared-actions">',(src/'poker-overlays.html').read_text()+'\n'+(src/'link-settings.html').read_text()+'\n<script id="shared-actions">',1)
s=s.replace("this.state.currentTab = name;document.title=", "this.state.currentTab = name;document.documentElement.dataset.activeTab=name;document.dispatchEvent(new CustomEvent('app:tab-change',{detail:name}));document.title=",1)
s=s.replace("bank:'我的题库'}", "bank:'我的题库',poker:'德州扑克'}",1)
s=s.replace('</head>','<style id="poker-design">'+(src/'poker.css').read_text()+'</style><style id="link-design">'+(src/'link.css').read_text()+'</style></head>',1)
def factory(file,marker):
 return (src/file).read_text().split(marker,1)[1].rsplit('\n});',1)[0]
link=factory('link-core.js',"})(typeof globalThis!=='undefined'?globalThis:this,function(){")
s=s.replace('<script id="shared-actions">','<script id="link-rules">const LinkRules=(()=>{'+link+'\n})();</script>\n<script id="shared-actions">',1)
engine=factory('poker-engine.js',"})(typeof globalThis!=='undefined'?globalThis:this,function(){")
script="(()=>{\n'use strict';\nconst PokerRules=(()=>{"+engine+'\n})();\n'+(src/'link-ui.js').read_text()+'\n'+(src/'poker-ui.js').read_text()+'\n})();'
s=s.replace('</body>','<script id="linked-runtime">'+script+'</script></body>',1)
(src/'maogou-xindongju-linked-v7.html').write_text(s)
(root.parent/'maogou-xindongju-linked-v7.html').write_text(s)
print('Built linked standalone:',len(s.encode()),'bytes')
~~~~~~~~~~

## 52. `/workspace/output/linked-edition/tests/link-rules.cjs`

~~~~~~~~~~
const assert=require('node:assert/strict'),fs=require('node:fs'),path=require('node:path');
const {DEFAULTS,validateRules,selectQuestion,planChallenges,LinkService}=require('../src/link-core.js');
const checks=[];const question=(id,type,level)=>({id,type,text:id+' 题目',category:type==='truth'?'真心话':'大冒险',tags:[],linkDifficulty:level,usedCount:0});
const questions=[question('T1','truth',1),question('T2','truth',2),question('T3','truth',3),question('D1','dare',1),question('D2','dare',2),question('D3','dare',3)];
function settlement(ends,{tableId='table',handNo=1,starts=ends.map(()=>1000),dealer=0,kind='showdown',categories=[],folded=[],inHand=[]}={}){
 return {tableId,handNo,phase:'complete',actor:null,dealer,kind,players:ends.map((endChips,seat)=>({id:tableId+':seat:'+seat,seat,name:seat<2?'同名':'玩家'+seat,startChips:starts[seat],endChips,netDelta:endChips-starts[seat],inHand:inHand[seat]??true,folded:folded.includes(seat),handCategory:categories[seat]??null}))};
}
for(const [loss,expected] of [[1,1],[199,1],[200,2],[499,2],[500,3],[1000,3]])assert.equal(planChallenges(settlement([1000-loss,1000+loss]),DEFAULTS)[0].level,expected);
checks.push('净亏损分级与 20%／50% 精确边界，淘汰玩家保留挑战');
assert.equal(planChallenges(settlement([990,1010],{kind:'fold',categories:[8,8]}),DEFAULTS)[0].level,1);
assert.equal(planChallenges(settlement([990,1010],{categories:[8,5]}),DEFAULTS)[0].level,2);
assert.equal(planChallenges(settlement([500,1500],{categories:[8,8]}),DEFAULTS)[0].level,3);
assert.equal(planChallenges(settlement([990,1010],{categories:[8,1]}),DEFAULTS)[0].level,1);
assert.equal(planChallenges(settlement([990,1010],{categories:[1,8],folded:[1]}),DEFAULTS)[0].level,1);
checks.push('特殊牌型只来自摊牌且净盈利未弃牌者；折叠升级封顶，弃牌获胜不评估牌型');
const ties=planChallenges(settlement([800,800,1400]),DEFAULTS);assert.deepEqual(ties.map(t=>t.participantId),['table:seat:0','table:seat:1']);assert.ok(ties.every(t=>t.chooserId==='table:seat:2'));
assert.equal(planChallenges(settlement([600,1200,1200],{dealer:1}),DEFAULTS)[0].chooserId,'table:seat:2');
assert.equal(planChallenges(settlement([1000,1000]),DEFAULTS).length,0);assert.equal(planChallenges(settlement([1000,0,1000],{starts:[1000,0,1000],inHand:[true,false,true]}),DEFAULTS).length,0);
checks.push('并列输家按座位入队、并列赢家从庄家左侧选人、平局与休息座位不产生挑战');
assert.equal(planChallenges(settlement([990,1010]),{...DEFAULTS,enabled:false}).length,0);
assert.equal(planChallenges(settlement([990,1010]),{...DEFAULTS,perHand:false,lossEnabled:false,specialEnabled:false}).length,0);
assert.equal(planChallenges(settlement([800,1200]),{...DEFAULTS,perHand:false})[0].level,2);
assert.equal(planChallenges(settlement([990,1010],{categories:[1,5]}),{...DEFAULTS,perHand:false,lossEnabled:false})[0].level,2);
checks.push('可独立配置常规／阈值／特殊触发，总开关停止新增');
assert.throws(()=>validateRules({...DEFAULTS,threshold2:50,threshold3:20}));assert.throws(()=>validateRules({...DEFAULTS,threshold2:1.5}));assert.throws(()=>validateRules({...DEFAULTS,maxLevel:4}));assert.throws(()=>validateRules({...DEFAULTS,enabled:'true'}));
assert.equal(selectQuestion(questions,{type:'truth',level:2,random:()=>0}).id,'T2');assert.equal(selectQuestion(questions.filter(q=>q.id!=='T2'),{type:'truth',level:2}).id,'T1');assert.equal(selectQuestion([question('X','truth',3)],{type:'truth',level:1}),null);assert.equal(selectQuestion([question('X','truth',1)],{type:'truth',level:1,excludeId:'X'}),null);
checks.push('配置校验；同类型按等级选题，只向下回退，不重复唯一旧题，不抽未分级题');
let tableSequence=0,saved=null,pool=questions.slice();const store=new LinkService({idFactory:()=> 't'+(++tableSequence),pickQuestion:options=>selectQuestion(pool,options),saveRules:r=>saved=r});const tid=store.startTable();
const first=settlement([800,1200],{tableId:tid});store.sync({...first,phase:'playing'});assert.throws(()=>store.updateRules(DEFAULTS));assert.equal(store.snapshot().tasks.length,0);store.sync(first);assert.equal(store.snapshot().tasks.length,1);assert.equal(store.sync(first),false);assert.equal(store.snapshot().tasks.length,1);
let task=store.snapshot().tasks[0];assert.equal(task.level,2);assert.equal(store.sync({...first,phase:'playing'}),false);
assert.throws(()=>store.choosePartner(task.id,task.participantId));store.chooseType(task.id,'truth');assert.equal(store.snapshot().tasks[0].question,null);store.choosePartner(task.id,first.players[1].id);assert.equal(store.snapshot().tasks[0].status,'ready');assert.equal(store.snapshot().tasks[0].question.id,'T2');
const copy=store.snapshot();copy.tasks[0].question.text='篡改副本';assert.notEqual(store.snapshot().tasks[0].question.text,'篡改副本');pool=[];store.redraw(task.id);assert.equal(store.snapshot().tasks[0].question.id,'T2');assert.ok(store.snapshot().tasks[0].error);pool=questions.slice();
checks.push('结算幂等、同名按玩家标识区分、类型与搭档齐全才抽题、快照隔离、删题后保留已抽题');
store.updateRules({...DEFAULTS,maxLevel:1});assert.ok(saved);assert.equal(store.snapshot().tasks[0].level,2);
const next=settlement([1300,700],{tableId:tid,handNo:2,starts:[800,1200]});store.sync({...next,phase:'playing'});assert.throws(()=>store.resolve(task.id));assert.equal(store.snapshot().tasks[0].question.id,'T2');assert.equal(store.sync(first),false);store.sync(next);assert.equal(store.snapshot().tasks.length,2);assert.equal(store.snapshot().tasks[1].level,1);assert.equal(store.snapshot().tasks[0].rulesVersion,1);assert.equal(store.snapshot().tasks[1].rulesVersion,2);
store.resolve(task.id);assert.throws(()=>store.resolve(task.id));assert.equal(store.snapshot().tasks[1].status,'pending');store.resolve(store.snapshot().tasks[1].id,true);assert.deepEqual(store.snapshot().tasks.map(t=>t.status),['completed','skipped']);
checks.push('带待办继续下一手、行动期禁止挑战、旧题保留、规则下手生效、重复完成不误处理下一项');
const before=store.snapshot();assert.throws(()=>store.sync(settlement([2000,2000],{tableId:tid,handNo:3})));assert.deepEqual(store.snapshot(),before);
store.reset();assert.equal(store.snapshot().tasks.length,0);assert.equal(store.sync(next),false);assert.equal(store.snapshot().rules.maxLevel,1);const newId=store.startTable();assert.notEqual(newId,tid);assert.equal(store.sync(first),false);
checks.push('错误结算原子拒绝；重开清空队列、旧桌通知被拒绝、配置保留');
const badStore=new LinkService({pickQuestion:()=>null,idFactory:()=> 'bad',loadRules:()=>{throw Error('禁止存储')},saveRules:()=>{throw Error('满')}});assert.ok(badStore.snapshot().storageNote);badStore.updateRules({...DEFAULTS,threshold2:25});assert.equal(badStore.snapshot().rules.threshold2,25);assert.ok(badStore.snapshot().storageNote);
const badSchema=new LinkService({pickQuestion:()=>null,loadRules:()=>({schemaVersion:8,rules:DEFAULTS})});assert.deepEqual(badSchema.snapshot().rules,DEFAULTS);
checks.push('配置读取损坏或写入失败时保持内存可用并显示持久提示');
const report={checks};fs.writeFileSync(path.join(__dirname,'../link-rules-verification.json'),JSON.stringify(report,null,2));console.log(JSON.stringify(report,null,2));
~~~~~~~~~~

## 53. `/workspace/output/linked-edition/tests/link-browser.cjs`

~~~~~~~~~~
const {chromium}=require('playwright'),fs=require('node:fs'),path=require('node:path'),http=require('node:http'),assert=require('node:assert/strict');
(async()=>{
 const root=path.resolve(__dirname,'..'),html=fs.readFileSync(path.join(root,'src/maogou-xindongju-linked-v7.html'),'utf8');const server=http.createServer((req,res)=>{res.writeHead(200,{'Content-Type':'text/html;charset=utf-8'});res.end(html)});await new Promise(r=>server.listen(0,'127.0.0.1',r));const url=`http://127.0.0.1:${server.address().port}`;
 const b=await chromium.launch({executablePath:'/usr/bin/chromium',args:['--no-sandbox']}),checks=[],errors=[];const context=await b.newContext({viewport:{width:1280,height:1000},reducedMotion:'reduce'}),p=await context.newPage();p.on('pageerror',e=>errors.push(e.stack));p.setDefaultTimeout(7000);
 const $=s=>p.locator(s),P=r=>$('#link-poker [data-role="'+r+'"]'),G=r=>$('#link-game [data-role="'+r+'"]');
 const shot=async name=>{await p.evaluate(()=>scrollTo(0,0));await p.screenshot({path:path.join(root,'screenshots',name+'.png'),fullPage:true})};
 const settings=async()=>{await $('[data-link-settings]').click();assert.equal(await $('#link-settings-dialog').evaluate(e=>e.open),true)};
 const confirm=async()=>{await $('#pk-confirm-player').click();assert.equal(await $('.pk-hole-card').count(),2)};
 try{
  await p.goto(url);assert.equal(await p.evaluate(()=>QuestionService.getAll().filter(q=>[1,2,3].includes(q.linkDifficulty)).length),100);
  await $('#btn-truth').click();const quick=await $('#question-text').innerText();await $('[data-mode=session]').click();await $('#btn-start-session').click();await $('#btn-session-truth').click();const sessionQ=await $('#session-question-text').innerText(),sessionName=await $('#current-player-name').innerText();
  await $('#nav-poker').click();await settings();assert.equal(await $('#lr-enabled').evaluate(e=>e===document.activeElement),true);await $('#lr-threshold2').fill('60');await $('#lr-threshold3').fill('50');await $('#link-settings-save').click();assert.equal(await $('#link-settings-error').isVisible(),true);assert.equal(await $('#lr-threshold3').getAttribute('aria-invalid'),'true');assert.equal(await $('#lr-threshold2').inputValue(),'60');await $('#link-settings-cancel').click();await settings();assert.equal(await $('#lr-threshold2').inputValue(),'20');await $('#lr-threshold2').fill('1');await $('#link-settings-save').click();
  checks.push('100 道内置题逐题分级；规则无效输入保留、取消恢复、保存可生效');
  await $('#pk-count').selectOption('2');await $('#pk-name-0').fill('<小鹿>');await $('#pk-name-1').fill('<小鹿>');await $('#pk-start').click();assert.equal(await $('.pk-hole-card').count(),0);await confirm();await $('#pk-fold').click();assert.equal(await $('#nav-poker').getAttribute('aria-selected'),'true');assert.equal(p.url(),url+'/');assert.equal(await $('.pk-hole-card').count(),0);assert.equal(await P('count').innerText(),'1 项');assert.ok((await P('target').innerText()).includes('座位 1'));assert.equal(await P('level').innerText(),'2 级 · 心动');assert.ok((await P('money').innerText()).includes('净变化 -10'));assert.equal(await P('task').locator('option').count(),1);
  await p.evaluate(()=>{window.dispatchEvent(new Event('focus'));window.dispatchEvent(new Event('focus'))});assert.equal(await P('task').locator('option').count(),1);
  await P('truth').click();assert.equal(await P('question').isVisible(),false);await P('partner').selectOption({index:1});const firstQuestion=await P('question-text').innerText();assert.ok(firstQuestion);assert.ok((await P('pair').innerText()).includes('座位 1'));assert.ok((await P('pair').innerText()).includes('座位 2'));assert.equal(await P('complete').isEnabled(),true);await shot('poker-linked-desktop');
  checks.push('弃牌结算只入队一次、退款不算亏损、按座位区分重名、类型与搭档齐全后自动抽题，不切页不亮牌');
  await $('#pk-next-hand').click();assert.equal(await $('#pk-curtain').evaluate(e=>e.open),true);assert.equal(await $('.pk-hole-card').count(),0);assert.equal(await P('complete').isDisabled(),true);assert.equal(await P('question-text').innerText(),firstQuestion);await $('#pk-leave').click();assert.equal(await $('#session-question-text').innerText(),sessionQ);assert.equal(await $('#current-player-name').innerText(),sessionName);await $('[data-mode=quick]').click();assert.equal(await $('#question-text').innerText(),quick);await $('#mode-linked-button').click();assert.equal(await G('question-text').innerText(),firstQuestion);assert.equal(await G('complete').isDisabled(),true);
  await $('#nav-poker').click();await confirm();await $('#pk-fold').click();assert.equal(await P('count').innerText(),'2 项');assert.equal(await P('question-text').innerText(),firstQuestion);await $('#nav-game').click();await shot('game-linked-desktop');
  await G('complete').evaluate(el=>{el.click();el.click()});assert.equal(await G('count').innerText(),'1 项');assert.equal(await P('count').innerText(),'1 项');assert.equal(await G('complete').isDisabled(),true);assert.equal(await G('resolved').innerText(),'这一项已完成。');await G('next').click();await G('dare').click();await G('partner').selectOption({index:1});const oldQ=await G('question-text').innerText();await G('redraw').click();assert.notEqual(await G('question-text').innerText(),oldQ);const keptQ=await G('question-text').innerText();
  checks.push('待办不中断下一手；进行期两处禁止挑战，原快速题与轮流题不变；完成与换题实时同步且重复点击不串任务');
  await $('#nav-bank').click();await $('#search-input').fill(keptQ);await $('.search-btn').click();assert.equal(await $('.list-item').count(),1);await $('.list-item-btn.delete').click();await $('#delete-commit').click();await $('#nav-game').click();assert.equal(await G('question-text').innerText(),keptQ);await G('skip').click();assert.equal(await G('count').innerText(),'0 项');assert.equal(await P('count').innerText(),'0 项');assert.ok((await P('summary').innerText()).includes('已完成 1 · 已跳过 1'));assert.equal(await $('#completed-count').innerText(),'0');
  await $('#nav-poker').click();await settings();await $('#lr-enabled').uncheck();await $('#link-settings-save').click();await $('#pk-next-hand').click();await confirm();await $('#pk-fold').click();assert.equal(await P('task').locator('option').count(),2);assert.equal(await P('count').innerText(),'0 项');await settings();await $('#lr-enabled').check();await $('#link-settings-save').click();assert.equal(await P('task').locator('option').count(),2);await $('#pk-next-hand').click();await confirm();await $('#pk-fold').click();assert.equal(await P('count').innerText(),'1 项');
  checks.push('删除原题保留任务快照；开关只作用于下一手，不追溯或丢弃队列，不修改独立完成计数');
  for(const width of [320,390,600,900,1280]){
   await p.setViewportSize({width,height:844});for(const tab of ['poker','game','bank']){await $('#nav-'+tab).click();assert.equal(await p.evaluate(()=>document.documentElement.scrollWidth>innerWidth),false,tab+' overflow '+width)}
  }
  await p.setViewportSize({width:390,height:844});await $('#nav-game').click();await shot('game-linked-mobile');await $('#nav-poker').click();await shot('poker-linked-mobile');await settings();await shot('link-settings-mobile');assert.equal(await p.evaluate(()=>document.documentElement.scrollWidth>innerWidth),false);await $('#link-settings-cancel').click();
  await $('#pk-new-table').click();assert.ok((await $('#pk-confirm-description').innerText()).includes('1 项联动待办'));await $('#pk-confirm-cancel').click();assert.equal(await P('count').innerText(),'1 项');await $('#pk-new-table').click();await $('#pk-confirm-accept').click();assert.equal(await P('count').innerText(),'0 项');assert.equal(await G('count').innerText(),'0 项');assert.equal(await P('question-text').textContent(),'');assert.equal(await G('question-text').textContent(),'');
  const rules=await p.evaluate(()=>JSON.parse(localStorage.getItem('xindong_link_rules_v1')));assert.equal(rules.rules.threshold2,1);assert.equal(rules.rules.enabled,true);assert.ok(!JSON.stringify(rules).includes('<小鹿>'));assert.ok(!Object.keys(rules).some(k=>/players|tasks|cards|deck/.test(k)));
  await p.reload();await $('#nav-poker').click();assert.equal(await P('count').innerText(),'0 项');await settings();assert.equal(await $('#lr-threshold2').inputValue(),'1');await $('#link-settings-cancel').click();
  checks.push('320/390/600/900/1280px 两模块与题库无横向溢出；重开确认清队列，刷新仅保留非个人规则');
  // An old custom-only bank stays usable and ungraded until the user opts it into linking.
  const custom=await b.newContext({viewport:{width:390,height:844}}),cp=await custom.newPage();cp.on('pageerror',e=>errors.push(e.stack));await cp.addInitScript(()=>localStorage.setItem('truth_or_dare_data_v1',JSON.stringify({truth:[{id:'T900',text:'旧题：说一个让你开心的小细节。',type:'truth',category:'真心话',tags:[],usedCount:0}],dare:[]})));await cp.goto(url);await cp.locator('#nav-poker').click();await cp.locator('#pk-count').selectOption('2');await cp.locator('#pk-start').click();await cp.locator('#pk-confirm-player').click();await cp.locator('#pk-fold').click();await cp.locator('#link-poker [data-role=truth]').click();await cp.locator('#link-poker [data-role=partner]').selectOption({index:1});assert.equal(await cp.locator('#link-poker [data-role=error]').isVisible(),true);assert.equal(await cp.locator('#link-poker [data-role=complete]').isDisabled(),true);
  await cp.locator('#nav-bank').click();assert.equal(await cp.locator('[data-link-grade=T900]').inputValue(),'');await cp.locator('[data-link-grade=T900]').selectOption('1');await cp.locator('#add-text').fill('新题：说一句温柔的话。');await cp.locator('#add-link-difficulty').selectOption('2');await cp.locator('.btn-add').click();assert.equal(await cp.locator('[data-link-grade=T901]').inputValue(),'2');await cp.locator('#nav-poker').click();await cp.locator('#link-poker [data-role=redraw]').click();const customQ=await cp.locator('#link-poker [data-role=question-text]').innerText();assert.ok(customQ.includes('旧题'));await cp.locator('#link-poker [data-role=redraw]').click();assert.equal(await cp.locator('#link-poker [data-role=question-text]').innerText(),customQ);assert.ok((await cp.locator('#link-poker [data-role=error]').innerText()).includes('没有其他'));await custom.close();checks.push('旧自定义题保持未分级；空候选可恢复，新增与编辑难度可用，唯一题不会重复替换');
  const pub=await b.newContext({viewport:{width:1280,height:1000},reducedMotion:'reduce'}),sp=await pub.newPage();sp.on('pageerror',e=>errors.push(e.stack));await sp.goto(url);await sp.locator('#nav-poker').click();await sp.locator('#pk-count').selectOption('2');await sp.locator('#pk-spectator').check();await sp.locator('#pk-start').click();await sp.locator('#pk-allin').click();await sp.locator('#pk-call').click();assert.equal(await sp.locator('#poker-app').getAttribute('data-phase'),'showdown');assert.equal(await sp.locator('#link-poker [data-role=count]').innerText(),'0 项');await sp.waitForFunction(()=>document.querySelector('#poker-app').dataset.phase==='complete');const n=await sp.locator('#link-poker [data-role=count]').innerText();assert.ok(['0 项','1 项'].includes(n));if(n==='1 项'){assert.equal(await sp.locator('#link-poker [data-role=level]').innerText(),'3 级 · 默契');await sp.screenshot({path:path.join(root,'screenshots','showdown-linked-desktop.png'),fullPage:true})}assert.equal(await sp.locator('.pk-hole-card').count(),4);await pub.close();checks.push('旁观与逐家揭晓全程保留，结算完成前队列为零，淘汰挑战最高三级');
  const blocked=await b.newContext(),bp=await blocked.newPage();await bp.addInitScript(()=>{Storage.prototype.setItem=()=>{throw new DOMException('禁止存储','SecurityError')}});await bp.goto(url);await bp.locator('#nav-poker').click();await bp.locator('[data-link-settings]').click();await bp.locator('#lr-threshold2').fill('25');await bp.locator('#link-settings-save').click();await bp.locator('[data-link-settings]').click();assert.equal(await bp.locator('#lr-threshold2').inputValue(),'25');assert.equal(await bp.locator('#link-storage-note').isVisible(),true);await blocked.close();checks.push('本地存储不可写时联动规则继续在内存生效，保留明确提示');
  assert.deepEqual(errors,[]);const report={checks,pageErrors:errors,browser:await b.version()};fs.writeFileSync(path.join(root,'link-browser-verification.json'),JSON.stringify(report,null,2));console.log(JSON.stringify(report,null,2));
 }finally{await b.close();await new Promise(r=>server.close(r))}
})().catch(e=>{console.error(e);process.exit(1)});
~~~~~~~~~~

## 54. `/workspace/output/linked-edition/README.md`

~~~~~~~~~~
# 猫狗心动局 · 德扑联动版 v7

打开 `src/maogou-xindongju-linked-v7.html` 即可使用，图片、角色、规则和题库均已嵌入，无需服务器或外部依赖。v6 原文件保留在原目录。

## 联动玩法

1. 在“德州扑克”设置 2—6 位玩家并开始。本机轮流确认身份查看底牌；旁观模式会明确公开手牌。
2. 每手结算后，净输最多者收到心动挑战，并列者各一张。按开手筹码计算，亏损达到 20%／50% 时升至二级／三级；赢家公开同花及以上再升一级，最高三级。
3. 赢家选择真心话或大冒险，接受挑战者从本桌其他玩家中选择搭档，然后自动抽题。可以换题、完成或跳过，不会改变筹码。
4. 挑战自动排队，可以直接开始下一手。下注或逐家揭晓时暂停处理挑战，结算后恢复。
5. 在德扑下方“心动待办”和“游戏桌 → 德扑联动”都能处理同一队列，两处即时同步。独立快速抽题、轮流心动与助手保持原有流程。

“联动设置”可调整开关、阈值、牌型门槛、升级幅度和上限，保存后下一手生效。“我的题库”支持给题目设置联动难度；旧自定义题默认未分级，仍可独立抽取。牌局结束前不依据私密底牌触发任务，逐家揭晓不会被联动跳过。

规则配置和题库保存在本机。牌局、玩家、挑战队列和完成记录只在本次打开期间存在，刷新后清空；重开桌会在确认中明确待办清除数量。待办不会自动过期；已处理记录保留最近 100 项，累计完成／跳过计数完整保留。此同步仅发生在同一 HTML 内，不是跨设备同步。

隐私边界是页面 DOM 与同屏交接。单文件 JavaScript 仍需在运行内存中持有底牌，不能防止调试器检查内存。

## 开发与验证

- `src/core-game.html` 保留原真心话大冒险基础与资产，并扩展题库元数据。
- `src/link-core.js` 负责规则、队列、结算去重和配置版本；无 DOM、网络或私人底牌。
- `src/link-ui.js` 将共享状态投影到两个模块。
- `src/poker-*` 保留德扑引擎和隐私动画，并提供明确的公共结算适配。
- `python build.py` 生成独立 v7 HTML；不要直接打开未合成的核心模板。

执行 `premium-ui.json` 中全部命令可复现验证。浏览器测试需要 Node.js、Playwright、Chromium 和 axe-core，当前环境已配置。测试包含德扑规则、DOM 隐私、完整逐家动画、联动规则、跨模块任务流、旧题迁移、配置失败、触屏、响应式与无障碍检查。实际浏览器验证使用 Chromium 154；其他现代浏览器使用相同标准 DOM、原生 dialog/select 和 CSS 动画路径，未声称已逐一真机验证。

测试报告与截图在本目录。`DESIGN.md` 和 `UX-CONTRACT.md` 记录共同设计与行为；`AUDIT-NOTES.md` 保留静态审计局限及浏览器证据。
~~~~~~~~~~

