# Audit Phase Process Graphic

A lightweight, responsive 5-step audit process diagram built with semantic HTML, CSS (variables), Flexbox, and inline SVG arrows. No JS or frameworks.

## Files
- `index.html` — semantic HTML scaffold for the diagram
- `style.css` — responsive layout styling with CSS variables

## Quick Start (Local)
1. Open `index.html` in a browser.
2. Edit text labels directly in `index.html` if needed.

## WordPress Embed
There are two simple ways to use this in WordPress.

### Option A: Link the CSS from your media library or theme, paste HTML in a block
1. Upload `style.css` to your theme, child theme, or media library.
2. Add a "Custom HTML" block on the page and paste the following, updating the `href` to your uploaded CSS location.

```html
<link rel="stylesheet" href="/wp-content/uploads/style.css">

<section class="phase-diagram" aria-labelledby="phase-diagram-title">
	<h2 id="phase-diagram-title" class="visually-hidden">Process Phases</h2>
	<ol class="phases" role="list">
		<li class="phase-block" role="listitem" aria-label="Step 1: Risk Evaluation">
			<h3 class="phase-heading">Step 1</h3>
			<p class="phase-title">Risk Evaluation</p>
		</li>
		<li class="arrow" aria-hidden="true">
			<svg viewBox="0 0 24 24" focusable="false" aria-hidden="true" class="arrow-svg">
				<defs>
					<marker id="arrowhead" markerWidth="6" markerHeight="6" refX="5.5" refY="3" orient="auto" markerUnits="strokeWidth">
						<path d="M0,0 L6,3 L0,6 z" fill="currentColor" />
					</marker>
				</defs>
				<line x1="2" y1="12" x2="22" y2="12" stroke="currentColor" stroke-width="3" stroke-linecap="round" marker-end="url(#arrowhead)" />
			</svg>
		</li>
		<li class="phase-block" role="listitem" aria-label="Step 2: Audit Planning">
			<h3 class="phase-heading">Step 2</h3>
			<p class="phase-title">Audit Planning</p>
		</li>
		<li class="arrow" aria-hidden="true">
			<svg viewBox="0 0 24 24" focusable="false" aria-hidden="true" class="arrow-svg">
				<defs>
					<marker id="arrowhead" markerWidth="6" markerHeight="6" refX="5.5" refY="3" orient="auto" markerUnits="strokeWidth">
						<path d="M0,0 L6,3 L0,6 z" fill="currentColor" />
					</marker>
				</defs>
				<line x1="2" y1="12" x2="22" y2="12" stroke="currentColor" stroke-width="3" stroke-linecap="round" marker-end="url(#arrowhead)" />
			</svg>
		</li>
		<li class="phase-block" role="listitem" aria-label="Step 3: Audit Fieldwork">
			<h3 class="phase-heading">Step 3</h3>
			<p class="phase-title">Audit Fieldwork</p>
		</li>
		<li class="arrow" aria-hidden="true">
			<svg viewBox="0 0 24 24" focusable="false" aria-hidden="true" class="arrow-svg">
				<defs>
					<marker id="arrowhead" markerWidth="6" markerHeight="6" refX="5.5" refY="3" orient="auto" markerUnits="strokeWidth">
						<path d="M0,0 L6,3 L0,6 z" fill="currentColor" />
					</marker>
				</defs>
				<line x1="2" y1="12" x2="22" y2="12" stroke="currentColor" stroke-width="3" stroke-linecap="round" marker-end="url(#arrowhead)" />
			</svg>
		</li>
		<li class="phase-block" role="listitem" aria-label="Step 4: Audit Issuance">
			<h3 class="phase-heading">Step 4</h3>
			<p class="phase-title">Audit Issuance</p>
		</li>
		<li class="arrow" aria-hidden="true">
			<svg viewBox="0 0 24 24" focusable="false" aria-hidden="true" class="arrow-svg">
				<defs>
					<marker id="arrowhead" markerWidth="6" markerHeight="6" refX="5.5" refY="3" orient="auto" markerUnits="strokeWidth">
						<path d="M0,0 L6,3 L0,6 z" fill="currentColor" />
					</marker>
				</defs>
				<line x1="2" y1="12" x2="22" y2="12" stroke="currentColor" stroke-width="3" stroke-linecap="round" marker-end="url(#arrowhead)" />
			</svg>
		</li>
		<li class="phase-block" role="listitem" aria-label="Step 5: Closure and Follow-Up">
			<h3 class="phase-heading">Step 5</h3>
			<p class="phase-title">Closure and <br />Follow-Up</p>
		</li>
	</ol>
</section>
```

Notes:
- Some WordPress setups may block `<link>` tags in HTML blocks. If so, enqueue `style.css` in your (child) theme or add contents of `style.css` under "Appearance → Customize → Additional CSS".

### Option B: Enqueue CSS in theme/child theme
Add to your child theme's `functions.php`:

```php
add_action('wp_enqueue_scripts', function() {
	wp_enqueue_style('audit-phases', get_stylesheet_directory_uri() . '/style.css', [], null);
});
```

Then paste only the `<section ...>...</section>` HTML into a "Custom HTML" block.

## Cascade CMS Embed
1. Upload `style.css` to a public folder in Cascade (e.g., `/_internal/styles/style.css`).
2. Reference it in your page or in a site-wide header:

```html
<link rel="stylesheet" href="/_internal/styles/style.css">
```

3. Paste the same `<section class="phase-diagram">...</section>` markup into a WYSIWYG or HTML block.

## Theming via CSS Variables
You can override these in your site’s CSS:

```css
:root {
	--phase-color: #CFB991;
	--phase-text-color: #222;
	--arrow-color: #000000;
	--gap: 16px;
	--block-radius: 8px;
}
```

## Scaling to N Steps
- Duplicate a `li.phase-block` and place a `li.arrow` after it (except after the last block).
- The layout keeps all steps on one row until the mobile breakpoint (≤768px), then stacks vertically with rotated arrows.

## Accessibility
- Uses semantic elements and hidden heading for screen readers.
- Arrow elements are marked `aria-hidden`.
- Headings use `<h3>` and titles use `<p>`.

## License
MIT
