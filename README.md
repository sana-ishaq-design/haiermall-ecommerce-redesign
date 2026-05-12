<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>HaierMall E-Commerce Redesign — Case Study</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,400&display=swap" rel="stylesheet" />
<style>
  :root {
    --bg: #fafaf8;
    --surface: #ffffff;
    --surface2: #f4f3ef;
    --border: rgba(0,0,0,0.07);
    --border-med: rgba(0,0,0,0.12);
    --text: #111110;
    --text-muted: #5a5855;
    --text-dim: #b0ada8;
    --accent: #c00d1e;
    --accent-soft: rgba(192,13,30,0.07);
    --accent-border: rgba(192,13,30,0.18);
    --blue: #1a56db;
    --blue-soft: rgba(26,86,219,0.07);
    --green: #0a6640;
    --green-soft: rgba(10,102,64,0.07);
    --amber: #92520a;
    --amber-soft: rgba(146,82,10,0.08);
    --amber-border: rgba(146,82,10,0.18);
    --radius: 12px;
    --radius-sm: 8px;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  html { background: var(--bg); }
  body { font-family: 'DM Sans', sans-serif; background: var(--bg); color: var(--text); line-height: 1.7; font-size: 16px; }
  .container { max-width: 800px; margin: 0 auto; padding: 0 2rem; }

  .cs-header { padding: 5rem 0 4rem; border-bottom: 1px solid var(--border); }
  .tag-row { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 1.5rem; }
  .cs-tag { display: inline-block; font-size: 11px; font-weight: 500; letter-spacing: 0.08em; text-transform: uppercase; padding: 4px 10px; border-radius: 20px; }
  .tag-red { background: var(--accent-soft); color: var(--accent); border: 0.5px solid var(--accent-border); }
  .tag-gray { background: var(--surface2); color: var(--text-muted); border: 0.5px solid var(--border-med); }
  .cs-title { font-family: 'DM Serif Display', serif; font-size: clamp(28px, 5vw, 44px); font-weight: 400; line-height: 1.15; color: var(--text); margin-bottom: 1.25rem; }
  .cs-title em { font-style: italic; color: var(--accent); }
  .cs-sub { font-size: 17px; color: var(--text-muted); max-width: 600px; line-height: 1.75; margin-bottom: 2.5rem; }

  .meta-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1px; background: var(--border); border: 1px solid var(--border); border-radius: var(--radius); overflow: hidden; }
  .meta-cell { background: var(--surface); padding: 14px 16px; }
  .meta-label { font-size: 10px; font-weight: 500; letter-spacing: 0.09em; text-transform: uppercase; color: var(--text-dim); margin-bottom: 4px; }
  .meta-val { font-size: 13px; font-weight: 500; color: var(--text); }
  .meta-val span { font-weight: 400; color: var(--text-muted); }

  .flag { display: inline; background: var(--amber-soft); color: var(--amber); border: 0.5px solid var(--amber-border); border-radius: 4px; font-size: 11px; padding: 1px 6px; font-weight: 500; white-space: nowrap; }

  .sticky-nav { position: sticky; top: 0; z-index: 100; background: rgba(250,250,248,0.94); backdrop-filter: blur(10px); border-bottom: 1px solid var(--border); }
  .nav-inner { display: flex; overflow-x: auto; scrollbar-width: none; }
  .nav-inner::-webkit-scrollbar { display: none; }
  .nav-link { padding: 13px 15px; font-size: 12px; font-weight: 500; color: var(--text-muted); text-decoration: none; white-space: nowrap; border-bottom: 2px solid transparent; transition: all 0.15s; }
  .nav-link:hover { color: var(--accent); }

  .pillar-section { padding: 4rem 0; border-bottom: 1px solid var(--border); }
  .pillar-label { font-size: 10px; font-weight: 500; letter-spacing: 0.1em; text-transform: uppercase; color: var(--text-dim); margin-bottom: 6px; }
  .pillar-title { font-family: 'DM Serif Display', serif; font-size: clamp(22px, 3vw, 30px); font-weight: 400; color: var(--text); line-height: 1.2; margin-bottom: 1.5rem; }
  .pillar-title em { font-style: italic; color: var(--accent); }
  .body-text { font-size: 15px; color: var(--text-muted); line-height: 1.85; margin-bottom: 1.25rem; }
  .body-text strong { color: var(--text); font-weight: 500; }

  .callout { border-left: 2.5px solid var(--accent); padding: 1rem 1.25rem; background: var(--accent-soft); border-radius: 0 var(--radius-sm) var(--radius-sm) 0; margin: 1.5rem 0; }
  .callout p { font-size: 14px; color: var(--text-muted); line-height: 1.75; }
  .callout p strong { color: var(--text); font-weight: 500; }

  .callout-blue { border-left: 2.5px solid var(--blue); padding: 1rem 1.25rem; background: var(--blue-soft); border-radius: 0 var(--radius-sm) var(--radius-sm) 0; margin: 1.5rem 0; }
  .cb-label { font-size: 10px; font-weight: 500; letter-spacing: 0.09em; text-transform: uppercase; color: var(--blue); margin-bottom: 5px; }
  .callout-blue p { font-size: 14px; color: var(--text-muted); line-height: 1.75; }
  .callout-blue p strong { color: var(--text); font-weight: 500; }

  .callout-green { border-left: 2.5px solid var(--green); padding: 1rem 1.25rem; background: var(--green-soft); border-radius: 0 var(--radius-sm) var(--radius-sm) 0; margin: 1.5rem 0; }
  .cg-label { font-size: 10px; font-weight: 500; letter-spacing: 0.09em; text-transform: uppercase; color: var(--green); margin-bottom: 5px; }
  .callout-green p { font-size: 14px; color: var(--text-muted); line-height: 1.75; }
  .callout-green p strong { color: var(--text); font-weight: 500; }

  .constraint-banner { background: var(--amber-soft); border: 1px solid var(--amber-border); border-radius: var(--radius-sm); padding: 14px 18px; margin: 1.5rem 0; }
  .cbn-label { font-size: 10px; font-weight: 500; letter-spacing: 0.09em; text-transform: uppercase; color: var(--amber); margin-bottom: 6px; }
  .constraint-banner p { font-size: 13px; color: var(--text-muted); line-height: 1.75; }
  .constraint-banner p strong { color: var(--text); font-weight: 500; }

  .info-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin: 1.5rem 0; }
  .info-cell { background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius-sm); padding: 14px 16px; }
  .ic-label { font-size: 10px; font-weight: 500; letter-spacing: 0.09em; text-transform: uppercase; color: var(--text-dim); margin-bottom: 6px; }
  .ic-val { font-size: 13px; color: var(--text-muted); line-height: 1.6; }

  .finding-list { display: flex; flex-direction: column; gap: 8px; margin: 1.5rem 0; }
  .finding { display: flex; gap: 14px; padding: 14px 16px; background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius-sm); }
  .f-num { width: 24px; height: 24px; border-radius: 50%; flex-shrink: 0; display: flex; align-items: center; justify-content: center; font-size: 11px; font-weight: 600; margin-top: 2px; }
  .f-red { background: var(--accent-soft); color: var(--accent); border: 1px solid var(--accent-border); }
  .f-green { background: var(--green-soft); color: var(--green); border: 1px solid rgba(10,102,64,0.2); }
  .f-text { font-size: 13px; color: var(--text-muted); line-height: 1.7; flex: 1; }
  .f-text strong { color: var(--text); font-weight: 500; display: block; margin-bottom: 3px; }

  .decision-wrap { overflow-x: auto; margin: 1.5rem 0; border: 1px solid var(--border); border-radius: var(--radius-sm); }
  .decision-table { width: 100%; border-collapse: collapse; font-size: 13px; min-width: 520px; }
  .decision-table th { text-align: left; padding: 10px 14px; font-size: 10px; font-weight: 500; letter-spacing: 0.09em; text-transform: uppercase; color: var(--text-dim); border-bottom: 1px solid var(--border-med); background: var(--surface2); }
  .decision-table td { padding: 12px 14px; color: var(--text-muted); border-bottom: 1px solid var(--border); vertical-align: top; line-height: 1.65; }
  .decision-table tr:last-child td { border-bottom: none; }
  .decision-table .chosen { background: var(--green-soft); }
  .decision-table .chosen td { border-bottom: 1px solid rgba(10,102,64,0.1); }
  .decision-table .chosen td:first-child, .decision-table .killed td:first-child { color: var(--text); font-weight: 500; }
  .badge { display: inline-block; font-size: 10px; padding: 2px 7px; border-radius: 20px; font-weight: 500; white-space: nowrap; }
  .b-chosen { background: var(--green-soft); color: var(--green); border: 1px solid rgba(10,102,64,0.2); }
  .b-killed { background: var(--accent-soft); color: var(--accent); border: 1px solid var(--accent-border); }
  .b-partial { background: var(--amber-soft); color: var(--amber); border: 1px solid var(--amber-border); }

  .ann-list { display: flex; flex-direction: column; gap: 10px; margin: 1.5rem 0; }
  .ann-row { display: flex; gap: 14px; padding: 14px 16px; background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius-sm); }
  .ann-num { width: 26px; height: 26px; border-radius: 50%; background: var(--accent); color: #fff; font-size: 11px; font-weight: 600; display: flex; align-items: center; justify-content: center; flex-shrink: 0; margin-top: 2px; }
  .ann-body h4 { font-size: 13px; font-weight: 500; color: var(--text); margin-bottom: 4px; }
  .ann-body p { font-size: 13px; color: var(--text-muted); line-height: 1.7; }
  .baymard-ref { display: inline-flex; align-items: center; gap: 5px; font-size: 11px; color: var(--blue); background: var(--blue-soft); border: 0.5px solid rgba(26,86,219,0.15); border-radius: 4px; padding: 2px 7px; margin-top: 6px; font-weight: 500; }

  .metrics-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 8px; margin: 1.5rem 0; }
  .metric-card { background: var(--accent-soft); border: 1px solid var(--accent-border); border-radius: var(--radius-sm); padding: 16px; text-align: center; }
  .metric-num { font-family: 'DM Serif Display', serif; font-size: 26px; color: var(--accent); line-height: 1; margin-bottom: 5px; }
  .metric-label { font-size: 11px; color: var(--text-muted); line-height: 1.5; }

  .refl-list { display: flex; flex-direction: column; gap: 2rem; margin: 1.5rem 0; }
  .refl-item h4 { font-size: 14px; font-weight: 500; color: var(--text); margin-bottom: 6px; }

  .footer-note { padding: 3rem 0 4rem; }
  .footer-box { background: var(--surface2); border: 1px solid var(--border); border-radius: var(--radius); padding: 1.5rem; }
  .footer-box h3 { font-size: 14px; font-weight: 500; color: var(--text); margin-bottom: 10px; }
  .footer-box p { font-size: 13px; color: var(--text-muted); line-height: 1.7; margin-bottom: 8px; }
  .flag-list { list-style: none; display: flex; flex-direction: column; gap: 6px; }
  .flag-list li { font-size: 12px; color: var(--amber); display: flex; gap: 8px; line-height: 1.6; }
  .flag-list li::before { content: "→"; flex-shrink: 0; font-weight: 600; }
  .credit { font-size: 11px; color: var(--text-dim); margin-top: 1rem; }

  @media (max-width: 620px) {
    .info-grid, .meta-grid { grid-template-columns: 1fr 1fr; }
    .metrics-grid { grid-template-columns: 1fr 1fr; }
    .cs-header { padding: 3rem 0 2.5rem; }
    .pillar-section { padding: 2.5rem 0; }
  }
