# ChallengeEU Design System & Development Guide

This guide outlines the technical stack, design tokens, and component patterns used for the ChallengeEU web interface.

---

## Technical Stack

To maintain consistency, all pages use the following lightweight stack without a build step:

* **Structure:** HTML5 (Semantic)
* **Styling:** Tailwind CSS (via CDN for rapid prototyping)
* **Icons:** Lucide Icons (via CDN)

### Quick Start Template

Every new page should start with this boilerplate:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Course Catalogue</title>
    <script src="https://unpkg.com/lucide@latest"></script>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
 <!-- Content Bolcks go in here -->
    <script>
        lucide.createIcons();
    </script>
</body>
</html>
```



### Primary Action Button(CTA)

```html

<a href="#" class="inline-flex items-center justify-center rounded-full bg-sky-600 px-6 py-3 text-sm font-semibold text-white shadow-sm hover:bg-sky-500 transition-colors">
    Button Text
    <svg data-lucide="arrow-right" class="ml-2 h-4 w-4"></svg>
</a>

```


### Category Badges

Used to tag content (e.g., "Regional Innovation" or "WP2").

```html

<div class="inline-flex items-center gap-1.5 rounded-full bg-indigo-100 px-3 py-1 text-xs font-medium text-indigo-800">
    <svg data-lucide="flask-conical" class="h-3.5 w-3.5"></svg>
    Label Text
</div>

```

# UI Component: Cards

Cards are the primary container for organizing information. In the ChallengeEU system, cards are designed to be clean, lightweight, and elevated slightly off the background using a specific combination of borders and shadows.

### The Feature Card (Horizontal)

```html

<div class="rounded-2xl border border-slate-200 bg-white p-6 shadow-sm">
    <div class="flex items-start gap-4">
        
        <div class="flex-shrink-0 flex items-center justify-center h-12 w-12 rounded-full bg-indigo-50 text-indigo-600">
            <svg data-lucide="book-open" class="h-6 w-6"></svg>
        </div>
        
        <div>
            <h3 class="text-lg font-semibold text-slate-900">Card Title</h3>
            <p class="mt-2 text-sm text-slate-600">
                Description text goes here. Keep it concise and legible.
            </p>
        </div>
    </div>
</div>


```


### The Clickable Card (Interactive)

```html

<a href="#" class="group block rounded-2xl border border-slate-200 bg-white p-6 shadow-sm hover:shadow-md hover:border-sky-200 transition-all duration-200">
    <div class="flex items-center justify-between">
        
        <div class="flex items-center gap-4">
            <div class="h-10 w-10 rounded-full bg-sky-100 flex items-center justify-center text-sky-600 group-hover:bg-sky-600 group-hover:text-white transition-colors">
                <svg data-lucide="graduation-cap" class="h-5 w-5"></svg>
            </div>
            <h3 class="font-semibold text-slate-900 group-hover:text-sky-600 transition-colors">
                Bachelor Programs
            </h3>
        </div>

        <svg data-lucide="arrow-right" class="h-5 w-5 text-slate-300 group-hover:text-sky-600 transform group-hover:translate-x-1 transition-all"></svg>
    </div>
</a>

```

### The Image Card (Vertical)

```html

<div class="overflow-hidden rounded-2xl border border-slate-200 bg-white shadow-sm hover:shadow-md transition-shadow">
    
    <div class="relative h-48 w-full bg-slate-100">
        <img 
            src="[https://images.unsplash.com/photo-1523050854058-8df90110c9f1?auto=format&fit=crop&q=80&w=800](https://images.unsplash.com/photo-1523050854058-8df90110c9f1?auto=format&fit=crop&q=80&w=800)" 
            alt="University Campus" 
            class="h-full w-full object-cover"
        >
    </div>

    <div class="p-6">
        <span class="inline-flex items-center rounded-full bg-emerald-50 px-2 py-1 text-xs font-medium text-emerald-700 ring-1 ring-inset ring-emerald-600/20 mb-3">
            New Mobility
        </span>

        <h3 class="text-lg font-semibold text-slate-900 mb-2">
            Erasmus+ Applications Open
        </h3>
        
        <p class="text-sm text-slate-600 mb-4">
            Students can now apply for the upcoming semester exchange programs across all partner universities.
        </p>

        <a href="#" class="text-sm font-semibold text-sky-600 hover:text-sky-500 inline-flex items-center">
            Read more <svg data-lucide="arrow-right" class="ml-1 h-4 w-4"></svg>
        </a>
    </div>
</div>

```
## Fusion of Tailwind with ChallengeEU Branding

Setting this code as the new inital boiler plate an attempt to fusion the desing of talwind and challengeEU branding.
*Note: this code is not currently working so it is advised not to use it.

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ChallengeEU Course Catalogue</title>

    <!-- 1. IMPORT GOOGLE FONTS -->
    <!-- FIX: Using @import inside <style> is more reliable for Elementor HTML widgets than <link> tags -->
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Alegreya:ital,wght@0,400;0,500;0,600;0,700;1,400&family=Source+Sans+3:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&display=swap');
    </style>

    <!-- 2. TAILWIND SCRIPT & CONFIGURATION -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    // Mapping your specific color palette
                    colors: {
                        orange: {
                            light: '#F16E22',
                            dark:  '#571714',
                        },
                        gray: {
                            light: '#CCCEED', // Overriding default gray-light
                            dark:  '#2A2C37', // Your dark gray
                        },
                        offwhite: '#F2F0EB',
                        pink: {
                            light: '#FAE4F1',
                            dark:  '#FBBFEC',
                        },
                        purple: {
                            light: '#D0A5EB',
                            dark:  '#621782',
                        },
                        yellow: {
                            light: '#FAEEB0',
                            dark:  '#FBD83D',
                        },
                        green: {
                            light: '#A6C3A3',
                            dark:  '#016220',
                        },
                        blue: {
                            light: '#BAD4FF',
                            dark:  '#5692FF',
                        },
                        navy: {
                            light: '#B7C9ED',
                            dark:  '#193D69',
                        }
                    },
                    // Mapping your specific fonts
                    fontFamily: {
                        // "Primary Typeface: Alegreya" -> mapped to font-serif
                        serif: ['Alegreya', 'serif'], 
                        // "Paragraphs: Source Sans 3" -> mapped to font-sans
                        sans: ['"Source Sans 3"', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    
    <!-- Load Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
</head>
<body class="font-sans text-gray-dark"> <!-- Set default font and text color -->

    <script>
        lucide.createIcons();
    </script>
</body>
</html>

```