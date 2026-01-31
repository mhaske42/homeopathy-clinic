# C2H Clinic - AI Coding Agent Guidelines

## Project Overview

C2H Clinic is a responsive medical website for a homoeopathy clinic owned by Dr. Varsha Mhaske-Vichare. The site is built on the BootstrapMade Medilab template (v4.6.0) and showcases clinic services, doctor credentials, patient testimonials, and provides contact information.

**Key Sites:**

- Production: `https://c2hclinic.com`
- Contact: C2Hclinics@gmail.com | Phone: 8169438894

## Architecture & Structure

### Frontend Stack

- **HTML5** (`index.html`, `inner-page.html`) - Static pages with semantic markup
- **CSS3** (`assets/css/style.css`) - Single stylesheet with all custom styling; extends vendor components
- **Vanilla JavaScript** (`assets/js/main.js`) - No jQuery dependency (v4.0.0+ redesign)
- **Bootstrap 5.1.2** - Grid, components, utilities via CDN
- **Icon Libraries**: Bootstrap Icons, Boxicons, FontAwesome, Remix Icon

### Key Vendor Dependencies

```
assets/vendor/
├── bootstrap/          # CSS/JS framework
├── animate.css/        # CSS animations
├── bootstrap-icons/    # SVG icon fonts
├── fontawesome-free/   # Popular icons
├── glightbox/          # Lightbox gallery
├── swiper/             # Slider carousel
└── php-email-form/     # Backend form validation (requires PHP)
```

### Page Structure Pattern

Both HTML pages follow this structure:

1. **Top Bar** (`#topbar`) - Contact info, social links
2. **Header** (`#header`) - Logo, navigation, call-to-action button
3. **Hero Section** (`#hero`) - Main heading with CTA
4. **Main Content** (`#main`) - Multiple section blocks with id anchors
5. **Footer** (`#footer`) - Links, contact info, social

## Key Components & Patterns

### Navigation System

- **Smooth scroll anchors** with hash links (e.g., `href="#about"`)
- Mobile nav toggle via `.mobile-nav-toggle` button toggles `#navbar.navbar-mobile`
- Active nav state managed by `navbarlinksActive()` - adds `.active` class based on scroll position
- Navigation sections: Home, About, Services, Diet & Counselling, Success Stories, Gallery, Contact

### Content Sections (Section IDs)

- `#why-us` - 3-column value proposition
- `#about` - Doctor bio section with image/video placeholder
- `#services` - 9-column grid of medical specialties
- `#diet-conselling` - Tab-based section (Diet/Counselling tabs)
- `#success-stories` - Swiper carousel testimonials
- `#gallery` - 6-item lightbox image grid
- `#contact` - Info boxes + embedded Google Map

### JavaScript Patterns

All JS functions wrapped in IIFE with "use strict". Key utilities:

```javascript
select(selector, (all = false)); // DOM query wrapper
on(type, el, listener, (all = false)); // Event listener wrapper
onscroll(el, listener); // Scroll event wrapper
scrollto(hash); // Smooth scroll with header offset
```

**Initialized Components:**

- GLightbox for image galleries (`.glightbox` & `.galelry-lightbox` selectors)
- Swiper carousel on `.testimonials-slider` with responsive breakpoints (1-2 slides)
- Mobile nav toggle, header scroll state, back-to-top button

### Styling Conventions

- **Primary Color**: `#9bc23b` (green - health/healing theme)
- **Accent Color**: `#3291e6` (blue - hover states)
- **Font Stack**: "Open Sans" (body), "Raleway" (headings), "Poppins" (secondary)
- **Section Spacing**: Classes like `.section-bg` for alternate row styling
- **Responsive Classes**: Bootstrap grid (col-lg-_, col-md-_) + Bootstrap Icons

## Backend & Forms

### Form Integration

- `forms/contact.php` - Contact form submission
- `forms/appointment.php` - Appointment booking form
- Both require PHP-Email-Form v3+ (SMTP + validation support in PRO version)
- Free version has basic validation via `assets/vendor/php-email-form/validate.js`

**Note**: Currently forms are NOT fully functional in free tier. Production uses upgraded PRO version handling.

## Analytics & Tracking

- **Google Tag Manager** integrated: `GTM-W2NTTCL`
- Tracks page views, conversions, and user behavior
- Implementation in both HTML pages

## Development Conventions

### Naming Patterns

- **IDs for sections**: lowercase with hyphens (`#why-us`, `#diet-conselling`)
- **CSS classes**: BEM-like approach via Bootstrap utilities + custom classes
- **JS functions**: camelCase, descriptive names
- **Icon classes**: `i.bi`, `i.fas`, `i.bx`, `i.ri` based on icon library

### File Organization

- Keep all images in `assets/img/` with subdirectories (doctors/, gallery/, testimonials/)
- CSS only in `assets/css/style.css` (single file)
- JS only in `assets/js/main.js` (single file)
- Vendor libraries untouched (all CDN hosted)

## Common Tasks

### Adding a New Section

1. Add section HTML block in `#main` with unique id
2. Add nav link in `#navbar` that scrolls to new section
3. Style with existing CSS variables and Utility classes
4. Ensure mobile responsive using Bootstrap grid

### Updating Contact Info

- Top bar: `#topbar .contact-info`
- Footer: `.footer-contact`
- Replace: phone (8169438894, 7208190802), email (C2Hclinics@gmail.com)

### Modifying Testimonials Carousel

- Add/edit `.swiper-slide` divs in `.testimonials-slider`
- Swiper JS automatically handles rendering (no manual initialization needed)
- Update breakpoints in main.js if changing slide count

### Gallery Image Updates

- Add/remove `.gallery-item` divs in `#gallery .row`
- Update image paths: `assets/img/gallery/gallery-N.jpeg`
- Lightbox auto-initializes from `.galelry-lightbox` class

## Important Notes

- **No build process** - Static HTML/CSS/JS, serve directly
- **Version 4.6.0** - Bootstrap 5.1.2, no jQuery (vanilla JS only)
- **Production site**: Hosted with upgraded PRO forms handler
- **Mobile-first**: Always test responsive at 320px, 768px, 1200px breakpoints
- **SEO**: Title, meta description empty in template - update before deployment
- **Accessibility**: Use semantic HTML, ARIA labels where applicable

## References

- Template docs: https://bootstrapmade.com/medilab-free-medical-bootstrap-theme/
- License: https://bootstrapmade.com/license/
