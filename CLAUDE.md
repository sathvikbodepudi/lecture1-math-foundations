# CLAUDE.md - AI Assistant Guide for lecture1-math-foundations

## Repository Overview

This repository contains an educational web page for **NBL 625/425 - Methods in Human Neuroimaging, Lecture 1: Mathematical Foundations of Imaging** at the University of Alabama at Birmingham.

### Purpose
A single-page, interactive HTML learning resource that covers:
- Pixels and voxels in neuroimaging
- Linear algebra fundamentals (scalars, vectors, matrices, tensors)
- Fourier transforms and their application to MRI/fMRI
- Critical evaluation of imaging methodologies

### Technology Stack
- **Pure HTML5/CSS3** - No build tools or frameworks
- **Tufte CSS** - Design based on Edward Tufte's principles
- **MathJax 3** - Mathematical equation rendering (CDN)
- **Static hosting** - Designed for GitHub Pages or local viewing
- **No dependencies** - Self-contained single HTML file

## Repository Structure

```
lecture1-math-foundations/
├── index.html                      # Main educational content (single-page app)
├── CLAUDE.md                       # This file - AI assistant guide
├── conceptual_pipeline.png         # Figure 1: Pipeline diagram
├── fourier_pairs.png              # Figure 7: Fourier transform examples
├── kspace_patterns.png            # Figure 9: K-space visualization
├── matrix_vector_eq.png           # Figure 6: Matrix-vector multiplication
├── pixels_voxels_heatmap.png      # Figure 3: Grid representations
├── pixels_voxels_person.png       # Figure 2: Cartoon examples
├── square_wave_terms.png          # Figure 8: Square wave approximations
├── svmt_infographic.png           # Figure 5: Scalar→tensor hierarchy
└── water_fat_phase.png            # Figure 10: Water-fat phase interaction
```

### File Descriptions