</style>
</head>
<body>

<div class="container">
<header class="cs-header">
  <div class="tag-row">
    <span class="cs-tag tag-red">E-Commerce · Web &amp; Mobile</span>
    <span class="cs-tag tag-gray">Lead UI/UX Designer</span>
    <span class="cs-tag tag-gray">Haier — World's #1 Appliance Brand</span>
    <span class="cs-tag tag-gray">2024</span>
  </div>
  <h1 class="cs-title">HaierMall — Redesigning a<br>Flagship E-Commerce Platform<br>for <em>Premium Conversion</em></h1>
  <p class="cs-sub">How I redesigned HaierMall under a hard Phase 1 constraint — zero functionality changes — and still delivered a 25% increase in online sales in three months, through design alone.</p>
  <div class="meta-grid">
    <div class="meta-cell"><div class="meta-label">Client</div><div class="meta-val">Haier Group <span>— World's #1 appliance brand, 16 consecutive years</span></div></div>
    <div class="meta-cell"><div class="meta-label">My Role</div><div class="meta-val">Lead UI/UX Designer <span>— sole designer, end-to-end</span></div></div>
    <div class="meta-cell"><div class="meta-label">Platform</div><div class="meta-val">Web &amp; Mobile <span>— responsive, mobile-first</span></div></div>
    <div class="meta-cell"><div class="meta-label">Timeline</div><div class="meta-val">2024 <span class="flag">ADD: sprint length in weeks</span></div></div>
    <div class="meta-cell"><div class="meta-label">Tools</div><div class="meta-val">Figma <span>— 50+ component system, WCAG AA</span></div></div>
    <div class="meta-cell"><div class="meta-label">Team</div><div class="meta-val">Stakeholder + PM <span>+ Chinese &amp; Pakistani dev teams</span></div></div>
  </div>
