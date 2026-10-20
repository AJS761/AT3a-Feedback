<!doctype html>
<html lang="en-AU">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>EDUC2151 AT3 Part A Feedback Builder</title>
<!-- =====================================================================
     SETTINGS: change the values below to customise the tool.
     Keep the quote marks and commas. Colours are in the :root block of the style section below.
     ===================================================================== -->
<script>
window.AT3_SETTINGS = {

  /* Colours are now in the :root block in the <style> section below,
     where the editor shows a colour square beside each hex code. */

  /* ---- Fonts (any family from fonts.google.com) ---- */
  fonts: {
    headings: "Tahoma",
    body:     "Tahoma",
    labels:   "Tahoma"    // small capitals labels and marks
  },
  textSize: 15,                  // main text size in pixels

  /* ---- Page text ---- */
  showHeader: true,              // false hides the title block (e.g. if your Wix page has its own)
  title:      "EDUC2151 AT3 Part A Tutor Feedback Builder",
  intro:      "Choose a band and mark for each criterion and tick what applies. The comment builds from the set wording, so copy it into Canvas and start the next student.",

  /* ---- Words used inside the comments ---- */
  stage: "Stage 4",              // "...to the History Stage 4 Syllabus"
  lms:   "Canvas",               // where students submit and where comments go

  /* ---- Dropdown and tick-box options ---- */
  klaList:    ["Aboriginal Studies", "Chinese", "Communication Technology", "Design Innovation Technology", "Drama", "Engineering Technology", "English", "Food Technology", "French", "Geography", "History", "Industrial Technology", "Japanese", "Mathematics", "PDHPE", "Science"],
  suitability:  ["strong", "great", "appropriate", "okay", "not appropriate"],
  callItA:      ["tool", "app", "platform", "technology"],
  forThisChosen:["content", "outcome", "lesson", "topic"],
  signOffs:     ["Kind regards", "Best wishes", "Cheers"],
  failReasons:  ["the resource not being student-facing", "the resource being designed for the wrong stage", "the missing overview", "there being no clear reason for the resource to be digital"],

  // "Where they could improve" options. The first part says which criterion
  // it relates to (c1, c2 or c3) so the tool can mark it as suggested.
  improvements: [
    ["c1", "structuring the resource so the same approach could be applied to other syllabus content"],
    ["c1", "an overview that clearly names the topic, outcome and content point, with syllabus elements that align"],
    ["c2", "the technology reshaping what learners do, rather than replicating a paper-based task"],
    ["c2", "digital features that add a clear learning benefit beyond convenience"],
    ["c3", "more consistent use of multimedia and cognitive-load principles"],
    ["c3", "content and language pitched more closely to the age and stage of your learners"]
  ],

  // "Overall resource" is filled in from the total mark using these cut-offs (out of 30)
  overallCutoffs: { wellThoughtOut: 25, appropriate: 18, adequate: 12 }
};
/* The comment wording itself is further down, in c1Text, c2Text, c3Text and OV. */
</script>
<!-- ===================== END OF SETTINGS ===================== -->
<style>
/* COLOURS: click a square beside a hex code to open the colour picker. */
:root{
  --bg:#e8ffe3;            /* page background */
  --panel:#ffffff;         /* panels and input boxes */
  --ink:#000000;           /* all text on light backgrounds */
  --line:#2f7d52;          /* outlines (drawn faint automatically) */
  --accent:#2f7d52;        /* buttons, ticked options, selected marks */
  --accent-hover:#256843;  /* buttons when the mouse is over them */
  --sel:#1b5a38;           /* the chosen band in each criterion */
  --banner:#1b5a38;        /* title band and comment panel heading */
  --banner-ink:#ffffff;    /* all text on dark green backgrounds */
  --gap:#c9eccf;           /* "gap to fill" highlights in the comment */
  --gap-ink:#000000;
  --head:#000000; --muted:#000000;
  --line-soft:color-mix(in srgb, var(--line) 28%, white);
  --tint:color-mix(in srgb, var(--accent) 7%, white);
  --display:Tahoma,sans-serif; --body:Tahoma,sans-serif; --mono:Tahoma,sans-serif;
}
*{box-sizing:border-box}
[hidden]{display:none!important}
body{margin:0;background:var(--bg);color:var(--ink);font-family:var(--body);font-size:var(--size,15px);line-height:1.5}
.wrap{max-width:1240px;margin:0 auto;padding-block:20px 48px;padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px))}

/* Title band */
header{background:var(--banner);color:var(--banner-ink);border-radius:12px;padding:22px 24px 24px;margin-bottom:20px;border-bottom:6px solid var(--accent)}
h1{font-family:var(--display);font-weight:600;font-size:1.9rem;line-height:1.15;margin:4px 0 0;text-wrap:balance;color:var(--banner-ink)}
.sub{margin:6px 0 0;max-width:none;color:var(--banner-ink)}
.eyebrow{font-family:var(--mono);font-size:.72rem;letter-spacing:.02em;color:var(--banner-ink)}

.grid{display:grid;grid-template-columns:minmax(0,1fr) minmax(0,440px);gap:24px;align-items:start}
@media (max-width:900px){.grid{grid-template-columns:minmax(0,1fr)}}
.form{display:flex;flex-direction:column;gap:16px;min-width:0}

