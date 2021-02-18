---
layout: default
title: Typography guide
nav_order: 7
permalink: /typo-guide
---


# h1 (and with `inline code`)

text-alpha (and with `inline code`)
{: .text-alpha }

## h2 (and with `inline code`)

text-beta (and with `inline code`)
{: .text-beta }

### h3 (and with `inline code`)

text-gamma (and with `inline code`)
{: .text-gamma }

#### h4 (and with `inline code`)

text-delta (and with `inline code`)
{: .text-delta }

##### h5 (and with `inline code`)

text-epsilon (and with `inline code`)
{: .text-epsilon }

###### h6 (and with `inline code`)

text-zeta (and with `inline code`)
{: .text-zeta }

text-small (and with `inline code`)
{: .text-small }

text-mono (and with `inline code`)
{: .text-mono }

`/_sass/typography.scss`:

```css
h1,
.text-alpha {
  @include fs-8;
  font-weight: 300;
}

h2,
.text-beta {
  @include fs-6;
}

h3,
.text-gamma {
  @include fs-5;
}

h4,
.text-delta {
  @include fs-2;
  font-weight: 400;
  text-transform: uppercase;
  letter-spacing: 0.1em;
}

h4 code {
  text-transform: none;
}

h5,
.text-epsilon {
  @include fs-3;
  color: $grey-dk-200;
}

h6,
.text-zeta {
  @include fs-2;
  color: $grey-dk-200;
}

.text-small {
  @include fs-2;
}

.text-mono {
  font-family: $mono-font-family !important;
}
```