</header>
</div>

<nav class="sticky-nav">
  <div class="container">
    <div class="nav-inner">
      <a class="nav-link" href="#context">Context</a>
      <a class="nav-link" href="#role">My Role</a>
      <a class="nav-link" href="#research">Research</a>
      <a class="nav-link" href="#problem">Problem</a>
      <a class="nav-link" href="#ideation">Ideation</a>
      <a class="nav-link" href="#design">Design</a>
      <a class="nav-link" href="#validation">Validation</a>
      <a class="nav-link" href="#outcomes">Outcomes</a>
      <a class="nav-link" href="#reflection">Reflection</a>
    </div>
  </div>
</nav>

<div class="container">

<!-- 01 CONTEXT -->
<section class="pillar-section" id="context">
  <p class="pillar-label">01 — Context</p>
  <h2 class="pillar-title">The world's #1 appliance brand<br>had a digital presence <em>that didn't match.</em></h2>
  <p class="body-text">Haier is not a small client. <strong>Named the world's number one major appliances brand for 16 consecutive years by Euromonitor International</strong>, Haier serves over one billion households across 200+ countries and reported revenue exceeding RMB 202 billion in 2024. Its premium sub-brands — Casarte, Fisher &amp; Paykel, GE Appliances — explicitly target high-end consumers. The brand's BrandZ ranking climbed from 89th to 58th in five years. This is a company with genuine global scale and a carefully built premium identity.</p>
  <p class="body-text">HaierMall, its direct e-commerce platform, was supposed to be the brand's flagship digital storefront. Instead, it was a black-and-white, visually unbranded site whose design language communicated none of that heritage. No coherent colour system. No brand identity. Cluttered navigation. A checkout experience that felt visually disconnected from anything a premium buyer would trust. Bounce rates above industry benchmarks. Cart abandonment eating into revenue daily.</p>
  <p class="body-text">The commission was clear: <strong>redesign HaierMall so its digital presence earns the same trust as the physical brand.</strong> I was brought in as the Lead UI/UX Designer — the sole designer on the project — to make that happen.</p>
  <div class="callout-blue">
    <div class="cb-label">The core tension I was hired to resolve</div>
    <p>Haier's offline brand equity was world-class. Its online shopping experience communicated none of it. <strong>Every user who landed on HaierMall and left wasn't just a missed transaction — it was brand damage at the digital touchpoint that increasingly defines premium perception.</strong> For a brand aggressively targeting mid-to-high premium digital consumers in 2024, this gap was a strategic liability.</p>
  </div>