/* Cards */
section.card{background:var(--panel);border:1px solid var(--line-soft);border-top:4px solid var(--head);border-radius:10px;padding:18px 18px 20px;display:flex;flex-direction:column;gap:14px;min-width:0}
section.crit{border-top-color:var(--accent)}
.card h2{font-family:var(--display);font-weight:600;font-size:1.15rem;margin:0;display:flex;gap:10px;align-items:baseline;flex-wrap:wrap;color:var(--ink)}
.card h2 .tag{font-family:var(--mono);font-size:.7rem;letter-spacing:.02em;color:var(--ink);font-weight:500}
.card h2 .score{margin-left:auto;font-family:var(--mono);font-size:.85rem;font-variant-numeric:tabular-nums;color:var(--banner-ink);background:var(--accent);border-radius:6px;padding:2px 8px}
.card h2 .score:empty{display:none}

/* Fields */
.fields{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:12px 14px}
label.f{display:flex;flex-direction:column;gap:5px;font-size:.82rem;font-weight:600;color:var(--ink);min-width:0}
input[type=text],select{font:inherit;font-size:.95rem;color:var(--ink);background:var(--panel);border:1px solid var(--line-soft);border-radius:7px;padding:8px 10px;width:100%}
small.hint{font-weight:400;font-size:.74rem;color:var(--ink)}
input[list]{padding-right:34px;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1.5l5 5 5-5' fill='none' stroke='%231b5a38' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right 12px center;cursor:pointer}
input[list]::-webkit-calendar-picker-indicator{opacity:0;position:absolute;right:0;top:0;width:34px;height:100%;cursor:pointer}
input[list]{position:relative}
input[type=text]::placeholder{color:var(--ink);opacity:1;font-style:italic;font-weight:300}
input[type=text]:focus,select:focus{outline:2px solid var(--accent);outline-offset:1px;border-color:transparent}

/* Band buttons */
.bands{display:grid;grid-template-columns:repeat(5,minmax(0,1fr));gap:6px}
@media (max-width:560px){.bands{grid-template-columns:repeat(2,minmax(0,1fr))}}
.bands input,.marks input,.chips input{position:absolute;opacity:0;pointer-events:none}
.bands label{display:flex;flex-direction:column;gap:2px;border:1px solid var(--line-soft);border-radius:8px;padding:8px 8px 9px;cursor:pointer;background:var(--panel);min-width:0}
.bands label:hover{border-color:var(--accent);background:var(--tint)}
.bands label b{font-family:var(--mono);font-size:.9rem;font-variant-numeric:tabular-nums;color:var(--ink)}
.bands label span{font-size:.76rem;color:var(--ink);line-height:1.25}
.bands input:checked + label{border-color:var(--sel);background:var(--sel)}
.bands input:checked + label b,.bands input:checked + label span{color:var(--banner-ink)!important}
.bands input:focus-visible + label,.marks input:focus-visible + label,.chips input:focus-visible + label{outline:2px solid var(--ink);outline-offset:2px}

/* Marks */
.markrow{display:flex;flex-wrap:wrap;align-items:center;gap:8px 12px}
.markrow .q{font-size:.82rem;font-weight:600;color:var(--ink)}
.marks{display:flex;gap:6px}
.marks label{font-family:var(--mono);font-variant-numeric:tabular-nums;min-width:2.4em;text-align:center;border:1px solid var(--line-soft);border-radius:7px;padding:5px 8px;cursor:pointer;background:var(--panel);color:var(--ink)}
.marks label:hover{border-color:var(--accent)}
.marks input:checked + label{background:var(--accent);border-color:var(--accent);color:var(--banner-ink)}
.guide{font-size:.8rem;color:var(--ink);flex:1 1 240px;min-width:0}
.desc{font-size:.85rem;color:var(--ink);margin:0;max-width:75ch}

/* Follow-up options */
.extra{display:flex;flex-direction:column;gap:8px;border-left:3px solid var(--accent);padding-left:12px}
.extra .q{font-size:.82rem;font-weight:600;color:var(--ink)}
.chips{display:flex;flex-wrap:wrap;gap:6px}
.chips label{font-size:.85rem;border:1px solid var(--line-soft);border-radius:999px;padding:4px 11px;cursor:pointer;background:var(--panel);color:var(--ink)}
.chips label:hover{border-color:var(--accent);background:var(--tint)}
.chips input:checked + label{background:var(--accent);border-color:var(--accent);color:var(--banner-ink)}
.chips label.sugg{border-color:var(--accent);border-style:dashed}
.chips label.sugg::after{content:" · suggested";font-size:.72rem;color:var(--ink)}
.chips input:checked + label.sugg::after{color:var(--banner-ink)}
.check{display:flex;gap:8px;align-items:flex-start;font-size:.9rem;cursor:pointer}
.check input{margin-top:3px;accent-color:var(--accent)}
.top-row{display:grid;grid-template-columns:minmax(0,1fr) minmax(0,240px);gap:16px;align-items:stretch}
.fields.cols3{grid-template-columns:repeat(3,minmax(0,1fr));grid-auto-rows:1fr;align-items:stretch}
.fields.cols3 label.f{justify-content:flex-end}
.fields.cols3 input,.fields.cols3 select{height:40px}
.access .extra{margin-top:auto}
@media (max-width:1200px){.fields.cols3{grid-template-columns:repeat(2,minmax(0,1fr))}}
@media (max-width:1000px){.top-row{grid-template-columns:minmax(0,1fr)}}
@media (max-width:600px){.fields.cols3{grid-template-columns:minmax(0,1fr)}}
.access{border-top-color:var(--ink)}
.access.on{border-color:var(--ink);box-shadow:inset 0 0 0 1px var(--ink)}

/* Comment panel */
.out{position:sticky;top:calc(env(safe-area-inset-top,0px) + 16px);background:var(--panel);border:1px solid var(--line-soft);border-radius:10px;display:flex;flex-direction:column;min-width:0;max-height:calc(100vh - 32px);overflow:hidden}
@media (max-width:900px){.out{position:static;max-height:none}}
.out-head{display:flex;align-items:center;gap:10px;padding:14px 16px;background:var(--banner);color:var(--banner-ink);flex-wrap:wrap}
.out-head strong{font-family:var(--display);font-weight:600;font-size:1.05rem}
.total{font-family:var(--mono);font-variant-numeric:tabular-nums;font-size:.95rem;margin-left:auto}
.status{font-size:.8rem;font-weight:600;border-radius:999px;padding:3px 10px;background:var(--accent);color:var(--banner-ink)}
.status.warn{background:var(--gap);color:var(--gap-ink);box-shadow:0 0 0 1px var(--banner-ink)}
.comment{padding:16px 18px;overflow:auto;font-size:.95rem;line-height:1.6;min-height:200px}
.comment p{margin:0 0 .8em}
.comment .h{display:block;font-weight:700;color:var(--ink)}
.comment .gap{background:var(--gap);color:var(--gap-ink);border-radius:4px;padding:0 5px;font-weight:600}
.autotext-key,.comment .autotext{background:#dcdcdc;color:#000;border-radius:4px;padding:0 4px;font-weight:600}
.out-foot{display:flex;flex-wrap:wrap;gap:8px 12px;align-items:center;padding:12px 16px;border-top:1px solid var(--line-soft);background:var(--tint)}
.opts{display:flex;flex-wrap:wrap;gap:4px 14px;width:100%}
.opts label{display:flex;gap:6px;align-items:center;font-size:.82rem;color:var(--ink);cursor:pointer}
.opts input{accent-color:var(--accent)}
button{font:inherit;font-size:.9rem;font-weight:600;border-radius:7px;padding:8px 14px;cursor:pointer;border:1px solid var(--accent);background:var(--panel);color:var(--ink)}
button:hover{background:var(--tint)}
button.primary{background:var(--accent);color:var(--banner-ink)}
button.primary:hover{background:var(--accent-hover);border-color:var(--accent-hover)}
button:focus-visible{outline:2px solid var(--ink);outline-offset:2px}
.note{font-size:.8rem;color:var(--ink);padding:8px 16px 12px;background:var(--tint);margin:0}
@media (prefers-reduced-motion:no-preference){.bands label,.chips label,.marks label,button{transition:background .12s,border-color .12s}}
</style>
</head>
<body>
<div class="wrap">
  <header id="pageHeader">
    <div class="eyebrow" id="hEyebrow"></div>
    <h1 id="hTitle"></h1>
    <p class="sub" id="hIntro"></p>
  </header>

  <div class="grid">
    <form class="form" id="f" autocomplete="off">

      <div class="top-row">
      <section class="card">
        <h2>Student and resource overview</h2>
        <div class="fields cols3">
          <label class="f">Student first name <small class="hint">(type in the box)</small><input type="text" id="name" placeholder="e.g. Abbie"></label>
          <label class="f">KLA <small class="hint">(choose from the list)</small><input type="text" id="kla" list="klas" placeholder="e.g. History"></label>
          <label class="f">Technology used <small class="hint">(type in the box)</small><input type="text" id="tech" placeholder="e.g. Genially"></label>
          <label class="f">How suitable it is <small class="hint">(choose from the list)</small>
            <select id="rating"></select></label>
          <label class="f">Call it a <small class="hint">(choose from the list)</small>
            <select id="tooltype"></select></label>
          <label class="f">For this chosen <small class="hint">(choose from the list)</small>
            <select id="lesson"></select></label>
        </div>
        <datalist id="klas"></datalist>
      </section>

      <section class="card access" id="accessCard">
        <h2>Access</h2>
        <label class="check"><input type="checkbox" id="noaccess"> <span><b>The resource couldn't be accessed or opened</b><br><span class="desc">Places every criterion in the Pre-structural band at 0 and writes a short comment instead.</span></span></label>
        <div class="extra" data-show="noaccess"><span class="q">Reason <small class="hint">(choose from the list)</small></span>
          <select id="accessReason">
            <option value="the link or file was broken">Broken link or file</option>
            <option value="the marker was required to create an account, sign up or log in to view it">Needed an account, sign-up or login</option>
            <option value="it was not submitted in a form the marker could open">Not submitted in a form the marker can open</option>
            <option value="elements of the resource were unreadable or there was no workable pathway through it">Unreadable or no workable pathway</option>
          </select></div>
      </section>
      </div>

      <div id="criteria" style="display:flex;flex-direction:column;gap:16px"></div>

      <section class="card">
        <h2>Overall comment</h2>
        <div class="bands" id="ov" style="grid-template-columns:repeat(auto-fit,minmax(120px,1fr))"></div>
        <div class="extra" data-show="ov:middle ov:low"><span class="q">Where they could improve (pick any; dashed ones match the lowest criterion)</span>
          <div class="chips" data-group="improve"></div>
          <input type="text" id="improveOther" placeholder="Anything else, in your own words (optional)"></div>
        <div class="extra" data-show="ov:fail"><span class="q">Reason it didn't meet the standards <small class="hint">(choose from the list)</small></span>
          <input type="text" id="failReason" list="failReasons" placeholder="e.g. the resource being designed for the wrong stage">
          <datalist id="failReasons"></datalist></div>
      </section>

      <section class="card">
        <h2>Sign-off</h2>
        <div class="fields">
          <label class="f">Your name <small class="hint">(type in the box)</small><input type="text" id="tutor" placeholder="e.g. Abbie Smith"></label>
          <label class="f">Sign-off <small class="hint">(choose from the list)</small>
            <select id="signoff"></select></label>
        </div>
        <p class="desc">Your name and sign-off are kept when you start the next student, and remembered on this device.</p>
      </section>
    </form>

    <aside class="out" aria-live="polite">
      <div class="out-head">
        <strong>Comment</strong>
        <span class="status" id="status">Ready</span>
        <span class="total" id="total">–/30</span>
      </div>
      <div class="comment" id="comment" contenteditable="true" spellcheck="true" aria-label="Comment (editable)"></div>
      <div class="out-foot">
        <button type="button" class="primary" id="copy">Copy comment</button>
        <button type="button" id="next">New student</button>
        <div class="opts">
          <label><input type="checkbox" id="headings"> Criterion headings and marks</label>
          <label><input type="checkbox" id="samr" checked> Refer to SAMR</label>
          <label><input type="checkbox" id="onepara"> One paragraph</label>
        </div>
      </div>
      <div class="note" id="copyNote">Green highlighted words are gaps still to fill.</div>
      <div class="note"><span class="autotext-key">Grey highlighted words</span> in the first paragraph (the overall resource and syllabus alignment descriptions) are generated automatically from the bands and marks you choose. Tutors: if you want different wording, click in the comment and edit it directly. Make any manual edits last, because changing a selection on the left rebuilds the comment.</div>
    </aside>
  </div>
</div>

<script>
/* ---------- Apply settings ---------- */
const S = window.AT3_SETTINGS || {};
(function applySettings(){
  const f = S.fonts || {};
  const root = document.documentElement.style;
  /* All fonts are fixed to Tahoma (set in :root); settings.fonts is ignored. */
  if (S.textSize) root.setProperty("--size", S.textSize + "px");
  const h = (id, t) => { const el = document.getElementById(id); if (el) el.textContent = t || ""; };
  h("hEyebrow", S.smallLabel); h("hTitle", S.title); h("hIntro", S.intro);
  if (S.title) document.title = S.title;
  document.getElementById("pageHeader").hidden = S.showHeader === false;
  const opts = (id, list, blank) => { document.getElementById(id).innerHTML = (blank ? `<option value="">${blank}</option>` : "") + (list||[]).map(o => `<option>${String(o).replace(/</g,"&lt;")}</option>`).join(""); };
  opts("rating", S.suitability || ["strong","great","appropriate","okay","not appropriate"]);
  opts("tooltype", S.callItA || ["tool","app","platform","technology"]);
  opts("lesson", S.forThisChosen || ["activity","lesson"]);
  opts("signoff", S.signOffs || ["Kind regards"]);
  document.getElementById("signoff").insertAdjacentHTML("beforeend", `<option value="">Name only</option>`);
  opts("klas", S.klaList || []);
  opts("failReasons", S.failReasons || []);
})();
const STAGE = S.stage || "Stage 4", LMS = S.lms || "Canvas";
const CUT = Object.assign({wellThoughtOut:25, appropriate:18, adequate:12}, S.overallCutoffs || {});

/* ---------- Rubric ---------- */
const SOLO = {"10":"Extended Abstract","9-8":"Relational","7-6":"Multi-structural","5-3":"Uni-structural","2-0":"Pre-structural"};
const RANGE = {"10":[10],"9-8":[9,8],"7-6":[7,6],"5-3":[5,4,3],"2-0":[2,1,0]};
const BAND_ORDER = ["10","9-8","7-6","5-3","2-0"];

const CRIT = [
 { id:"c1", title:"Discipline-specific application of digital design principles", tag:"Criterion 1",
   short:{"10":"Transferable, expert design application","9-8":"Discipline-driven design coherence","7-6":"Multiple aligned design applications","5-3":"Some discipline-specific design application","2-0":"Missing or mismatched design/discipline focus"},
   guide:{"5-3":"Top of range: overview present and broadly accurate. Bottom: incomplete, imprecise, or syllabus elements sit awkwardly together."},
   extras:{
     "10":[{type:"text",id:"c1ex",q:"Example from their resource",ph:"e.g. the timeline that reveals sources as students sequence events"}],
     "7-6":[{type:"chips",g:"c1principles",q:"Principles applied (pick any)",opts:["modelling","prompts","scaffolds","interactivity"]}],
     "5-3":[{type:"chips",g:"c1issues",q:"What wasn't clear? (pick any)",opts:["the connection to the discipline content is not clearly evident in the resource itself","the overview does not clearly name the topic, outcome and content point","the named syllabus elements do not align with one another"],labels:["Discipline connection not evident","Overview doesn't name topic/outcome/content point","Syllabus elements don't align"]}],
     "2-0":[{type:"chips",g:"c1missing",q:"Why it sits here (pick any)",
        opts:["omits any clear application of digital design principles","omits a clear discipline content focus","sets tasks where the intended design rationale cannot be inferred from what a learner is asked to do","is missing an overview",`targets the wrong stage (not ${STAGE})`,"has an overview that does not name the topic, outcome or content point","names syllabus elements that do not belong together, so the stated alignment is invalid"],
        labels:["No clear design principles","No discipline content focus","Design rationale can't be inferred","Overview missing","Wrong stage","Overview missing topic/outcome/content point","Syllabus elements don't belong together"]}]
   }},
 { id:"c2", title:"Purposeful technology integration", tag:"Criterion 2",
   short:{"10":"Transformative digital learning design","9-8":"Redefined learner action through technology","7-6":"Functional digital enhancements","5-3":"Some digital value","2-0":"Unwarranted or obstructive technology use"},
   guide:{"5-3":"Top of range: reliably delivers the activity and supports completion. Bottom: adds little beyond moving a paper-equivalent task online."},
   extras:{
     "10":[{type:"chips",g:"c2affordances",q:"Opportunities it creates (pick any)",opts:["an authentic audience","iterative feedback and revision","collaboration","real or live data","variable manipulation"]}],
     "7-6":[{type:"chips",g:"c2features",q:"Features it adds (pick any)",opts:["immediate feedback","interactivity","self-pacing","audio-visual supports","accessibility functions"]}],
     "2-0":[{type:"select",id:"c2bad",q:"The technology…",opts:[["is incidental to the learning","is incidental to the learning"],["undermines the task","undermines the task"]]}]
   }},
 { id:"c3", title:"Design for learning", tag:"Criterion 3",
   short:{"10":"Calibrated learning design for specific learners","9-8":"Coherent, accessible design for novices","7-6":"Multiple design supports applied","5-3":"Usable to varying degrees","2-0":"Inaccessible or unworkable resource"},
   guide:{"5-3":"Top of range: readable, navigable, reasonably well pitched, with at least one deliberate design choice. Bottom: recurring obstacles or mismatched pitch make learning noticeably harder."},
   extras:{
     "9-8":[{type:"chips",g:"c3principles",q:"Principles applied (pick any)",opts:["clear signalling","integrated text and visuals","sensible segmentation","an uncluttered layout"]}],
     "7-6":[{type:"chips",g:"c3strategies",q:"Strategies used (pick any)",opts:["chunking","headings","visuals paired with text","prompts","modelling","accessibility features"]},
            {type:"check",id:"c3slip",q:"The pitch slips in places"}],
     "5-3":[{type:"chips",g:"c3obstacles",q:"Obstacles (pick any)",opts:["unclear sequencing","heavy or poorly pitched text","a distracting layout","gaps in accessibility"]},
            {type:"select",id:"c3pitch",q:"Content and language for the age and stage",opts:[["well","Well pitched"],["not","Not well pitched"]]}],
     "2-0":[{type:"chips",g:"c3fail",q:"Why it's unworkable (pick any)",opts:["mismatch","overload"],labels:["Language or stage badly mismatched","Cognitive overload"]},
            {type:"select",id:"c3mismatch",q:"If mismatched, the content is…",opts:[["far too simple","far too simple"],["far too advanced","far too advanced"],["tonally inappropriate","tonally inappropriate"]]}]
   }}
];

const IMPROVE = S.improvements || [];

/* ---------- Build the form ---------- */
const $ = id => document.getElementById(id);
const esc = s => String(s).replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;").replace(/"/g,"&quot;");
function chipsHtml(g, opts, labels){
  return opts.map((v,i)=>`<input type="checkbox" id="${g}-${i}" name="${g}" value="${esc(v)}"><label for="${g}-${i}">${esc(labels?labels[i]:v)}</label>`).join("");
}
$("criteria").innerHTML = CRIT.map(c => {
  const bands = BAND_ORDER.map(b => `<input type="radio" name="${c.id}" id="${c.id}-${b}" value="${b}"><label for="${c.id}-${b}"><b>${b}</b><span>${SOLO[b]}</span></label>`).join("");
  const marks = BAND_ORDER.map(b => `<div class="markrow" data-show="${c.id}:${b}"><span class="q">Mark</span><div class="marks">${
      RANGE[b].map(m=>`<input type="radio" name="${c.id}m" id="${c.id}m-${m}" value="${m}"><label for="${c.id}m-${m}">${m}</label>`).join("")
    }</div>${c.guide[b]?`<span class="guide">${esc(c.guide[b])}</span>`:""}</div>`).join("");
  const extras = Object.entries(c.extras).map(([b,list]) => list.map(x => {
    let inner = "";
    if (x.type==="text") inner = `<input type="text" id="${x.id}" placeholder="${esc(x.ph||"")}">`;
    if (x.type==="chips") inner = `<div class="chips" data-group="${x.g}">${chipsHtml(x.g,x.opts,x.labels)}</div>`;
    if (x.type==="select") inner = `<select id="${x.id}">${x.opts.map(([v,l])=>`<option value="${esc(v)}">${esc(l)}</option>`).join("")}</select>`;
    if (x.type==="check") return `<div class="extra" data-show="${c.id}:${b}"><label class="check"><input type="checkbox" id="${x.id}"> ${esc(x.q)}</label></div>`;
    const hint = x.type==="select" ? ` <small class="hint">(choose from the list)</small>` : "";
    return `<div class="extra" data-show="${c.id}:${b}"><span class="q">${esc(x.q)}${hint}</span>${inner}</div>`;
  }).join("")).join("");
  return `<section class="card crit" data-crit="${c.id}">
    <h2>${esc(c.title)}<span class="score" id="${c.id}-score"></span></h2>
    <div class="bands">${bands}</div>
    <p class="desc" id="${c.id}-desc"></p>
    ${marks}${extras}</section>`;
}).join("");

$("ov").innerHTML = [["top","Top"],["middle","Middle"],["low","Low"],["fail","Didn't meet standards"]].map(([v,t]) =>
  `<input type="radio" name="ov" id="ov-${v}" value="${v}"><label for="ov-${v}"><span style="font-size:.88rem;color:inherit;font-weight:600">${t}</span></label>`).join("");
document.querySelector('[data-group="improve"]').innerHTML = chipsHtml("improve", IMPROVE.map(x=>x[1]));

/* ---------- Helpers ---------- */
const val = id => ($(id).value || "").trim();
const band = k => (document.querySelector(`input[name="${k}"]:checked`)||{}).value || "";
const mark = k => { const v = (document.querySelector(`input[name="${k}m"]:checked`)||{}).value; return v===undefined ? null : +v; };
const picks = g => [...document.querySelectorAll(`input[name="${g}"]:checked`)].map(i => i.value);
const list = a => a.length < 2 ? (a[0]||"") : a.slice(0,-1).join(", ") + " and " + a[a.length-1];
const an = w => /^[aeiou]/i.test(w) ? "an" : "a";
const GAP = s => `\u0000${s}\u0001`;
const or = (v, label) => v ? v : GAP(label);
const pos = (b, m) => { const r = RANGE[b]; if (m===null) return "mid"; return m===r[0] ? "top" : m===r[r.length-1] ? "bottom" : "mid"; };

/* ---------- Wording ---------- */
function c1Text(b, m, kla){
  if (b==="10") return `Your resource shows a transferable, expert design application. It applies the digital design principles precisely at the points where they add the most value to the discipline content, such as ${or(val("c1ex"),"example from their resource")}, and this is evident in the finished resource itself. It also structures the resource so the same approach could be applied to other syllabus content in ${kla}.`;
  if (b==="9-8") return `Your resource shows discipline-driven design coherence. It integrates the chosen digital design principles within the learning activity so they visibly shape what learners do, and the resource expands curriculum learning opportunities within the syllabus content. To move into the Extended Abstract band, structure the resource so the same approach could be applied to other syllabus content in ${kla}.`;
  if (b==="7-6") return `Your resource shows multiple aligned design applications. It applies several digital design principles, such as ${or(list(picks("c1principles")),"principles")}, that connect to the discipline content and help to expand curriculum learning opportunities, although these connections are not consistently sustained across the whole resource. To move into the Relational band, make sure the principles visibly shape what learners do throughout the whole activity.`;
  if (b==="5-3") {
    const iss = or(list(picks("c1issues")),"what wasn't clear");
    const p = pos(b,m);
    const lead = p==="top" ? `Your resource shows some discipline-specific design application. It applies a digital design principle that is relevant to the chosen syllabus content, and the overview is present and broadly accurate; however, ${iss}.`
      : p==="bottom" ? `Your resource shows some discipline-specific design application, but the application of a digital design principle is only implied or hard to identify, and ${iss}.`
      : `Your resource shows some discipline-specific design application. It applies a digital design principle that is relevant to the chosen syllabus content, although the application is limited and ${iss}.`;
    return lead + ` To move into the Multi-structural band, apply several digital design principles that clearly connect to the discipline content, and check that your overview names the topic, outcome and content point and that these align.`;
  }
  if (b==="2-0") return `Your resource has a missing or mismatched design/discipline focus. It ${or(list(picks("c1missing")),"why it sits here")}. It is important to read the instructions and the rubric carefully so that your resource is clearly aligned to the syllabus, and to support your learning and synthesis within the course.`;
}
function c2Text(b, m, tech){
  const samr = $("samr").checked;
  if (b==="10") return `Your resource demonstrates a transformative digital learning design. It engineers a digitally enabled learning experience that creates opportunities not otherwise available, through ${or(list(picks("c2affordances")),"opportunities")}, and your design choices make the technology visibly serve the targeted digital design principle rather than sit beside it.`;
  if (b==="9-8") return `Your resource redefines learner action through technology. It reshapes what learners do through digital affordances, so the core task would not be feasible in the same form on paper, and ${tech} clearly fits the content, learners and classroom constraints. To move into the Extended Abstract band, think about how the technology could create learning opportunities that would not otherwise be available, such as an authentic audience, iterative feedback and revision, collaboration, or real or live data.`;
  if (b==="7-6") return `Your resource adds functional digital enhancements, such as ${or(list(picks("c2features")),"features")}, that improve learning and usability. However, the underlying learner task remains broadly similar to a paper-based version${samr?", which places it at the augmentation level of the SAMR model":""}. To move into the Relational band, think about how the technology could reshape what learners actually do, so the core task would not be feasible in the same form on paper${samr?" (the modification or redefinition levels)":""}.`;
  if (b==="5-3") {
    const p = pos(b,m);
    const lead = p==="top" ? `Your resource provides a digital version of the resource that reliably delivers the activity and supports completion. However, the technology does not yet offer a clear learning benefit beyond convenience, and the underlying learner task remains broadly similar to a paper-based version.`
      : p==="bottom" ? `Your resource largely moves a paper-equivalent task online. The technology adds little beyond convenience, and the underlying learner task remains broadly similar to a paper-based version.`
      : `Your resource provides a digital version of the resource, but the technology offers little clear learning benefit beyond convenience, and the underlying learner task remains broadly similar to a paper-based version.`;
    return lead + (samr?` In SAMR terms, it currently sits at the substitution or lower augmentation level.`:"") + ` To move into the Multi-structural band, add purposeful features such as immediate feedback, interactivity or self-pacing that improve learning, not just access.`;
  }
  if (b==="2-0") return `Your resource uses technology in a way that ${val("c2bad")}, so there is no clear reason for the resource to be digital based on what the learner is asked to do. I would encourage you to read the instructions and the rubric carefully to make sure the technology you choose is meaningful to the learning.`;
}
function c3Text(b, m){
  if (b==="10") return `Your resource is a calibrated learning design for specific learners. It optimises cognitive load and accessibility through deliberate trade-offs, including what is left out, so it would hold up in a real classroom for the intended learners and devices. The design, content and language are precisely pitched to the age and stage of your target audience. Well done.`;
  if (b==="9-8") return `Your resource has a coherent, accessible design for novices. It applies multimedia and cognitive-load principles consistently, such as ${or(list(picks("c3principles")),"principles")}, so learners can navigate independently and focus on the intended learning. The content and language are consistently age and stage appropriate. To move into the Extended Abstract band, make more deliberate trade-offs (including what you leave out) so every element is precisely pitched to your intended learners.`;
  if (b==="7-6") return `Your resource applies several learning-focused design strategies, such as ${or(list(picks("c3strategies")),"strategies")}, that generally support understanding, although their application is uneven across the resource. The design, content and language are generally age and stage appropriate${$("c3slip").checked?", even if the pitch slips in places":""}. To move into the Relational band, apply multimedia and cognitive-load principles more consistently so learners can navigate independently.`;
  if (b==="5-3") {
    const ob = or(list(picks("c3obstacles")),"obstacles");
    const p = pos(b,m);
    const lead = p==="top" ? `Your resource is usable to varying degrees. It opens and functions, and it is readable and reasonably navigable with at least one deliberate design choice that aids understanding; however, there are some design obstacles, such as ${ob}.`
      : p==="bottom" ? `Your resource opens and functions, but recurring design obstacles, such as ${ob}, make it noticeably harder for learners to follow independently.`
      : `Your resource is usable to varying degrees. It opens and functions, but some design obstacles, such as ${ob}, make the pathway harder for learners to follow independently.`;
    const pitch = val("c3pitch")==="well" ? ` The content and language are well pitched to the age and stage of your target audience.` : ` The content and language are not yet well pitched to the age and stage of your target audience.`;
    return lead + pitch + ` To move into the Multi-structural band, use strategies such as chunking, headings, visuals paired with text and clear prompts to remove these obstacles.`;
  }
  if (b==="2-0") {
    const f = picks("c3fail");
    const s = [];
    if (f.includes("mismatch")) s.push(`The content and language are ${val("c3mismatch")} for the age and stage of the target audience, so it would not be usable with those learners.`);
    if (f.includes("overload")) s.push(`It imposes a cognitive load that prevents learners from engaging with the content.`);
    return `Your resource is unworkable for the intended learners. ` + (s.length ? s.join(" ") : GAP("why it's unworkable"));
  }
}

/* ---------- Auto-fill opening from marks ---------- */
function autoOpening(total, c1b){
  const aMap = {"10":"aligned","9-8":"aligned","7-6":"mostly aligned","5-3":"somewhat aligned","2-0":"not aligned"};
  return {
    align: c1b ? aMap[c1b] : "",
    quality: total===null ? "" : total>=CUT.wellThoughtOut ? "well thought out" : total>=CUT.appropriate ? "appropriate" : total>=CUT.adequate ? "adequate" : "inadequate"
  };
}
const AUTO = s => `\u0002${s}\u0003`;

/* ---------- Compose ---------- */
function compose(){
  const noaccess = $("noaccess").checked;
  const name = or(val("name"),"name"), kla = or(val("kla"),"KLA"), tech = or(val("tech"),"technology/app");
  const marks = CRIT.map(c => noaccess ? 0 : (band(c.id) ? mark(c.id) : null));
  const total = marks.every(m => m!==null) ? marks.reduce((a,b)=>a+b,0) : null;
  const blocks = []; // {head, text}
  blocks.push({text:`Hi ${name}, thank you for your submission.`});

  if (noaccess) {
    blocks.push({text:`Unfortunately, your resource could not be accessed because ${val("accessReason")}. It was an important part of the task for the resource to be submitted through ${LMS} in a form the marker can open, without needing to create an account, sign up or log in. As a result, it could not be marked against the rubric and has been placed in the Pre-structural band for each criterion. I would encourage you to read the instructions thoroughly and, if you are ever unsure, reach out to your tutor for clarification.`});
    return {blocks, total:0, marks};
  }

  const {quality: q, align: al} = autoOpening(total, band("c1"));
  const rating = val("rating"), tt = val("tooltype"), ls = val("lesson");
  let open = `Your resource is ${q ? AUTO(an(q)+" "+q) : "a "+GAP("overall resource")} student-facing digital resource ${al ? AUTO(al) : GAP("alignment")} to the ${kla} ${STAGE} Syllabus. `;
  open += rating==="not appropriate" ? `You have used ${tech}, which is not an appropriate ${tt} for this chosen ${ls}.`
    : `You have used ${tech}, which is ${rating ? an(rating)+" "+rating : "a "+GAP("suitability")} ${tt} for this chosen ${ls}.`;
  blocks.push({text:open});

  const fns = {c1:(b,m)=>c1Text(b,m,kla), c2:(b,m)=>c2Text(b,m,tech), c3:(b,m)=>c3Text(b,m)};
  CRIT.forEach((c,i) => {
    const b = band(c.id), m = marks[i];
    const head = `${c.tag}: ${c.title} (${m===null?"–":m}/10)`;
    blocks.push({head, text: b ? fns[c.id](b,m) : GAP(c.tag.toLowerCase())});
  });

  const ov = band("ov");
  const imp = [...picks("improve"), ...(val("improveOther") ? [val("improveOther")] : [])];
  const OV = {
    top: () => `This is a well thought through and designed digital resource and a great example of how ICT resources can be used in ${kla}. Well done!`,
    middle: () => `You have done a good job with your digital resource. To push it to the next level, it would have been good to see ${or(list(imp),"how they could improve")}. You were on the right track though, well done.`,
    low: () => `Although you were on the right track, there are some areas you could expand upon to strengthen your response. These include ${or(list(imp),"how they could improve")}.`,
    fail: () => `Unfortunately, due to ${or(val("failReason"),"reason")}, your resource didn't meet the standards set out in the rubric. I would encourage you to read the instructions thoroughly and, if you are ever unsure, reach out to your tutor for clarification.`
  };
  blocks.push({text: ov ? OV[ov]() : GAP("overall comment")});
  return {blocks, total, marks};
}

/* ---------- Render ---------- */
let plain = "";
function syncMarks(){
  // when a band is chosen with no valid mark, default to the top of its range
  CRIT.forEach(c => {
    const b = band(c.id); if (!b) return;
    const m = mark(c.id);
    if (m===null || !RANGE[b].includes(m)) $(`${c.id}m-${RANGE[b][0]}`).checked = true;
  });
}
function suggest(marks){
  const valid = marks.map((m,i)=>[m,CRIT[i].id]).filter(x=>x[0]!==null);
  const low = valid.length ? Math.min(...valid.map(x=>x[0])) : null;
  const lowIds = low===null || low===10 ? [] : valid.filter(x=>x[0]===low).map(x=>x[1]);
  IMPROVE.forEach(([cid],i) => document.querySelector(`label[for="improve-${i}"]`).classList.toggle("sugg", lowIds.includes(cid)));
}
function render(){
  syncMarks();
  const noaccess = $("noaccess").checked;
  $("accessCard").classList.toggle("on", noaccess);
  document.querySelectorAll(".crit").forEach(el => el.hidden = noaccess);
  document.querySelectorAll("[data-show]").forEach(el => {
    el.hidden = !el.dataset.show.split(" ").some(t => { if (t==="noaccess") return noaccess; const [k,v] = t.split(":"); return band(k) === v; });
  });
  CRIT.forEach(c => { const b = band(c.id); $(c.id+"-desc").textContent = b ? `${SOLO[b]}: ${c.short[b]}.` : "Choose a band.";
    const m = mark(c.id); $(c.id+"-score").textContent = b ? `${m}/10` : ""; });

  const {blocks, total, marks} = compose();
  suggest(marks);
  const heads = $("headings").checked, one = $("onepara").checked && !heads;
  $("onepara").disabled = heads;
  const tutor = or(val("tutor"),"tutor name"), so = val("signoff");
  const signLines = so ? [so + ",", tutor] : [tutor];
  const toHtml = s => esc(s).replace(/\u0000(.*?)\u0001/g, (_,g) => `<span class="gap">[${g}]</span>`).replace(/\u0002(.*?)\u0003/g, (_,g) => `<span class="autotext">${g}</span>`);
  const totalLine = heads && total!==null ? [`Total: ${total}/30`] : [];

  let html, txt;
  if (one) {
    html = `<p>${blocks.map(b=>toHtml(b.text)).join(" ")}</p>`;
    txt = blocks.map(b=>b.text).join(" ");
  } else {
    html = blocks.map(b => `<p>${heads && b.head ? `<span class="h">${toHtml(b.head)}</span>` : ""}${toHtml(b.text)}</p>`).join("");
    txt = blocks.map(b => (heads && b.head ? b.head + "\n" : "") + b.text).join("\n\n");
  }
  if (totalLine.length) { html += `<p><b>${totalLine[0]}</b></p>`; txt += "\n\n" + totalLine[0]; }
  html += `<p>${signLines.map(toHtml).join("<br>")}</p>`;
  txt += "\n\n" + signLines.join("\n");
  $("comment").innerHTML = html;
  edited = false;
  plain = txt.replace(/\u0000(.*?)\u0001/g, "[$1]").replace(/[\u0002\u0003]/g, "");

  const gaps = (txt.match(/\u0000/g) || []).length;
  $("status").textContent = gaps ? `${gaps} gap${gaps>1?"s":""} to fill` : "Complete";
  $("status").className = "status" + (gaps ? " warn" : "");
  $("total").textContent = `${total===null?"–":total}/30`;
}

let edited = false;
$("comment").addEventListener("input", () => { edited = true; });
$("f").addEventListener("input", render);
$("f").addEventListener("change", render);
$("f").addEventListener("submit", e => e.preventDefault());
const remember = (id, prop) => $(id).addEventListener("change", () => { try{localStorage.setItem("at3-"+id, String($(id)[prop]))}catch(e){} render(); });
remember("onepara","checked"); remember("headings","checked"); remember("samr","checked");
remember("tutor","value"); remember("signoff","value"); remember("kla","value");

$("copy").addEventListener("click", () => {
  const note = $("copyNote");
  const done = () => { $("copy").textContent = "Copied"; setTimeout(()=>{$("copy").textContent="Copy comment"},1500);
    note.textContent = /\[[^\]]+\]/.test(plain) ? "Copied, but the comment still has gaps in [brackets]." : `Copied. Paste it into ${LMS}.`; };
  const fallback = () => { const r = document.createRange(); r.selectNodeContents($("comment")); const s = getSelection(); s.removeAllRanges(); s.addRange(r);
    note.textContent = "Your browser blocked copying. The comment is selected, so press Ctrl+C (or ⌘C)."; };
  const text = edited ? $("comment").innerText.replace(/\n{3,}/g, "\n\n").trim() : plain;
  try { navigator.clipboard.writeText(text).then(done, fallback); } catch(e) { fallback(); }
});

$("next").addEventListener("click", () => {
  const keep = ["kla","tutor","signoff"].map(id => [id, $(id).value]);
  const keepChk = ["headings","samr","onepara"].map(id => [id, $(id).checked]);
  $("f").reset();
  keep.forEach(([id,v]) => $(id).value = v); keepChk.forEach(([id,v]) => $(id).checked = v);
  $("copyNote").textContent = "Green highlighted words are gaps still to fill.";
  render(); $("name").focus();
});

/* ---------- Example student + remembered settings ---------- */
try {
  for (const id of ["onepara","headings","samr"]) { const v = localStorage.getItem("at3-"+id); if (v!==null) $(id).checked = v==="true"; }
  for (const id of ["tutor","signoff"]) { const v = localStorage.getItem("at3-"+id); if (v!==null) $(id).value = v; }
} catch(e){}
render();
</script>

</body>
</html>
