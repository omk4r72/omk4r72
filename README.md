<!--
Instructions:
- This is a single-file animated GUI profile page you can host on GitHub Pages or any static host.
- Replace placeholders like {{GITHUB_URL}}, {{TWITTER_URL}}, {{LINKEDIN_URL}} and project links.
- Add your avatar at the path or replace the <img> src with your own URL.
- The design is lightweight, mobile-responsive, and uses pure HTML/CSS/JS (no frameworks).
-->

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Omkar — Cybersecurity & Reverse Engineering</title>
  <style>
    :root{--bg:#071126;--card:#0f1724;--accent:#4fd1c5;--muted:#8aa0b2}
    *{box-sizing:border-box}
    body{margin:0;font-family:Inter,ui-sans-serif,system-ui,-apple-system,'Segoe UI',Roboto,'Helvetica Neue',Arial; background:radial-gradient(1200px 600px at 10% 10%, rgba(79,209,197,0.05), transparent 8%), radial-gradient(900px 400px at 90% 90%, rgba(99,102,241,0.03), transparent 10%), var(--bg); color:#e6eef6; -webkit-font-smoothing:antialiased}
    .wrap{max-width:1100px;margin:48px auto;padding:28px}

    /* Card */
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01)); border:1px solid rgba(255,255,255,0.04); border-radius:18px; padding:28px; box-shadow:0 8px 30px rgba(2,6,23,0.6); position:relative; overflow:hidden}

    /* Animated background lines */
    .grid-lines{position:absolute;inset:0;opacity:0.06;pointer-events:none;background-image:linear-gradient(transparent 24px, rgba(255,255,255,0.02) 25px), linear-gradient(90deg, transparent 24px, rgba(255,255,255,0.02) 25px); background-size:50px 50px; transform:translateZ(0);}

    .header{display:flex;gap:20px;align-items:center}
    .avatar{width:120px;height:120px;border-radius:18px;flex:0 0 120px; overflow:hidden; border:1px solid rgba(255,255,255,0.05)}
    .avatar img{width:100%;height:100%;object-fit:cover;display:block;filter:grayscale(0.02) contrast(1.02)}

    .title h1{margin:0;font-size:28px;letter-spacing:0.2px}
    .title p{margin:6px 0 0;color:var(--muted)}

    /* Eye motif */
    .eye-wrap{width:86px;height:86px;border-radius:999px;background:linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.01));display:flex;align-items:center;justify-content:center;box-shadow:inset 0 3px 10px rgba(0,0,0,0.6)}
    .eye{width:54px;height:54px;border-radius:999px;background:conic-gradient(from 180deg at 50% 50%, #0ea5a4, #60a5fa, #a78bfa, #0ea5a4);display:flex;align-items:center;justify-content:center; animation:spin 8s linear infinite}
    .eye::after{content:'';width:22px;height:22px;background:#071126;border-radius:50%;box-shadow:0 0 18px rgba(79,209,197,0.18)}
    @keyframes spin{to{transform:rotate(360deg)}}

    .badges{display:flex;gap:8px;margin-top:10px}
    .badge{background:rgba(255,255,255,0.03);padding:6px 10px;border-radius:999px;border:1px solid rgba(255,255,255,0.02);font-size:13px;color:var(--muted)}

    /* Two column layout */
    .cols{display:grid;grid-template-columns:1fr 380px;gap:20px;margin-top:22px}
    .panel{background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent); border-radius:12px;padding:16px;border:1px solid rgba(255,255,255,0.03)}

    /* Projects list */
    .projects{display:flex;flex-direction:column;gap:12px}
    .proj{padding:12px;border-radius:10px;background:rgba(255,255,255,0.015); border:1px solid rgba(255,255,255,0.02)}
    .proj h4{margin:0 0 6px;font-size:15px}
    .proj p{margin:0;color:var(--muted);font-size:13px}

    /* Skills */
    .skill{display:flex;justify-content:space-between;align-items:center;margin:8px 0}
    .bar{height:8px;background:rgba(255,255,255,0.03);border-radius:999px;flex:1;margin-left:10px;overflow:hidden}
    .bar > i{display:block;height:100%;background:linear-gradient(90deg,var(--accent), #7c3aed);border-radius:999px;transform-origin:left;transition:width 1s cubic-bezier(.2,.9,.3,1)}

    /* Social icons row */
    .socials{display:flex;gap:10px;flex-wrap:wrap}
    .socials a{display:inline-flex;align-items:center;padding:8px 12px;border-radius:999px;background:rgba(255,255,255,0.02);color:var(--muted);text-decoration:none;font-size:13px;border:1px solid rgba(255,255,255,0.02)}

    /* Footer */
    .meta{display:flex;justify-content:space-between;align-items:center;margin-top:18px;color:var(--muted);font-size:13px}

    /* Floating particles */
    .particles{position:absolute;inset:0;pointer-events:none}
    .particle{position:absolute;border-radius:50%;opacity:0.06}

    /* small screens */
    @media (max-width:880px){.cols{grid-template-columns:1fr;}.avatar{width:86px;height:86px;flex:0 0 86px}.title h1{font-size:22px}}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="card">
      <div class="grid-lines"></div>
      <div class="particles" id="particles"></div>

      <div class="header">
        <div class="avatar"><img id="avatar" src="https://avatars.githubusercontent.com/u/9919?s=280&v=4" alt="avatar"></div>
        <div style="flex:1">
          <div style="display:flex;align-items:center;gap:14px;justify-content:space-between">
            <div class="title">
              <h1>Omkar — Ethical Hacker & Reverse Engineer</h1>
              <p id="tagline">I break things to make them stronger. CTF player • Bug Hunter • Malware researcher</p>
              <div class="badges">
                <span class="badge">TryHackMe · Red Team</span>
                <span class="badge">OffSec Paths</span>
                <span class="badge">REMnux</span>
              </div>
            </div>
            <div style="display:flex;flex-direction:column;align-items:flex-end;gap:10px">
              <div class="eye-wrap" title="Divyadarshi — All-seeing eye">
                <div class="eye" aria-hidden="true"></div>
              </div>
              <div style="font-size:12px;color:var(--muted)">Profile README</div>
            </div>
          </div>

          <div class="meta">
            <div>Open to Collaboration • CTFs • Bug Bounties</div>
            <div id="last-updated">Updated: <span id="date">—</span></div>
          </div>
        </div>
      </div>

      <div class="cols">
        <div>
          <div class="panel">
            <h3 style="margin-top:0">About Me</h3>
            <p style="color:var(--muted);margin-top:8px">I’m Omkar — an ethical hacker, reverse engineer and bug hunter from Maharashtra. I focus on practical malware analysis, Android pentesting, and vulnerability research. I write tools, solve CTFs, and hunt zero-days.</p>

            <h4 style="margin-top:18px">Featured Projects</h4>
            <div class="projects">
              <div class="proj"><h4>Automated Android Pentesting Tool</h4><p>CLI automation for SSL pinning bypass, static & dynamic checks, rooted device workflows. (link placeholder)</p></div>
              <div class="proj"><h4>Adaptive Malware Detection (Linux)</h4><p>Research-grade detectors for rootkits, EDR evasion, GPU execution — early-stage research. (link placeholder)</p></div>
              <div class="proj"><h4>Blockchain Evidence Chain</h4><p>Secure chain-of-custody PoC built with Solidity & audit tooling. (link placeholder)</p></div>
            </div>

            <h4 style="margin-top:18px">Skills</h4>
            <div style="margin-top:8px">
              <div class="skill"><strong>C / C++</strong><div class="bar"><i style="width:92%"></i></div></div>
              <div class="skill"><strong>Reverse Engineering</strong><div class="bar"><i style="width:88%"></i></div></div>
              <div class="skill"><strong>Python</strong><div class="bar"><i style="width:90%"></i></div></div>
              <div class="skill"><strong>Android Pentest</strong><div class="bar"><i style="width:82%"></i></div></div>
            </div>

          </div>

          <div class="panel" style="margin-top:12px">
            <h4 style="margin:0">Recent Activity</h4>
            <ul style="margin-top:10px;color:var(--muted);padding-left:18px">
              <li>Solidity scanner POC — 2025</li>
              <li>OSED path started — 2025</li>
              <li>Rooted Redmi Note 7 Pro — Jan 4, 2025</li>
            </ul>
          </div>
        </div>

        <aside>
          <div class="panel">
            <h4 style="margin:0">Contact & Social</h4>
            <div style="margin-top:10px" class="socials">
              <a id="github-link" href="{{GITHUB_URL}}" target="_blank">GitHub</a>
              <a id="twitter-link" href="{{TWITTER_URL}}" target="_blank">X / Twitter</a>
              <a id="linkedin-link" href="{{LINKEDIN_URL}}" target="_blank">LinkedIn</a>
              <a id="tryhackme-link" href="{{TRYHACKME_URL}}" target="_blank">TryHackMe</a>
            </div>

            <h4 style="margin-top:16px">Quick Stats</h4>
            <div style="display:flex;gap:8px;flex-wrap:wrap;margin-top:10px">
              <div class="badge">CTFs: Active</div>
              <div class="badge">Repos: 0</div>
              <div class="badge">Followers: 0</div>
            </div>

            <h4 style="margin-top:16px">Signature</h4>
            <p style="color:var(--muted);font-size:13px">“Cybersecurity is a mindset.” — Omkar</p>

          </div>
        </aside>
      </div>

    </div>
  </div>

  <script>
    // small helpers: replace placeholders with real links if present in location.hash
    (function(){
      // set last-updated date
      document.getElementById('date').innerText = new Date().toLocaleDateString();

      // particles generator
      const pzone = document.getElementById('particles');
      function makeParticle(){
        const d=document.createElement('div'); d.className='particle';
        const size = Math.random()*12+6; d.style.width = size+'px'; d.style.height = size+'px';
        d.style.left = Math.random()*100+'%'; d.style.top = Math.random()*100+'%';
        d.style.background = 'radial-gradient(circle at 30% 30%, rgba(79,209,197,0.18), rgba(79,209,197,0.02))';
        pzone.appendChild(d);
        setTimeout(()=>{d.style.transition='transform 6s linear,opacity 3s'; d.style.transform='translateY(-40px)'; d.style.opacity='0';},50);
        setTimeout(()=>d.remove(),7000);
      }
      setInterval(makeParticle,900);

      // typing effect for tagline
      const tag = document.getElementById('tagline');
      const phrases = ['I break things to make them stronger.','CTF player • Bug Hunter • Malware researcher','Automation • Reverse Engineering • Bug Hunting'];
      let pi=0, ci=0;
      function type(){
        const txt = phrases[pi];
        tag.innerText = txt.slice(0,ci);
        ci++;
        if(ci>txt.length){ setTimeout(()=>{ ci=0; pi=(pi+1)%phrases.length; setTimeout(type,200); },1200); }
        else setTimeout(type,40);
      }
      setTimeout(type,600);

      // placeholder link safe-replace: if user sets window.profileLinks = { github:'...', twitter:'...' }
      window.profileLinks = window.profileLinks || {};
      function applyLinks(){
        const map = { 'github-link':'{{GITHUB_URL}}', 'twitter-link':'{{TWITTER_URL}}','linkedin-link':'{{LINKEDIN_URL}}','tryhackme-link':'{{TRYHACKME_URL}}' };
        Object.keys(map).forEach(id=>{
          const el = document.getElementById(id);
          const placeholder = map[id];
          const url = (window.profileLinks[id] || '').trim() || placeholder;
          if(url && !url.includes('{{')) el.href = url; else el.href='#';
        });
      }
      applyLinks();

      // small animation trigger for skill bars to animate in
      function animateSkills(){
        document.querySelectorAll('.bar > i').forEach(i=>{ const w = i.style.width; i.style.width='0%'; setTimeout(()=>i.style.width=w,340); });
      }
      setTimeout(animateSkills,800);

    })();
  </script>
</body>
</html>
