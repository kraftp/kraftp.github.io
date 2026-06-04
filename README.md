# kraftp.github.io

Peter's personal site repository.  Site hosted at [petereliaskraft.net](https://petereliaskraft.net).

Styling is [Tailwind](https://tailwindcss.com), prebuilt into a single static file at `css/tailwind.css` (no runtime CDN). The pages just link it.

## Rebuilding the CSS

After changing Tailwind classes in any `.html` file, regenerate `css/tailwind.css`. This writes a temporary config, rebuilds, and removes it — no extra files are left behind:

```bash
cat > tailwind.config.js <<'EOF'
module.exports = {
  content: ['./index.html', './blog/*.html'],
  theme: { extend: {
    fontFamily: { sans: ['Inter', 'system-ui', 'sans-serif'], display: ['Lora', 'Georgia', 'serif'] },
    colors: { accent: { DEFAULT: '#0d9488', dark: '#0f766e' } },
  } },
}
EOF
npx -y tailwindcss@3 -c tailwind.config.js -o css/tailwind.css --minify
rm tailwind.config.js
```
