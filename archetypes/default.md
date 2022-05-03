---
title: {{with replaceRE "^\\d{4}-\\d{2}-\\d{2}-" "" .Name}}{{replace . "-" " " | title }}{{end}}
draft: true
---

