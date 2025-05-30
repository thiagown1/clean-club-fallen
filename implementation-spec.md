# AWP Legacy Kits - Detailed Implementation Specification

## HTML STRUCTURE BLUEPRINT

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AWP Legacy Kits - Fallen Club</title>
    <style>/* Embedded CSS */</style>
</head>
<body>
    <!-- Header Section -->
    <header class="main-header">
        <div class="hero-section">
            <h1 class="legacy-title">AWP LEGACY</h1>
            <p class="hero-description">Limited Edition Collection</p>
        </div>
    </header>

    <!-- Kit 1 Section - T-shirt -->
    <section class="kit-section kit-1">
        <div class="kit-container">
            <div class="product-showcase">
                <div class="product-image">
                    <!-- T-shirt mockup -->
                </div>
                <div class="product-details">
                    <h2>Kit 1 - AWP Legacy Jersey</h2>
                    <div class="kit-items">
                        <!-- List of included items -->
                    </div>
                    <div class="pricing">
                        <!-- Price information -->
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Kit 2 Section - Hoodie -->
    <section class="kit-section kit-2">
        <div class="kit-container">
            <div class="product-showcase">
                <div class="product-image">
                    <!-- Hoodie mockup -->
                </div>
                <div class="product-details">
                    <h2>Kit 2 - AWP Legacy Hoodie</h2>
                    <div class="kit-items">
                        <!-- List of included items -->
                    </div>
                    <div class="pricing">
                        <!-- Price information -->
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Limited Edition Section -->
    <section class="limited-edition">
        <div class="certificate-showcase">
            <!-- Limited edition certificate mockup -->
        </div>
    </section>

    <!-- Campaign Information -->
    <section class="campaign-info">
        <div class="campaign-details">
            <!-- AWP Legacy campaign information -->
        </div>
    </section>

    <script>/* Embedded JavaScript */</script>
</body>
</html>
```

## CSS ARCHITECTURE

### 1. CSS Reset and Base Styles
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
}

body {
    font-family: 'Arial', sans-serif;
    background-color: #000000;
    color: #ffffff;
    line-height: 1.6;
    overflow-x: hidden;
}
```

### 2. Layout System
- **Grid System**: CSS Grid for main layout structure
- **Flexbox**: For component-level layouts
- **Container Max-width**: 1200px with padding for smaller screens

### 3. Color Variables
```css
:root {
    --primary-black: #000000;
    --accent-yellow: #FFD700;
    --pure-white: #ffffff;
    --secondary-gray: #808080;
    --dark-gray: #333333;
    --gradient-dark: linear-gradient(135deg, #000000, #1a1a1a);
}
```

### 4. Typography Scale
```css
.legacy-title {
    font-size: clamp(2rem, 5vw, 4rem);
    font-weight: bold;
    letter-spacing: 2px;
}

.section-title {
    font-size: clamp(1.5rem, 3vw, 2.5rem);
    font-weight: 600;
}

.body-text {
    font-size: clamp(0.9rem, 2vw, 1.1rem);
}
```

## COMPONENT SPECIFICATIONS

### 1. Header Component
- **Background**: Dark gradient with subtle texture
- **Title**: "AWP LEGACY" with glow effect
- **Animation**: Fade-in on load
- **Height**: 50vh minimum

### 2. Kit Showcase Components

#### Kit 1 (T-shirt)
- **Layout**: Image left, details right (desktop) / stacked (mobile)
- **Image**: Product mockup with hover zoom effect
- **Items List**: Bullet points with icons
- **Special Features**: "Limited Edition" badge

#### Kit 2 (Hoodie)
- **Layout**: Image right, details left (desktop) / stacked (mobile)
- **Styling**: Slightly different accent color to distinguish
- **Interactive**: Hover effects on product details

### 3. Limited Edition Certificate
- **Design**: Certificate mockup with golden border
- **Animation**: Subtle rotation on hover
- **Text**: "Edição Limitada" with authenticity details

### 4. Campaign Information
- **Layout**: Two-column grid
- **Content**: Campaign details and strategy information
- **Visual**: AWP-themed graphics and icons

## JAVASCRIPT FUNCTIONALITY

### 1. Smooth Scrolling Navigation
```javascript
// Smooth scroll for anchor links
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault();
        document.querySelector(this.getAttribute('href')).scrollIntoView({
            behavior: 'smooth'
        });
    });
});
```

### 2. Intersection Observer for Animations
```javascript
// Animate elements on scroll
const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
};

const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('animate-in');
        }
    });
}, observerOptions);

// Observe all animation targets
document.querySelectorAll('.animate-on-scroll').forEach(el => {
    observer.observe(el);
});
```

### 3. Interactive Product Hover Effects
```javascript
// Product image hover effects
document.querySelectorAll('.product-image').forEach(image => {
    image.addEventListener('mouseenter', function() {
        this.style.transform = 'scale(1.05)';
    });
    
    image.addEventListener('mouseleave', function() {
        this.style.transform = 'scale(1)';
    });
});
```

## RESPONSIVE DESIGN STRATEGY

### Mobile-First Approach
1. **Base styles**: Mobile (320px+)
2. **Tablet styles**: 768px+
3. **Desktop styles**: 1024px+
4. **Large desktop**: 1440px+

### Key Responsive Features
- **Typography**: Fluid scaling using clamp()
- **Images**: Responsive images with srcset if needed
- **Layout**: Grid/flexbox with breakpoint adjustments
- **Navigation**: Mobile-friendly interaction patterns

## PERFORMANCE OPTIMIZATION

### 1. CSS Optimization
- Minified inline CSS
- Critical path CSS prioritization
- Reduced specificity conflicts

### 2. Image Optimization
- WebP format with fallbacks
- Lazy loading implementation
- Proper sizing for different viewports

### 3. JavaScript Optimization
- Minimal DOM manipulation
- Event delegation where possible
- Debounced scroll events

## BROWSER COMPATIBILITY

### Target Browsers
- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+
- Mobile Safari iOS 13+
- Chrome Mobile Android 80+

### Fallbacks
- CSS Grid fallback with Flexbox
- Modern JavaScript with polyfills if needed
- Progressive enhancement approach

## INTEGRATION GUIDELINES

### Constructor Compatibility
1. **Self-contained**: All resources inline
2. **No external dependencies**: Pure HTML/CSS/JS
3. **Clean markup**: Semantic HTML structure
4. **Conflict prevention**: Namespaced CSS classes

### Testing Checklist
- [ ] HTML validation
- [ ] CSS validation
- [ ] Cross-browser testing
- [ ] Mobile responsiveness
- [ ] Performance audit
- [ ] Accessibility compliance
- [ ] Constructor integration test

## CONTENT PLACEHOLDERS

### Kit 1 Items
- Camiseta Oficial
- Card Físico do Fallen - Edição Especial
- 1 Cartela com 6 adesivos de Fallenzitos
- 1 Chave para Abrir Baú Lendário (Golden Ticket)

### Kit 2 Items
- Moletom Oficial
- Card Físico do Fallen - Edição Especial
- 2 Cartelas com 12 adesivos de Fallenzitos
- 2 Chaves para Abrir Baú Lendário (Golden Ticket)

### Campaign Text
- AWP LEGACY concept explanation
- Limited edition details
- Tribute to AWP legends
- Community celebration message

---

**Implementation Ready**: All specifications defined for immediate development start. 