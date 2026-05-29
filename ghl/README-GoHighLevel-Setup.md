# PerformWell Coaching → GoHighLevel Setup

This folder contains your landing page split into the pieces GoHighLevel (GHL) needs.

## Files

| File | What it is | Where it goes in GHL |
|------|-----------|----------------------|
| `1-head-code.html` | Google Fonts links | Funnel/Website **Head** tracking code |
| `2-custom-code-block.html` | All CSS + page HTML + scripts | A **Custom Code / Custom JS-HTML** element on the page |

---

## Step-by-step

### 1. Create the page
- GHL → **Sites → Funnels** (or **Websites**) → **+ New**
- Add a **Blank** step/page
- Open the page in the builder

### 2. Add the fonts (Head code)
- Funnel/Website → **Settings** (gear icon) → **Tracking Code / Custom Code**
- Find the **Head** section
- Paste the contents of `1-head-code.html`
- Save

### 3. Add the page itself
- In the page builder, drag in a **Section** → set it to full width, remove default padding
- Add a **Custom Code / Custom JS-HTML** element inside it
- Paste the **entire** contents of `2-custom-code-block.html`
- Save & Preview

> The block already includes the `<style>` and `<script>` tags, so it's self-contained — no extra setup needed for the design or animations.

### 4. ⚠️ Make the form capture leads (REQUIRED)
The built-in form does **not** submit anywhere yet. Pick one:

**Option A — Native GHL Form (recommended)**
1. GHL → **Sites → Forms → Builder** → create a form with fields:
   First Name, Last Name, Email, Goal (dropdown), Service (dropdown), Message
2. In the page builder, **delete** the `<form>...</form>` portion of the custom code
   (the whole Contact form column), and drop a GHL **Form** element in its place.
3. Style the GHL form to match: Black bg `#0A0A0A`, Gold buttons `#C9A84C`.
4. Attach a **Workflow** to the form: auto-reply email/SMS + add to a pipeline.

**Option B — Webhook (more technical)**
1. GHL → **Automation → Workflows → New → Inbound Webhook**, copy the URL.
2. In `2-custom-code-block.html`, change `<form action="#" ...>` to
   `<form action="PASTE_WEBHOOK_URL" method="POST" ...>`
3. Make sure each input has a `name=""` (they already do).

### 5. Connect your domain
- Funnel/Website → **Settings → Domain** → add/select your domain
- Set this page as the funnel's home/landing step

---

## Brand reference (for matching native GHL elements)

- **Colors:** Black `#0A0A0A` · Ebony `#1A1A1A` · Gold `#C9A84C` · Bright Gold `#E2B84A` · Ebony White `#F5F0E8`
- **Fonts:** Inter (headings, 900) · Montserrat (emphasis, 700) · Roboto (body/UI)
- **Buttons:** Gold fill, black text, uppercase, letter-spacing 0.12em

---

## Tips & gotchas

- GHL sometimes injects its own CSS reset — if spacing looks off, wrap nothing extra; the block uses scoped class names so clashes are rare.
- Custom Code elements have a size limit on some plans. If it won't save, this means you should use **Option B (native rebuild)** instead — ask and I'll write a section-by-section build spec.
- Images: replace the placeholder blocks first (see main project notes), and host images either in GHL **Media Library** or an external URL, then use those URLs in the `src=""`.
- Always **Preview** (not just the editor) — custom code renders properly only in preview/live.