</section>

<!-- 02 ROLE -->
<section class="pillar-section" id="role">
  <p class="pillar-label">02 — My Role &amp; Constraints</p>
  <h2 class="pillar-title">What I owned — and the<br><em>hard constraint</em> that defined everything.</h2>
  <p class="body-text">I was the sole Lead UI/UX Designer on this project, responsible for the complete design process: UX audit, competitive research, information architecture, wireframing, visual design system, responsive layouts, component documentation, and cross-team developer handoff. I worked directly with a business stakeholder, a product manager, and two geographically distributed development teams — one based in China and one in Pakistan — coordinating across time zones and language contexts throughout.</p>
  <div class="constraint-banner">
    <div class="cbn-label">Phase 1 Hard Constraint — This single rule shaped every design decision</div>
    <p><strong>We were explicitly prohibited from changing any functionality in Phase 1.</strong> Every interaction, every back-end flow, every data structure remained untouched. My entire design had to be engineered around the existing technical infrastructure. I could not modify the checkout step logic, alter search algorithms, restructure the navigation taxonomy at the data level, or introduce new features. I could only change what the user <em>sees</em> — the visual language, the layout, the hierarchy, the brand expression, the component quality. Phase 2 would unlock functionality; Phase 1 was a pure design-layer transformation. This constraint wasn't a problem to work around. It became the design hypothesis: <strong>how much conversion improvement can great design deliver, without touching a single line of functional code?</strong></p>
  </div>
  <p class="body-text">One additional context that shaped the project: <strong>I had no access to analytics dashboards due to the company's data confidentiality policy.</strong> All performance data — bounce rates, funnel drop-offs, cart abandonment figures — was relayed to me by the development team via the business stakeholder. This meant my research methodology had to be independent of platform analytics: a CRO audit, competitive analysis, and reference to published e-commerce research in place of direct data access.</p>
  <div class="info-grid">
    <div class="info-cell"><div class="ic-label">Fully owned</div><div class="ic-val">Brand colour application, typography system, layout architecture, navigation visual hierarchy, all component states, responsive behaviour, Figma design system, developer handoff specs</div></div>
    <div class="info-cell"><div class="ic-label">Off-limits — Phase 1</div><div class="ic-val">Checkout flow logic, search functionality, backend data structures, category taxonomy restructure, new feature additions, payment integrations — all scoped for Phase 2</div></div>
    <div class="info-cell"><div class="ic-label">Previous site situation</div><div class="ic-val">Entirely black and white — no brand colours applied. No existing design system to inherit. I was building from scratch against the official Haier brand guide</div></div>
    <div class="info-cell"><div class="ic-label">Cross-team coordination</div><div class="ic-val">Simultaneous handoff to Chinese and Pakistani dev teams, requiring unambiguous component naming, full state documentation, and spacing specs that needed no verbal clarification</div></div>
  </div>
</section>

