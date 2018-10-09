---
title : "프로토타입 아키텍쳐 구조
tags : [MSA]
---

### 1. 프로토타입 아키텍츠 구조 잡기

**ProTip:** Be sure to remove `/docs` and `/test` if you forked or downloaded Minimal Mistakes. These folders contain documentation and test pages for the theme and you probably don't littering up in your repo.
{: .notice--info}

**ProTip:** Be sure to remove `/docs` and `/test` if you forked or downloaded Minimal Mistakes. These folders contain documentation and test pages for the theme and you probably don't littering up in your repo.
{: .notice--info}

[<i class="fas fa-download"></i> Download Minimal Mistakes Theme](https://github.com/mmistakes/minimal-mistakes/archive/master.zip){: .btn .btn--success}

| Parameter   | Required | Description | Default |
| ---------   | -------- | ----------- | ------- |
| **toc**     | Optional | Show table of contents. (boolean) | `false` |
| **toc_label** | Optional | Table of contents title. (string) | `toc_label` in UI Text data file. |
| **toc_icon**  | Optional | Table of contents icon, displays before the title. (string) | [Font Awesome](https://fontawesome.com/icons?d=gallery&s=solid&m=free) <i class="fas fa-file-alt"></i> **file-alt** icon. Other FA icons can be used instead. |


```bash
sample-project
└── _pages/
    ├── 404.md               # custom 404 page
    ├── about.md             # about page
    └── contact.md           # contact page
```

