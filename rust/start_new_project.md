# Start a new Rust project with cargo

To start a new project in your current path, simply run the following command in the terminal.
```bash
cargo new <project-name> --bin
```

The *--bin* is added to specify a binary target. Alternatively, *--lib* specifies a library as target.

This command will create a project folder with a simple template project, a main function, a .git folder, and a manifest (*Cargo.toml*) for the package metadata.

## Source

[https://doc.rust-lang.org/cargo/guide/creating-a-new-project.html](https://doc.rust-lang.org/cargo/guide/creating-a-new-project.html)