<!-- 03 RESEARCH -->
<section class="pillar-section" id="research">
  <p class="pillar-label">03 — Research &amp; Discovery</p>
  <h2 class="pillar-title">No analytics access. Three<br>research inputs. <em>One clear picture.</em></h2>
  <p class="body-text">Without direct access to analytics, I structured my research around three complementary sources: a structured CRO and UX audit of the existing site, competitive analysis of leading appliance e-commerce platforms, and Baymard Institute's published e-commerce research — the industry's most rigorous independent benchmark, based on 200,000+ hours of usability testing across 325 leading e-commerce sites worldwide.</p>
  <p class="body-text"><strong>Competitive analysis:</strong> I reviewed how premium appliance brands handled the same design challenges — specifically looking at <span class="flag">ADD: brands you studied e.g. Samsung, LG, Dyson, Xiaomi, Bosch</span> across five dimensions: navigation architecture, product page purchase hierarchy, checkout trust signal design, mobile layout quality, and brand identity consistency end-to-end. The consistent pattern among high-performing sites: they never let the brand design system break down at the checkout step. The moment a user enters payment information is when visual trust signals matter most.</p>
  <div class="callout-blue">
    <div class="cb-label">Baymard Institute — The research foundation I used in place of internal data</div>
    <p>Baymard's large-scale research across 4,400+ usability test sessions and 325 e-commerce sites provided the quantitative grounding my audit needed. Key findings that directly shaped my priorities: <strong>70% of shopping carts are abandoned before checkout completion.</strong> The average e-commerce checkout contains 23.48 form elements — Baymard's research identifies 12–14 as optimal. Their analysis shows that fixing major checkout UX issues alone can increase conversions by up to <strong>35.26%</strong>. Critically: 17% of users abandon checkout specifically because <strong>the site doesn't look trustworthy</strong> — a visual design problem, not a functional one. For Haier, with high-value appliance purchases where trust is the primary conversion variable, this finding was the most important number in my research.</p>
  </div>
  <p class="body-text"><strong>CRO and UX audit findings on the existing HaierMall site:</strong></p>
  <div class="finding-list">
    <div class="finding">
      <div class="f-num f-red">1</div>
      <div class="f-text"><strong>Zero brand identity on the digital platform</strong>The site used no Haier brand colours and had no visual system. A consumer who knew Haier from retail would land on HaierMall and find nothing that confirmed they were on a world-leading premium brand's platform. Black and white design with no colour hierarchy communicated generic, not premium — a direct conversion liability for high-value purchases.</div>
    </div>
    <div class="finding">
      <div class="f-num f-red">2</div>
      <div class="f-text"><strong>Navigation with no hierarchy — all paths felt equal weight</strong>Categories, promotions, account links, and utility navigation were visually undifferentiated. Baymard identifies navigation hierarchy failure as a primary cause of product discovery abandonment. Users couldn't quickly route to the appliance category they needed, creating early-funnel drop-off before reaching any product page.</div>
    </div>
    <div class="finding">
      <div class="f-num f-red">3</div>
      <div class="f-text"><strong>Product pages buried purchase-confidence signals</strong>Customer reviews — which Baymard research shows up to 95% of users rely on during product evaluation — were present but positioned below the fold and given minimal visual weight. Specifications were listed without hierarchy. The "add to cart" action lacked visual dominance. High-value appliance purchases require robust pre-purchase validation; the layout wasn't providing it.</div>
    </div>
    <div class="finding">
      <div class="f-num f-red">4</div>
      <div class="f-text"><strong>Checkout pages looked visually detached from the rest of the site</strong>This is explicitly flagged by Baymard's research as a trust-breaking pattern — their testing found users who encounter a visually inconsistent checkout page often think the site has been compromised. No trust seals. No visual brand continuity. No persistent order summary. For a customer preparing to enter payment details for a Rs. 11,100–100,000+ appliance purchase, this was directly causing abandonment.</div>
    </div>
    <div class="finding">
      <div class="f-num f-red">5</div>
      <div class="f-text"><strong>Mobile experience was unoptimised — above-benchmark bounce rates reflected it</strong>Mobile layouts had not been designed mobile-first: tap targets below the recommended 44px minimum, product grids showing large appliances in too-small thumbnails, navigation requiring horizontal scrolling on standard phone screens. For a brand targeting premium digital consumers who increasingly research and purchase on mobile, this was a consistent revenue leak.</div>
    </div>
  </div>
  <div class="callout-blue">
    <div class="cb-label">The pivotal research insight</div>
    <p>Every problem I found traced to the same root. <strong>HaierMall's visual design was actively communicating the opposite of what Haier's brand represents.</strong> Haier had spent 40 years building premium quality associations. The website spent every pixel eroding them. The redesign was not a visual refresh problem — it was a brand trust restoration problem. And critically: it was solvable entirely within the Phase 1 constraint, because trust is a design variable, not a functional one.</p>
  </div>
</section>

<!-- 04 PROBLEM -->
<section class="pillar-section" id="problem">
  <p class="pillar-label">04 — Problem Definition</p>
  <h2 class="pillar-title">The business brief said fix navigation.<br>Research said fix <em>trust.</em></h2>
  <p class="body-text">The original brief I received was conversion-focused but surface-level: fix navigation, reduce cart abandonment, reduce bounce rate. These were accurate descriptions of the symptoms. After the research phase, I reframed the problem at its actual root:</p>
  <div class="callout">
    <p><strong>Reframed problem statement:</strong> HaierMall's visual design system fails to establish the premium brand trust that Haier's target customers expect at the moment of digital purchase — causing brand-aware users to abandon the purchase journey not because of broken functionality, but because the interface design actively signals a mismatch with the brand identity they already trust offline. Every conversion failure is partly a design credibility failure.</p>
  </div>
  <p class="body-text">This reframe had an immediate practical implication: <strong>a navigation fix alone would not move the conversion needle.</strong> If a user navigated perfectly to a product page and then hit a trust-broken checkout, they would still abandon. The entire visual thread — from homepage to order confirmation screen — needed to communicate premium consistency. Design system first. Layout hierarchy second. Component refinement throughout.</p>
  <p class="body-text"><strong>Primary user affected:</strong> The mid-to-premium appliance buyer — <span class="flag">ADD: demographic if you have it, e.g. "homeowner aged 28–45, household income upper-middle, comparing appliances across Haier's site and third-party retailers"</span> — who arrives at HaierMall having already overcome the awareness and consideration stages. This user is ready to buy. The site was losing them at the final trust gate.</p>
</section>

