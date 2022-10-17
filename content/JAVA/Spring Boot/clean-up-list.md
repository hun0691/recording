
---
title: "Piuh"
date: 2021-03-30T21:37:45+09:00
draft: true
---

1 Swagger Config 의미

```
@Bean
 public Docket api() {
  return new Docket(DocumentationType.SWAGGER_2)
      .select()
      .apis(RequestHandlerSelectors.any())
      .paths(PathSelectors.any())
      .build();
}
```
