
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Advanced CV Builder</title>

  <!-- libs for PDF -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

  <style>
    :root{
      --bg1:#0f172a; --bg2:#1e293b; --card:#111827; --muted:#94a3b8;
      --primary:#38bdf8; --accent:#facc15; --ring:#22d3ee;
      --text:#e5e7eb; --soft:#334155;
    }
    *{box-sizing:border-box}
    body{
      margin:0; min-height:100vh; font-family:system-ui,Arial,sans-serif;
      background: radial-gradient(1200px 600px at 20% -10%, #0a1729 0%, transparent 60%),
                  radial-gradient(1200px 600px at 120% 110%, #0a1729 0%, transparent 60%),
                  linear-gradient(135deg,var(--bg1),var(--bg2) 60%, var(--bg1));
      color:var(--text); display:flex; align-items:flex-start; justify-content:center; padding:24px;
    }
    .wrap{width:100%; max-width:1100px; display:grid; gap:24px; grid-template-columns:1fr; }
    @media (min-width:1000px){ .wrap{ grid-template-columns: 520px 1fr; align-items:start; } }

    /* form */
    .card{
      background: rgba(17,24,39,0.85);
      border:1px solid rgba(148,163,184,0.15);
      border-radius:20px; padding:20px;
      backdrop-filter: blur(8px);
      box-shadow: 0 10px 30px rgba(0,0,0,0.45), inset 0 1px 0 rgba(255,255,255,0.03);
    }
    h1{margin:0 0 8px; font-size:26px}
    .sub{margin:0 0 16px; color:var(--muted)}
    .row{display:grid; gap:12px; grid-template-columns:1fr}
    @media (min-width:640px){ .row.two{ grid-template-columns:1fr 1fr; } }
    label{font-weight:600; font-size:13px; color:#cbd5e1}
    input,textarea,select{
      width:100%; border:1px solid var(--soft); background:#0b1220; color:var(--text);
      padding:10px 12px; border-radius:10px; outline:none; transition:.2s;
    }
    input:focus,textarea:focus,select:focus{border-color:var(--ring); box-shadow:0 0 0 3px rgba(34,211,238,.2)}
    textarea{min-height:96px; resize:vertical}
    .hint{color:var(--muted); font-size:12px; margin-top:-6px}

    .btns{display:flex; gap:10px; flex-wrap:wrap; margin-top:10px}
    .btn{
      border:none; cursor:pointer; border-radius:12px; padding:10px 16px; font-weight:700;
      transition:.2s; letter-spacing:.2px;
    }
    .primary{background:var(--primary); color:#06253b}
    .primary:hover{filter:brightness(1.05)}
    .ghost{background:transparent; color:var(--primary); border:1px solid var(--primary)}
    .ghost:hover{background:rgba(56,189,248,0.08)}
    .danger{background:#ef4444; color:white}
    .danger:hover{filter:brightness(1.05)}

    /* preview */
    .preview{
      position:sticky; top:24px;
    }
    .cv{
      background:#0b1324; border:1px solid rgba(148,163,184,.18); border-radius:24px;
      padding:22px; box-shadow: 0 20px 40px rgba(0,0,0,0.4);
    }
    .hero{display:flex; gap:16px; align-items:center; margin-bottom:8px}
    .photo{width:76px; height:76px; border-radius:18px; object-fit:cover; border:2px solid var(--primary)}
    .avatar{width:76px; height:76px; border-radius:18px; background:linear-gradient(135deg,#2563eb,#06b6d4);
      display:flex; align-items:center; justify-content:center; color:white; font-weight:800; font-size:22px}
    .nm{font-size:22px; font-weight:800; margin:0}
    .tag{color:var(--muted); margin:2px 0 0}
    .sec{margin-top:18px}
    .sec h3{margin:0 0 10px; font-size:15px; color:var(--accent); letter-spacing:.3px}
    .kv p{margin:4px 0}
    .kv b{color:#f3f4f6}
    .grid-2{display:grid; gap:10px; grid-template-columns:1fr}
    @media (min-width:600px){ .grid-2{grid-template-columns:1fr 1fr} }
    table{width:100%; border-collapse:collapse; overflow:hidden; border-radius:12px}
    th,td{border:1px solid #22304a; padding:10px; text-align:left; font-size:14px}
    th{background:#0e1a31; color:#cfe6ff}
    .sign{height:60px; display:block; object-fit:contain}
    .muted{color:var(--muted)}
  </style>
</head>
<body>
  <div class="wrap">

    <!-- ========== FORM ========== -->
    <form id="cvForm" class="card">
      <h1>Advanced CV Builder</h1>
      <p class="sub">Fill the form. Click <b>Preview CV</b> to see the designed card. Then <b>Save as PDF</b>.</p>

      <div class="row two">
        <div>
          <label>Full Name</label>
          <input name="name" placeholder="Ayush Kar" required />
        </div>
        <div>
          <label>Father's Name</label>
          <input name="father" placeholder="Pradip Kar" />
        </div>
      </div>

      <div class="row two">
        <div>
          <label>Phone</label>
          <input name="phone" placeholder="+91 0000000000" required />
        </div>
        <div>
          <label>Email</label>
          <input type="email" name="email" placeholder="name@example.com" required />
        </div>
      </div>

      <div class="row">
        <div>
          <label>Address</label>
          <textarea name="address" placeholder="Street, Post, PS, District, PIN"></textarea>
        </div>
      </div>

      <div class="row two">
        <div>
          <label>Date of Birth</label>
          <input type="date" name="dob"/>
        </div>
        <div>
          <label>Nationality</label>
          <input name="nationality" placeholder="Indian"/>
        </div>
      </div>

      <div class="row two">
        <div>
          <label>Religion</label>
          <input name="religion" placeholder="Hinduism"/>
        </div>
        <div>
          <label>Marital Status</label>
          <select name="marital">
            <option value="">-- Select --</option>
            <option>Unmarried</option>
            <option>Married</option>
          </select>
        </div>
      </div>

      <div class="row two">
        <div>
          <label>Category</label>
          <input name="category" placeholder="General / SC / ST / OBC"/>
        </div>
        <div>
          <label>Languages (comma separated)</label>
          <input name="languages" placeholder="Bengali, Hindi & English"/>
        </div>
      </div>

      <div class="row two">
        <div>
          <label>Upload Profile Photo</label>
          <input type="file" id="profilePhoto" accept="image/*"/>
          <p class="hint">Square photo looks best (e.g., 600×600).</p>
        </div>
        <div>
          <label>Upload Signature Photo</label>
          <input type="file" id="signaturePhoto" accept="image/*"/>
        </div>
      </div>

      <hr style="border-color:#22304a; opacity:.4; margin:14px 0">

      <div class="row">
        <div>
          <label>Professional Summary</label>
          <textarea name="summary" placeholder="Responsible fresher with basic computer knowledge..."></textarea>
        </div>
      </div>

      <div class="row">
        <label>Educational Background</label>
        <table>
          <thead>
            <tr><th>Examination</th><th>Board / University</th><th>Year</th><th>% / Status</th></tr>
          </thead>
          <tbody>
            <tr>
              <td><input name="exam1" placeholder="Secondary (Class X)"/></td>
              <td><input name="board1" placeholder="W.B.B.S.E"/></td>
              <td><input name="year1" placeholder="2024"/></td>
              <td><input name="perc1" placeholder="Appeared / 75%"/></td>
            </tr>
            <tr>
              <td><input name="exam2" placeholder="Higher Secondary / Class XI (Commerce)"/></td>
              <td><input name="board2" placeholder="W.B.C.H.S.E"/></td>
              <td><input name="year2" placeholder="2025"/></td>
              <td><input name="perc2" placeholder="Appearing"/></td>
            </tr>
            <tr>
              <td><input name="exam3" placeholder="B.A (Hons) / Diploma (optional)"/></td>
              <td><input name="board3" placeholder="C.U / —"/></td>
              <td><input name="year3" placeholder="—"/></td>
              <td><input name="perc3" placeholder="—"/></td>
            </tr>
          </tbody>
        </table>
      </div>

      <div class="row">
        <div>
          <label>Computer Skills (you write)</label>
          <textarea name="computerSkills" placeholder="Tally Prime, MS Office, Internet, AI, Digital Marketing..."></textarea>
        </div>
      </div>

      <div class="row two">
        <div>
          <label>Other Skills</label>
          <textarea name="otherSkills" placeholder="Drawing, Taekwondo, Communication..."></textarea>
        </div>
        <div>
          <label>Work Experience</label>
          <textarea name="experience" placeholder="Fresher / any part-time or internship..."></textarea>
        </div>
      </div>

      <div class="row">
        <div>
          <label>Declaration</label>
          <textarea name="declaration">I hereby declare that all the information furnished above is true to the best of my knowledge.</textarea>
        </div>
      </div>

      <div class="row two">
        <div>
          <label>Place</label>
          <input name="place" value="Kolkata"/>
        </div>
        <div>
          <label>Date</label>
          <input type="date" name="date"/>
        </div>
      </div>

      <div class="btns">
        <button type="button" class="btn primary" onclick="generatePreview()">Preview CV</button>
        <button type="button" class="btn ghost" onclick="downloadPDF()">Save as PDF</button>
        <button type="reset" class="btn danger">Reset</button>
      </div>
    </form>

    <!-- ========== PREVIEW ========== -->
    <div class="preview">
      <div id="cvCard" class="cv" style="display:none;">
        <!-- Filled by JS -->
      </div>
    </div>

  </div>

  <script>
    let profileData = ""; let signData = "";

    // read photos
    document.getElementById("profilePhoto").addEventListener("change", function(){
      const f=this.files[0]; if(!f) return;
      const r=new FileReader(); r.onload=e=>profileData=e.target.result; r.readAsDataURL(f);
    });
    document.getElementById("signaturePhoto").addEventListener("change", function(){
      const f=this.files[0]; if(!f) return;
      const r=new FileReader(); r.onload=e=>signData=e.target.result; r.readAsDataURL(f);
    });

    function safe(v){ return (v??"").toString().trim(); }
    function initials(name){
      if(!name) return "AA";
      return name.split(/\s+/).slice(0,2).map(w=>w[0]?.toUpperCase()||"").join("") || "AA";
    }

    function generatePreview(){
      const form = document.getElementById('cvForm');
      const d = new FormData(form);

      const name   = safe(d.get('name'));
      const father = safe(d.get('father'));
      const phone  = safe(d.get('phone'));
      const email  = safe(d.get('email'));
      const address= safe(d.get('address'));
      const dob    = safe(d.get('dob'));
      const nationality = safe(d.get('nationality'));
      const religion    = safe(d.get('religion'));
      const marital     = safe(d.get('marital'));
      const category    = safe(d.get('category'));
      const languages   = safe(d.get('languages'));
      const summary     = safe(d.get('summary'));

      // education rows
      const rows = [
        {ex:d.get('exam1'), bd:d.get('board1'), yr:d.get('year1'), pr:d.get('perc1')},
        {ex:d.get('exam2'), bd:d.get('board2'), yr:d.get('year2'), pr:d.get('perc2')},
        {ex:d.get('exam3'), bd:d.get('board3'), yr:d.get('year3'), pr:d.get('perc3')}
      ].filter(r => safe(r.ex) || safe(r.bd) || safe(r.yr) || safe(r.pr));

      const comp   = safe(d.get('computerSkills'));
      const other  = safe(d.get('otherSkills'));
      const exp    = safe(d.get('experience'));
      const decl   = safe(d.get('declaration'));
      const place  = safe(d.get('place'));
      const date   = safe(d.get('date'));

      // build preview html
      let heroImg = profileData
        ? `<img class="photo" src="${profileData}" alt="profile">`
        : `<div class="avatar">${initials(name)}</div>`;

      let eduTable = rows.length ? `
        <div class="sec">
          <h3>Educational Background</h3>
          <table>
            <thead><tr><th>Examination</th><th>Board / University</th><th>Year</th><th>% / Status</th></tr></thead>
            <tbody>
              ${rows.map(r=>`<tr><td>${safe(r.ex)}</td><td>${safe(r.bd)}</td><td>${safe(r.yr)}</td><td>${safe(r.pr)}</td></tr>`).join("")}
            </tbody>
          </table>
        </div>
      ` : "";

      const cvHTML = `
        <div class="hero">
          ${heroImg}
          <div>
            <p class="nm">${name || "Your Name"}</p>
            <p class="tag">${summary || "Fresher — Seeking office/administrative or data-entry roles"}</p>
          </div>
        </div>

        <div class="grid-2">
          <div class="sec">
            <h3>Contact</h3>
            <div class="kv">
              <p><span class="muted">Phone</span><br><b>${phone}</b></p>
              <p><span class="muted">Email</span><br><b>${email}</b></p>
              <p><span class="muted">Address</span><br><b>${address}</b></p>
            </div>
          </div>

          <div class="sec">
            <h3>Personal</h3>
            <div class="kv">
              <p><b>Father's Name:</b> ${father}</p>
              <p><b>D.O.B:</b> ${dob}</p>
              <p><b>Nationality:</b> ${nationality}</p>
              <p><b>Religion:</b> ${religion}</p>
              <p><b>Marital Status:</b> ${marital}</p>
              <p><b>Category:</b> ${category}</p>
            </div>
          </div>
        </div>

        <div class="sec">
          <h3>Languages</h3>
          <p><b>${languages}</b></p>
        </div>

        ${eduTable}

        <div class="sec">
          <h3>Skills & Computer</h3>
          <p><b>Computer:</b> ${comp || "—"}</p>
          <p><b>Other skills:</b> ${other || "—"}</p>
        </div>

        <div class="sec">
          <h3>Work Experience</h3>
          <p><b>${exp || "Fresher — No formal work experience yet."}</b></p>
        </div>

        <div class="sec">
          <h3>Declaration</h3>
          <p class="muted">${decl}</p>
          <div class="grid-2" style="margin-top:8px; align-items:center">
            <p><b>Place:</b> ${place || "—"}<br><b>Date:</b> ${date || "—"}</p>
            <div style="text-align:right">
              ${signData ? `<img class="sign" src="${signData}" alt="signature">` : `<span class="muted">Signature</span>`}
              <div style="border-top:1px solid #334155; margin-top:6px"> </div>
            </div>
          </div>
        </div>
      `;

      const card = document.getElementById('cvCard');
      card.style.display = 'block';
      card.innerHTML = cvHTML;
      // scroll to preview on small screens
      card.scrollIntoView({behavior:'smooth', block:'start'});
    }

    async function downloadPDF(){
      const card = document.getElementById('cvCard');
      if(card.style.display==='none'){ alert('Please generate Preview first.'); return; }
      const canvas = await html2canvas(card, {scale:2, backgroundColor:null});
      const imgData = canvas.toDataURL('image/png');
      const { jsPDF } = window.jspdf;
      const pdf = new jsPDF('p','mm','a4');

      // scale to fit width
      const pageWidth = pdf.internal.pageSize.getWidth();
      const pageHeight = pdf.internal.pageSize.getHeight();
      const imgWidth = pageWidth - 20; // margins
      const imgHeight = canvas.height * imgWidth / canvas.width;

      let y = 10;
      if(imgHeight <= pageHeight - 20){
        pdf.addImage(imgData, 'PNG', 10, y, imgWidth, imgHeight);
      } else {
        // multi-page if content long
        let h = imgHeight; let sY = 0;
        const pxPerMM = canvas.height / imgHeight;
        while(h > 0){
          const sliceHeightMM = pageHeight - 20;
          const sliceHeightPX = sliceHeightMM * pxPerMM;
          const sliceCanvas = document.createElement('canvas');
          sliceCanvas.width = canvas.width;
          sliceCanvas.height = sliceHeightPX;
          const ctx = sliceCanvas.getContext('2d');
          ctx.drawImage(canvas, 0, sY, canvas.width, sliceHeightPX, 0, 0, canvas.width, sliceHeightPX);
          const sliceData = sliceCanvas.toDataURL('image/png');
          pdf.addImage(sliceData, 'PNG', 10, 10, imgWidth, sliceHeightMM);
          h -= sliceHeightMM;
          sY += sliceHeightPX;
          if(h > 0) pdf.addPage();
        }
      }
      pdf.save('My_CV.pdf');
    }
  </script>
</body>
</html>
