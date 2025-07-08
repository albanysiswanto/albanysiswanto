<div align="center">
  <img src="img/Header.png"  />
</div>

###

![](https://visitor-badge.laobi.icu/badge?page_id=albanysiswanto.albanysiswanto)

###

###
```rust
// src/profile/intro.rs

use actix_web::{get, web, App, HttpResponse, HttpServer, Responder};
use chrono::{NaiveDate, Utc};

#[get("/intro")]
async fn intro_handler() -> impl Responder {
    let profile = {
        name: "Albany Siswanto",
        email: "albanysiswanto@yahoo.com",
    };

    let media = {
        instagram: "@albanysiswanto",
        linkedin: "@albanysiswanto",
    };

    let start_date = NaiveDate::from_ymd_opt(2018, 1, 1).unwrap();
    let now = Utc::now().naive_utc().date();
    let experience = now.year() - start_date.year();

    let langs = vec![
        ("backend", "rust:actix|javascript:bun|python"),
        ("frontend", "javascript:svelte-js,next-js"),
        ("database", "postgresql|mysql|sqlite"),
    ];
    let misc = vec![
        ("devops", "aws:ec2,rds,lightsail,s3"),
        ("tools", "git|httpie|neovim|zed"),
        ("os", "fedora-os"),
    ];

    let response = format!(
        "Profile: {} \nEmail: {}\nIG & LinkedIn: {}\nExperience: {} years\nLangs: {:?}\nMisc: {:?}",
        profile.name,
        profile.email,
        media.instagram,
        experience,
        langs,
        misc
    );

    HttpResponse::Ok().body(response)
}
```
###