#### index.html
- **Lines 1-343**: Complete Tufte CSS styling system with:
  - Cream background (#fffff8) with serif typography (et-book, Palatino, Georgia)
  - Wide margin layout (55% content column, 50% margin for sidenotes)
  - Sidenotes and marginnotes for commentary and references
  - Mobile-responsive design (breakpoint at 760px)
- **Lines 345-663**: Semantic HTML content organized into sections:
  - Header with course metadata
  - Floating navigation TOC
  - 10 main content sections (how-to-use, concept-map, pixels-voxels, linear-algebra, fourier, integration, critical-evaluation, pitfalls, summary, references)
  - Footer with usage instructions

#### Image Assets
All PNG files are **static educational diagrams** referenced in the HTML:
- Figures are displayed using `.figure` CSS class containers
- Each includes figure titles and captions
- File sizes range from 32KB to 1.9MB (high-quality diagrams)

## Development Workflows

### Viewing the Page Locally
```bash
# Option 1: Open directly in browser
open index.html  # macOS
xdg-open index.html  # Linux
start index.html  # Windows

# Option 2: Serve with Python
python3 -m http.server 8000
# Then navigate to http://localhost:8000

# Option 3: Serve with Node.js
npx serve .
```

### Editing Content
1. Open `index.html` in a text editor
2. Content is organized in semantic `<section>` tags with unique IDs
3. Each section is self-contained and can be edited independently
4. Preview changes by refreshing the browser

### Adding New Images
1. Add PNG file to repository root
2. Reference in HTML: `<img src="filename.png" alt="description" />`
3. Wrap in `.figure` div for consistent styling
4. Add figure title and caption using existing patterns

### GitHub Pages Deployment
This repository is configured for GitHub Pages:
- **Branch**: Currently on `claude/add-claude-documentation-S5DfH`
- **Publishing**: Root directory serves `index.html` automatically
- **URL Pattern**: `https://[username].github.io/lecture1-math-foundations/`
- **No build step required** - Static HTML served directly

## Key Conventions for AI Assistants

### Content Editing Guidelines

#### 1. Preserve Academic Integrity
- **CRITICAL**: All content is adapted from course materials (Bolding, NBL 625/425)
- Do not remove attribution or references
- Maintain academic citations in references section (lines 1112-1152)
- Preserve instructor/student metadata in header (lines 524-532)

#### 2. Respect Visual Design System
The page uses Tufte's design principles:
- **DO NOT** change CSS variable definitions (lines 16-24) without explicit request
- Minimalist aesthetic: cream background, serif fonts, subtle colors
- Wide margins for sidenotes create breathing room and commentary space
- No heavy borders, shadows, or gradients - let content and typography shine

#### 3. Mathematical Notation
- **MathJax** is used for all equations (inline and display)
- Inline math: `<span class="inline-math">\( equation \)</span>`
- Display math: Use `\[ \]` or `$$ $$` delimiters within MathJax
- **DO NOT** replace MathJax with images or plain text
- Test equation rendering after changes

#### 4. Section Structure
Each section follows this pattern:
```html
<section id="unique-id">
  <h2>Section Title <span class="pill">Category</span></h2>
  <div class="grid-2">  <!-- Optional: for two-column layouts -->
    <div>Content</div>
    <div class="figure">Image</div>
  </div>
  <div class="callout [critical|limitation|success]">
    <strong>Label</strong><br />
    Important note
  </div>
</section>
```

#### 5. Sidenotes and Marginnotes Usage
- `.marginnote`: Unnumbered margin notes for commentary, sources, limitations
- `.sidenote`: Numbered sidenotes (auto-incrementing) for detailed asides
- Use `<span class="newthought">` for small-caps emphasis at section starts

**When to add marginnotes**:
- After introducing a concept that has limitations
- When presenting critical evaluation points
- For summarizing important insights
- For source attributions and references

#### 6. Image References
All images are in the **root directory** and follow this naming convention:
- Descriptive names with underscores: `concept_description.png`
- Referenced without path: `src="filename.png"` (not `src="./filename.png"`)
- Always include meaningful alt text for accessibility

### Common Editing Tasks

#### Adding a New Section
1. Choose a unique `id` (lowercase, hyphens)
2. Follow existing section structure pattern (h2 for section title, h3 for subsections)
3. Place between existing sections in logical flow
4. Use marginnotes for critical commentary
5. Update "Summary and Self-Check" if needed

#### Modifying Equations
```html
<!-- Inline equation -->
<p>The Fourier transform <span class="inline-math">\(X(f)\)</span> is defined as...</p>

<!-- Display equation -->
<p>
  <span class="inline-math">
    \( X(f) = \int_{-\infty}^{\infty} x(t)\, e^{-j 2\pi f t}\, dt \)
  </span>
</p>
```

#### Adding Code Blocks
```html
<div class="code-block">
# Python pseudocode
def function_name():
    return value
</div>
```

#### Creating Comparison Blocks
See pixels vs voxels comparison for pattern:
- Use `.comparison` div with two `.comparison-column` divs
- Simple grid layout without heavy styling
- Use small-caps h3 headers for comparison headings

### Responsive Design Considerations

- **Desktop** (>760px): Content 55% width, sidenotes in right margin
- **Mobile** (≤760px): Full-width content, sidenotes appear inline with background

When editing:
- Test at multiple viewport sizes
- Avoid hardcoded widths
- Use relative units (rem, em, %)
- Images automatically scale to container width
- Sidenotes/marginnotes automatically reflow on mobile

### Accessibility Best Practices

1. **Semantic HTML**: Use proper heading hierarchy (h1→h2→h3)
2. **Alt text**: Every `<img>` must have descriptive alt attribute
3. **Color contrast**: Maintain existing contrast ratios (WCAG AA compliant)
4. **Keyboard navigation**: Preserve smooth scrolling and anchor links
5. **Screen readers**: Use `aria-label` for decorative elements if needed

### Version Control Practices

#### Branch Naming
- Feature branches: `claude/add-[feature]-[session-id]`
- Current branch: `claude/add-claude-documentation-S5DfH`
- **NEVER** commit directly to main branch

#### Commit Messages
Follow this pattern:
```
Add [feature/content] to [section]

- Specific change 1
- Specific change 2
```

Examples:
- `Add critical evaluation callout to Fourier section`
- `Update matrix-vector equation figure and caption`
- `Fix responsive layout breakpoint in CSS`

#### What to Commit
- **DO commit**: HTML content changes, new images, documentation
- **DO NOT commit**: Temporary files, OS-specific files (.DS_Store)
- Git already ignores appropriate files (no .gitignore needed for this project)

### Testing Checklist

Before committing changes:
- [ ] HTML validates (no unclosed tags, proper nesting)
- [ ] All images load correctly
- [ ] MathJax equations render properly
- [ ] No console errors in browser
- [ ] Responsive layout works at 320px, 768px, 1024px, 1920px widths
- [ ] All internal anchor links work
- [ ] External links open in new tabs (`target="_blank" rel="noopener noreferrer"`)
- [ ] Content flows logically top to bottom

### Common Pitfalls to Avoid

1. **Breaking MathJax**
   - Don't remove the MathJax script tag (lines 7-12)
   - Don't escape special characters inside `\( \)` delimiters
   - Test all equations after editing

2. **Breaking Tufte Layout**
   - Don't add heavy borders, shadows, or gradients
   - Don't change the margin width ratio (55% content, 50% margin)
   - Maintain serif typography - don't switch to sans-serif
   - Keep background cream (#fffff8), not white or dark

3. **Sidenote/Marginnote Misuse**
   - Use `.marginnote` for most commentary (unnumbered)
   - Use `.sidenote` only if you need numbered references
   - Don't nest sidenotes inside other elements

4. **Image Paths**
   - All images are in root directory
   - Use relative paths: `src="image.png"` not `src="/image.png"`
   - Check that new images are committed to git

5. **Accessibility Violations**
   - Don't skip heading levels (h2→h4)
   - Ensure sufficient contrast (current palette is WCAG AA compliant)
   - Don't remove alt attributes from images

6. **Content Integrity**
   - Don't modify citations without verification
   - Don't change technical terminology without domain expertise
   - Preserve all acknowledgments and attributions

## Maintenance and Updates

### When to Update This Repository

1. **Content corrections**: Fix typos, update equations, clarify explanations
2. **New figures**: Add supplementary diagrams or visualizations
3. **Enhanced interactivity**: Add demos or interactive elements
4. **Accessibility improvements**: Better alt text, ARIA labels, contrast fixes
5. **Reference updates**: Add new citations, update links

### When NOT to Update

- Don't "modernize" for the sake of technology changes
- Don't add frameworks or build tools unless absolutely necessary
- Don't change the educational content without instructor approval
- Don't remove or replace images without replacements of equal quality

### Long-term Considerations

- **MathJax CDN**: Currently using v3 from jsDelivr (stable, widely cached)
- **Browser compatibility**: Targets modern browsers (ES6+ baseline)
- **Performance**: Single HTML file keeps load times fast
- **Archival**: Page is fully self-contained except MathJax (can be vendored if needed)

## Educational Context

### Course Information
- **Course**: NBL 625/425 - Methods in Human Neuroimaging
- **Institution**: University of Alabama at Birmingham (UAB)
- **Instructor**: Mark Bolding, PhD
- **Lecture**: 1 of series (Mathematical Foundations of Imaging)

### Learning Objectives (from content)
Students should be able to:
1. Explain the difference between pixels and voxels
2. Represent neuroimaging data as scalars, vectors, matrices, and tensors
3. Apply Fourier transform concepts to MRI reconstruction
4. Critically evaluate limitations of classical imaging methods
5. Understand modern advances (parallel imaging, compressed sensing)

### Target Audience
- Graduate students in neuroscience, biomedical engineering, psychology
- Researchers entering neuroimaging field
- Advanced undergraduates with mathematical background

## AI Assistant Behavior Guidelines

### When Helping with This Repository

1. **Understand the domain**: This is educational neuroscience content
2. **Preserve pedagogical structure**: Content order is intentional
3. **Maintain academic rigor**: Citations and attributions are critical
4. **Respect visual design**: The dark theme and gradients serve learning goals
5. **Test comprehensively**: Math rendering and responsive layout are essential

### Suggested Interaction Patterns

**User asks to add content:**
1. Identify appropriate section or create new one
2. Follow existing HTML structure patterns
3. Match writing style (formal academic, with accessible explanations)
4. Add relevant callouts for limitations/critical perspectives
5. Update TOC if new section created

**User asks to fix a bug:**
1. Reproduce the issue in context
2. Check HTML validation
3. Test MathJax rendering if equations involved
4. Verify responsive behavior
5. Test in multiple browsers if layout issue

**User asks to improve accessibility:**
1. Audit current accessibility state
2. Add/improve alt text for images
3. Check heading hierarchy
4. Verify color contrast ratios
4. Test keyboard navigation

**User asks to update references:**
1. Maintain existing citation format
2. Add to appropriate reference list category
3. Include complete bibliographic information
4. Use proper HTML entities for special characters

## Quick Reference

### CSS Class Reference
```css
/* Typography */
.newthought          /* Small-caps emphasis at section starts */
.subtitle            /* Italic subtitle below h1 */
.meta                /* Course/instructor metadata */

/* Margins and sidenotes */
.sidenote            /* Numbered sidenote in margin (auto-numbered) */
.marginnote          /* Unnumbered margin note */
.sidenote-number     /* Counter for sidenotes */

/* Figures */
figure               /* Standard figure container */
figure.fullwidth     /* Full-width figure (90% of page) */
figcaption           /* Figure captions */

/* Layout */
article              /* Main article wrapper */
section              /* Content sections (HTML element) */

/* Specialized */
.comparison          /* Two-column comparison grid */
.comparison-column   /* Individual comparison column */
.badge               /* Small inline labels */

/* Math and code */
.inline-math         /* MathJax inline math wrapper */
pre                  /* Code blocks (HTML element) */
code                 /* Inline code (HTML element) */

/* Text styles */
.epigraph            /* Pull quotes/epigraphs */
```

### Color Variables
```css
--bg: #fffff8              /* Cream background (Tufte style) */
--text: #111               /* Dark text */
--text-muted: #555         /* Muted text for captions */
--accent: #a00000          /* Dark red accent (rarely used) */
--border: #ccc             /* Light gray borders */
--margin-bg: #fefef6       /* Slight tint for mobile sidenotes */
--code-bg: #f5f5f0         /* Light beige for code blocks */
```

### Common HTML Patterns

**Section with marginnote:**
```html
<section id="section-name">
  <h2>Section Title</h2>
  <p><span class="newthought">Opening thought</span> with small caps...</p>

  <p class="marginnote"><strong>Note:</strong> Critical commentary or limitation here.</p>

  <p>Main content continues...</p>
</section>
```

**Adding a figure:**
```html
<figure>
  <img src="image.png" alt="Description" />
  <figcaption><strong>Figure X.</strong> Caption text with context.</figcaption>
</figure>

<!-- For full-width figures -->
<figure class="fullwidth">
  <img src="image.png" alt="Description" />
  <figcaption><strong>Figure X.</strong> Caption text.</figcaption>
</figure>
```

## Support and Resources

### Documentation
- **HTML5**: https://developer.mozilla.org/en-US/docs/Web/HTML
- **CSS3**: https://developer.mozilla.org/en-US/docs/Web/CSS
- **MathJax**: https://docs.mathjax.org/en/latest/

### Domain Knowledge
- **MRI Physics**: McRobbie et al., "MRI from Picture to Proton"
- **Image Processing**: Gonzalez & Woods, "Digital Image Processing"
- **Neuroimaging**: Poldrack et al., "Handbook of Functional MRI Data Analysis"

### Validation Tools
- HTML: https://validator.w3.org/
- Accessibility: https://wave.webaim.org/
- Color Contrast: https://webaim.org/resources/contrastchecker/

---

## Summary for AI Assistants

This repository is a **single-page educational website** about mathematical foundations of neuroimaging, designed with **Tufte's principles**: minimalism, wide margins for sidenotes, serif typography, and integration of figures with text.

Key requirements:
- **Respect for academic content** (citations, attributions, technical accuracy)
- **Careful handling of math rendering** (MathJax)
- **Preservation of Tufte aesthetic** (cream background, serif fonts, sidenotes, no heavy styling)
- **Accessibility awareness** (semantic HTML, alt text, contrast)

The repository is **intentionally simple** - no build tools, no frameworks, just clean HTML/CSS inspired by Edward Tufte's design philosophy. When in doubt, favor clarity and readability over ornamentation.

**Most important**: This is educational content for graduate students. Accuracy, clarity, and accessibility are paramount. When editing technical content, verify against domain literature. When changing design, ensure it serves the learning objectives and maintains the Tufte aesthetic.