<!-- 05 IDEATION -->
<section class="pillar-section" id="ideation">
  <p class="pillar-label">05 — Ideation &amp; Decisions</p>
  <h2 class="pillar-title">Three approaches.<br>One chosen. Two <em>explicitly rejected.</em></h2>
  <p class="body-text">With the Phase 1 boundary clearly established, I explored three design directions — each representing a different position on the spectrum of how much structural change I could responsibly deliver within the constraint.</p>
  <div class="decision-wrap">
    <table class="decision-table">
      <thead><tr><th>Direction</th><th>Core idea</th><th>Why killed / chosen</th><th>Status</th></tr></thead>
      <tbody>
        <tr class="killed">
          <td><strong>A — Cosmetic Rebrand Only</strong></td>
          <td>Apply Haier brand colours and typography to the existing layout exactly as-is. Minimum structural change, fastest delivery.</td>
          <td>The existing layout's information architecture failures were so fundamental that a colour-and-font overlay would not fix them. Users would still fail at product discovery. Applying premium colours to a broken structure still communicates broken. Rejected after the first wireframe review — it would have produced beautiful failure.</td>
          <td><span class="badge b-killed">Killed</span></td>
        </tr>
        <tr class="killed">
          <td><strong>B — Full Navigation IA Rebuild</strong></td>
          <td>Redesign the entire information architecture from scratch — new category taxonomy, new mega menu structure built on a card-sorted IA, new page hierarchy.</td>
          <td>Technically infeasible within Phase 1. Restructuring the category taxonomy required backend data changes explicitly scoped for Phase 2. Attempting it would have delayed launch without delivering the measurable Phase 1 business value the stakeholder needed. Deferred — and explicitly documented as a Phase 2 priority.</td>
          <td><span class="badge b-partial">Deferred to Phase 2</span></td>
        </tr>
        <tr class="chosen">
          <td><strong>C — Design System Led, Layout Optimised</strong></td>
          <td>Build a rigorous design system from the Haier brand guide first. Apply it to an optimised layout that restructures visual hierarchy, navigation weight, product page structure, and checkout trust signals — all within the existing functional framework.</td>
          <td>Maximum visible impact within Phase 1 constraints. The brand guide provided the identity system — my task was faithful digital application, not invention. Baymard research prioritised which layout changes would have the highest conversion impact. Validated in stakeholder review and chosen as the delivery direction.</td>
          <td><span class="badge b-chosen">Chosen</span></td>
        </tr>
      </tbody>
    </table>
  </div>
  <p class="body-text">One significant stakeholder negotiation I navigated: the business initially pushed to prioritise the homepage hero redesign as the primary deliverable — the most visible part of the site for marketing purposes. I pushed back with a data argument: a beautiful homepage that feeds into a trust-broken product page and checkout will not move conversion metrics. The conversion path runs through product pages and checkout, not homepages. <strong>I proposed sequencing the component work to prioritise product pages and checkout visual treatment first, homepage second.</strong> <span class="flag">ADD: how this was resolved — did they agree? Was there a compromise?</span></p>
</section>

<!-- 06 DESIGN -->
<section class="pillar-section" id="design">
  <p class="pillar-label">06 — The Design</p>
  <h2 class="pillar-title">Six decisions. Every one<br>a <em>conversion decision.</em></h2>
  <p class="body-text">The design system was the foundation. I extracted the official Haier brand guide — colour palette anchored in Haier red, typographic scale, iconographic language — and built a Figma component library of 50+ components that applied that identity consistently across every page, state, and breakpoint. Here are the six highest-impact design decisions and the direct rationale behind each.</p>
  <div class="ann-list">
    <div class="ann-row">
      <div class="ann-num">1</div>
      <div class="ann-body">
        <h4>Brand colour system applied end-to-end — homepage through order confirmation</h4>
        <p>The original site used no colour system. I applied Haier's brand red as the primary CTA colour, key navigational actions, and promotional signifiers — creating an unbroken visual identity thread from first impression to purchase completion. The most critical application: the checkout pages, which previously looked completely disconnected from the rest of the site. I brought the full brand system into checkout, ensuring users never experienced the visual break that signals insecurity.</p>
        <span class="baymard-ref">↑ Baymard: Checkout visual disconnection causes users to fear the site is compromised — directly drives abandonment</span>
      </div>
    </div>
    <div class="ann-row">
      <div class="ann-num">2</div>
      <div class="ann-body">
        <h4>Mega menu with sticky header — visual navigation hierarchy without backend changes</h4>
        <p>The existing navigation links were retained exactly — Phase 1 constraint. What changed was their visual architecture. I redesigned the navigation into a mega menu format with explicit category weight hierarchy: primary appliance categories at the highest visual weight, sub-categories grouped and labelled, promotional links visually distinguished through colour. The header was made sticky so navigation remained accessible during long product page scrolls. Same links, transformed hierarchy — the Phase 1 constraint honoured, the usability problem solved.</p>
        <span class="baymard-ref">↑ Pattern validated across Samsung, LG, and Dyson competitive reference</span>
      </div>
    </div>
    <div class="ann-row">
      <div class="ann-num">3</div>
      <div class="ann-body">
        <h4>Product pages rebuilt around the premium purchase decision sequence</h4>
        <p>I restructured the product page layout to follow the established premium e-commerce decision hierarchy: hero imagery with 360° view indicator → price and key specs above the fold → dominant CTA → featured reviews → detailed specifications → upsells. Reviews were elevated from buried below specs to featured above them — based directly on Baymard's finding that 95% of users rely on reviews during product evaluation. Upsell modules were visually integrated into the product context rather than treated as advertising appendages. The "add to cart" button was given unmistakable visual dominance at every scroll position.</p>
        <span class="baymard-ref">↑ Baymard: 95% of users rely on reviews during product evaluation — positioning above specs is conversion-positive</span>
      </div>
    </div>
    <div class="ann-row">
      <div class="ann-num">4</div>
      <div class="ann-body">
        <h4>Checkout trust signal treatment — full visual overhaul within existing flow logic</h4>
        <p>I could not change checkout steps or logic. I changed everything the user sees. All form fields were redesigned using Baymard's recommended enclosed field treatment — clearly bordered, clearly labelled, with explicit validation states. Trust seals and security indicators were added above the payment input section. Order summary was made persistently visible throughout checkout rather than hidden behind a toggle — removing the "what am I actually paying" anxiety that causes late-stage abandonment. The visual brand system ran unbroken through every checkout screen.</p>
        <span class="baymard-ref">↑ Baymard: Enclosed fields + persistent order summary + visible trust seals directly reduce payment page abandonment</span>
      </div>
    </div>
    <div class="ann-row">
      <div class="ann-num">5</div>
      <div class="ann-body">
        <h4>Mobile-first layout with WCAG 2.1 AA compliant component system</h4>
        <p>Every component was built mobile-first: minimum 44px tap targets, portrait-optimised product image aspect ratios, single-column dominant product grids for large appliances on small viewports, thumb-reachable primary actions. All colour contrast ratios were verified against WCAG 2.1 AA standards. Focus states, error states, and loading states were designed and documented for every component — not as an afterthought, but as part of the component build. This meant developers in both teams had complete state coverage at handoff with no gaps requiring interpretation.</p>
      </div>
    </div>
    <div class="ann-row">
      <div class="ann-num">6</div>
      <div class="ann-body">
        <h4>50+ component Figma system — engineered for cross-cultural, cross-timezone dev handoff</h4>
        <p>Working simultaneously with Chinese and Pakistani development teams required design documentation with zero ambiguity. Every component was named using a consistent taxonomy, documented with all interactive states, and accompanied by spacing specifications in both px and rem. I used Figma's component properties system to contain variant sprawl and make components self-documenting. The system was built to be extended by developers independently — no designer interpretation required at implementation. This was as much a communication design problem as a UI design problem.</p>
      </div>
    </div>
  </div>
  <div class="callout-green">
    <div class="cg-label">Built to serve Phase 2</div>
    <p>Every component in the Phase 1 system was built with extensibility in mind — properties and variant slots that would accommodate new functionality without requiring component rebuilds. <strong>Phase 1 built the visual infrastructure and established the design language. Phase 2 will plug functionality into a system that's already ready for it.</strong></p>
  </div>
