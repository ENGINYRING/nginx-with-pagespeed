[![ENGINYRING](https://cdn.enginyring.com/img/logo_dark.png)](https://www.enginyring.com)

# nginx-with-pagespeed

Pre-compiled nginx with Google PageSpeed and Brotli modules for Debian 13 (Trixie).

## What is this?

A custom nginx build that includes:
- **nginx 1.29.1** - Latest stable
- **PageSpeed 1.14.36.1** - Automatic web optimization 
- **Brotli compression** - Superior compression
- **All standard nginx modules**

## Quick Install

```bash
# Remove existing nginx
sudo apt-get remove nginx nginx-common nginx-core nginx-full -y

# Download and install
wget https://github.com/ENGINYRING/nginx-with-pagespeed/releases/download/v1/nginx-with-pagespeed_1.29.1-1_amd64.deb
sudo dpkg -i nginx-with-pagespeed_1.29.1-1_amd64.deb
sudo apt-get install -f -y

# Start nginx
sudo systemctl start nginx
sudo systemctl enable nginx
```

## Verify Installation

```bash
nginx -V  # Check version and modules
curl -I http://localhost/  # Test web server
```

## Enable PageSpeed

```bash
sudo mv /etc/nginx/conf.d/pagespeed.conf.disabled /etc/nginx/conf.d/pagespeed.conf
sudo systemctl reload nginx
```

## Configuration Examples

### Basic PageSpeed
```nginx
pagespeed on;
pagespeed FileCachePath /var/cache/ngx_pagespeed/;
pagespeed EnableFilters rewrite_css,rewrite_javascript,rewrite_images;
```

### Brotli Compression
```nginx
brotli on;
brotli_comp_level 6;
brotli_types text/plain text/css application/javascript;
```

## Performance Benefits

- **20-40% faster** page loads with PageSpeed
- **25-35% less** bandwidth with Brotli
- **Automatic optimization** of CSS/JS/images

## Support

- Issues: [GitHub Issues](https://github.com/ENGINYRING/nginx-with-pagespeed/issues)
- Email: contact@enginyring.com

## Compatibility

- **OS**: Debian 13 (Trixie) x86_64 (maybe older, maybe newer - untested)
- **Replaces**: All standard nginx packages
- **Dependencies**: Automatically handled (in theory)

---

**Built by [ENGINYRING](https://github.com/ENGINYRING)**
