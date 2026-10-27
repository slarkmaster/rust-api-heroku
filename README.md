# Rust API Heroku

## Description

This is a simple API written in Rust using the Axum framework. It is deployed on Heroku.

## Instruction

1. Install Heroku CLI: `brew tap heroku/brew && brew install heroku`
2. Login to Heroku: `heroku login`
3. After creating the git repo with the required code & PORT is parametrized so that Heroku can assign a port to it.
4. Create a Heroku app: `heroku create`. I would recommend to also add buildpacks for the app. For Rust, it is `emk/rust`. Do like this: `heroku create --buildpack emk/rust`. This will create a Heroku app with the specified buildpack. If throws error, then just create the app and add the buildpack in the next step.
5. Create a buildpack: `heroku buildpacks:set emk/rust` for an existing application. For a new application, it can be specified while creating the app: `heroku create --buildpack emk/rust`. [Repo](https://github.com/emk/heroku-buildpack-rust).
6. Verify info: `heroku info`
7. Add heroku remote to git: `heroku git:remote -a <app-name>`. E.g. `heroku git:remote -a rust-api-heroku`
8. Add Procfile: `web: ./target/release/rust-api-heroku`. `PORT=$PORT` is not required as it is already set by the Heroku. Just need to set the `.env` & configure the code to use the env vars using `dotenv` crate & `std::env::var` function. So, you need to set the env vars in the Heroku app.
9. Although optional to mention, but do create a `rust-toolchain.toml` file. It will help Heroku to know which version of Rust to use.
10. Commit everything & push to Heroku: `git push heroku main`. For more, follow the [deployment instructions on Heroku](https://github.com/abhi3700/my_coding_toolkit/blob/main/heroku.md#deployment)
11. Verify the app: `heroku open`
12. Check logs: `heroku logs --tail`. It shows the real-time logs.

[More](https://github.com/abhi3700/my_coding_toolkit/blob/main/heroku.md)
