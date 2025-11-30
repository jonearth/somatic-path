# Feldenkrais Hong Kong Website

A bilingual (English/Traditional Chinese) Hugo website for Feldenkrais Method awareness and classes in Hong Kong.

## Project Structure

```
somatic_path/
├── archetypes/           # Content templates
├── assets/               # Processed assets (CSS, JS)
├── content/
│   ├── en/              # English content
│   │   └── home/        # Homepage sections (headless bundle)
│   └── zh-HK/           # Traditional Chinese content
│       └── home/        # Homepage sections (headless bundle)
├── layouts/
│   ├── _default/        # Default layouts
│   ├── partials/        # Reusable components
│   └── index.html       # Homepage template
├── static/
│   ├── css/             # Static CSS
│   ├── js/              # JavaScript files
│   └── images/          # Static images
├── hugo.toml            # Hugo configuration
├── tailwind.config.js   # Tailwind CSS configuration
└── README.md
```

## Getting Started

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) (v0.110.0 or later)
- [Node.js](https://nodejs.org/) (for Tailwind CSS, optional)

### Development

1. Clone the repository
2. Navigate to the project directory
3. Run Hugo development server:

```bash
hugo server -D
```

4. Open your browser to `http://localhost:1313`

### Building for Production

```bash
hugo --minify
```

The generated site will be in the `public/` directory.

## Configuration

### Site Settings

Edit `hugo.toml` to configure:
- Site title and description
- Contact information (email, phone, social links)
- Menu navigation items

### Content Management

Homepage sections are managed as a "headless bundle" in `content/{lang}/home/`. Each section is a markdown file with front matter defining the content type and data.

Section files are numbered to control order:
- `01-hero.md` - Hero section
- `02-reality.md` - Reality check / pain points
- `03-solution.md` - The Feldenkrais Method
- `04-paradox.md` - Myth vs Truth
- `05-benefits.md` - Benefits for different audiences
- `06-teacher.md` - About the teacher
- `07-services.md` - Available services
- `08-class-info.md` - What to expect in class
- `09-testimonials.md` - Student testimonials
- `10-contact.md` - Contact section

### Languages

- **Default**: Traditional Chinese (`zh-HK`)
- **Secondary**: English (`en`)

The language switcher is included in the header navigation.

## Design System

### Colors

- `felden-green`: #4A5D54 (Primary)
- `felden-sand`: #D6CFC1 (Secondary)
- `felden-terra`: #C47F68 (Accent)
- `felden-bg`: #F9F8F6 (Background)
- `felden-dark`: #2C3E36 (Dark text)
- `felden-light`: #E8E4DE (Light elements)

### Typography

**English**:
- Headings: Playfair Display
- Body: Lato

**Chinese**:
- Headings: Noto Serif TC
- Body: Noto Sans TC

## Deployment

This site is optimized for deployment on a Singapore VPS with 2GB RAM and 2 CPU cores. Hugo generates static files that can be served efficiently with minimal resources.

Recommended setup:
- Nginx or Caddy as reverse proxy
- Let's Encrypt for SSL certificates
- Hugo builds static files (no runtime required)

### Example Nginx Configuration

```nginx
server {
    listen 80;
    server_name your-domain.com;
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl http2;
    server_name your-domain.com;

    ssl_certificate /path/to/cert.pem;
    ssl_certificate_key /path/to/key.pem;

    root /var/www/feldenkrais-hk/public;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    # Cache static assets
    location ~* \.(css|js|jpg|jpeg|png|gif|ico|svg|woff|woff2)$ {
        expires 30d;
        add_header Cache-Control "public, immutable";
    }
}
```

## License

All rights reserved. Feldenkrais Method® and Awareness Through Movement® are registered service marks of the Feldenkrais Guild® of North America.