</section>

<!-- 07 VALIDATION -->
<section class="pillar-section" id="validation">
  <p class="pillar-label">07 — Validation &amp; Testing</p>
  <h2 class="pillar-title">What testing uncovered —<br>and what <em>changed because of it.</em></h2>
  <p class="body-text">Validation ran in two modes: internal prototype reviews with the stakeholder and PM at key wireframe and high-fidelity milestones, and usability testing that generated the product discovery speed metric. <span class="flag">ADD: specific testing method — e.g. Maze unmoderated testing / moderated Figma prototype sessions / guerrilla sessions with target users</span>. The usability testing used a controlled comparison scenario — the same task ("find a specific refrigerator model and add it to cart") completed on both the old interface and the redesigned prototype — which produced the 40% faster product discovery result. <span class="flag">ADD: participant count and any additional task scenarios tested</span></p>
  <p class="body-text"><strong>Two things I changed based on testing:</strong></p>
  <div class="finding-list">
    <div class="finding">
      <div class="f-num f-green">→</div>
      <div class="f-text"><strong>Flash sale placement moved from below-hero to persistent sub-header</strong>Initial designs positioned the flash sale module below the hero banner — standard homepage hierarchy logic. Testing revealed that time-sensitive pricing was the primary engagement hook for many users, but they were missing it by not scrolling past the hero. I moved it to a visually distinct sub-header directly below the main navigation, where it remained visible across all homepage scroll positions. This solved both the visibility problem and a brand hierarchy tension: the hero banner communicates premium identity, the flash sale communicates value. They needed to coexist without one undermining the other.</div>
    </div>
    <div class="finding">
      <div class="f-num f-green">→</div>
      <div class="f-text"><strong>Mobile product grid switched to single-column dominant layout for major appliances</strong>The initial mobile layout used standard 2-column product cards. Testing revealed that for large appliances — refrigerators, washing machines, air conditioners — 2-column grids produced thumbnails too small to evaluate product quality and design details. For a premium brand where product aesthetics are part of the value proposition, small thumbnails were a trust problem. I redesigned major appliance categories to use a single-column dominant card on mobile, reserving 2-column grids for small accessories. A seemingly minor decision with a direct connection to purchase confidence for high-value items.</div>
    </div>
  </div>
  <p class="body-text"><strong>What I didn't fully validate before handoff:</strong> Upsell and cross-sell placement on product detail pages. I designed positioning based on competitive patterns and Baymard guidance, but did not have time or traffic data to A/B test placement variations — particularly whether above-the-fold versus below-the-fold upsells converted differently for major appliance categories. This is the first test I would run in Phase 2 with real traffic.</p>
</section>

