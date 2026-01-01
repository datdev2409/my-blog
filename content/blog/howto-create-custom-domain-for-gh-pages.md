---
title: "How-to: Custom domain name for GitHub Pages"
description: The how-to document to config custom domain name for static website hosted on GitHub Pages
tags:
  - How-to
---

I host my personal blog on GitHub pages (datdev2409/my-blog). The default domain name for my website will be `datdev2409.github.io/my-blog/`. Now I want to create the custom domain name `blog.datnguyen2409.tech` to point to the GitHub pages

{{% steps %}}

## DNS Provider Config

**For a subdomain (e.g., blog.datnguyen2409.tech)**

Add the CNAME record point to the `datdev2409.github.io` (replace `datdev2409` with your GitHub username)

{{< callout type="info" >}}
The CNAME record should point to the hostname. Not the URL

❌ datdev2409.github.io/my-blog

✅ datdev2409.github.io
{{< /callout >}}

I use CloudFlare as the DNS provider. The config looks like below

![alt text](image-2.png)

**For an apex domain (root domain e.g., datnguyen2409.tech)**

Apex domain do not support CNAME record
Create the `A` records that point to the GitHub Pages IP Addresses

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

## GitHub Config

Create the CNAME file with the custom domain name in the root of repository
![alt text](image-1.png)

Go to: Repository -> Settings -> Pages

- Input your custom domain in `Custom Domain` section
- Check `Enforce HTTPS` to enable HTTPS for website

![alt text](image.png)

{{% /steps %}}

## References

[GitHub Documentation: Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#about-custom-domain-configuration)