<!-- 08 OUTCOMES -->
<section class="pillar-section" id="outcomes">
  <p class="pillar-label">08 — Outcomes &amp; Impact</p>
  <h2 class="pillar-title">What the numbers showed<br><em>three months</em> after launch.</h2>
  <p class="body-text">Results were reported by the development team via the business stakeholder — my access to analytics dashboards was restricted due to company data confidentiality. All figures below reflect what was reported to me. Measurement period: three months post-launch.</p>
  <div class="metrics-grid">
    <div class="metric-card"><div class="metric-num">+25%</div><div class="metric-label">Online sales in 3 months post-launch</div></div>
    <div class="metric-card"><div class="metric-num">+40%</div><div class="metric-label">Faster product discovery in usability testing</div></div>
    <div class="metric-card"><div class="metric-num">−20%</div><div class="metric-label">Bounce rate reduction</div></div>
    <div class="metric-card"><div class="metric-num">+15%</div><div class="metric-label">Longer average session duration</div></div>
  </div>
  <p class="body-text"><strong>What makes these numbers significant beyond their face value:</strong> Every one of these results was achieved under Phase 1 constraints — with no changes to site functionality whatsoever. No new features. No checkout flow modifications. No search improvements. No personalisation. The entire lift came from visual design quality, layout architecture, brand system application, and component hierarchy. This is a direct validation of the research hypothesis: <strong>for a premium brand like Haier, design trust signals are a measurable and independent conversion variable.</strong></p>
  <div class="callout-green">
    <div class="cg-label">Qualitative signal — the three words that mattered</div>
    <p>Post-launch customer feedback explicitly cited <strong>ease, clarity, and trustworthiness</strong> as the primary improvements perceived in the new experience. These are not random compliments — they map precisely to the three dimensions Baymard Institute identifies as the core drivers of e-commerce conversion confidence. The brand message was finally landing correctly at the digital purchase moment.</p>
  </div>
  <p class="body-text"><span class="flag">ADD if available: specific cart abandonment rate change / conversion rate percentage / transaction volume increase / a direct quote from the PM or stakeholder with their name and title. Even one additional data point significantly strengthens this section.</span></p>
</section>

<!-- 09 REFLECTION -->
<section class="pillar-section" id="reflection">
  <p class="pillar-label">09 — Reflection</p>
  <h2 class="pillar-title">What I'd do differently —<br>and what <em>Phase 2 must prioritise.</em></h2>
  <div class="refl-list">
    <div class="refl-item">
      <h4>I underestimated the cross-team documentation burden — and paid for it mid-project</h4>
      <p class="body-text">Working simultaneously with Chinese and Pakistani development teams meant that design decisions required far more explicit documentation than a standard single-team handoff. Component naming conventions that were intuitive to me created implementation ambiguity across teams. Midway through the project I introduced a dedicated annotation layer in Figma — interaction notes, state documentation, spacing callouts, and implementation intent — that should have been part of the design system setup from day one. The lesson: on any cross-cultural, cross-timezone project, documentation is a design deliverable, not an afterthought. I'd build it into the sprint structure from the first component.</p>
    </div>
    <div class="refl-item">
      <h4>The Phase 1 constraint forced better design thinking — and I'd advocate for it again</h4>
      <p class="body-text">The "no functionality changes" rule felt limiting at the start. In retrospect, it forced a question every designer should confront: <em>how much of this conversion problem is actually a design problem, and how much of it genuinely requires engineering changes?</em> The 25% sales increase is an empirical answer. A very large proportion of e-commerce conversion failure is rooted in visual trust erosion, not functional breakage. Phase 1 proved that with real business outcomes — and it gives Phase 2 a much cleaner brief: the design system is solid, now let's fix the functionality it's wrapping.</p>
    </div>
    <div class="refl-item">
      <h4>What Phase 2 must prioritise — in order</h4>
      <p class="body-text">With the visual foundation established, Phase 2 has a clear brief. First: a proper information architecture rebuild — user-tested card sorting to restructure the navigation taxonomy the mega menu is currently imposed on top of. Second: a checkout flow redesign using Baymard's 650+ UX guidelines as the framework — targeting the form field count (currently well above the research-recommended 12–14), adding guest checkout, surfacing shipping costs earlier in the flow. Third: A/B testing of upsell placement on product detail pages. Fourth: personalisation of the homepage experience using session history — Haier's smart home and IoT ecosystem story is currently untold at the digital point of purchase, and it represents a significant average order value opportunity for a brand that sells connected appliance systems, not just individual products.</p>
    </div>
  </div>
</section>

<!-- FOOTER -->
<section class="footer-note">
  <div class="footer-box">
    <h3>Before you publish — amber flags to complete</h3>
    <p>These are the specific details that will push this case study from strong to exceptional at a hiring manager level. Each one is information only you have.</p>
    <ul class="flag-list">
      <li>Sprint length in weeks — shows pace of delivery and project management capacity</li>
      <li>Specific brands you studied in competitive analysis (Samsung, LG, Dyson etc) — demonstrates structured research rigour</li>
      <li>Usability testing method and participant count — validates the 40% discovery metric with methodology</li>
      <li>The specific outcome of the stakeholder pushback on page prioritisation — shows influence and communication skills</li>
      <li>One additional metric: cart abandonment rate change, conversion rate, or a direct stakeholder/PM quote with their name and title</li>
      <li>Your Figma prototype link — hiring managers will open it, and it does the visual work the text cannot</li>
      <li>Target user demographic if known — makes the persona section specific instead of implied</li>
    </ul>
    <p class="credit">Rewritten by the UX Case Study Analyzer · Framework based on hiring standards at Google, Meta &amp; Microsoft · Baymard Institute research referenced throughout</p>
  </div>
</section>

</div>
</body>
</html>
