# elialotti-cv

This is a small personal project to automatically generate my resume from a json file. It uses python, latex and Jinja2.
You are welcome to fork this project to generate your own resume.

## How does it work

You can generate as many resumes you want, you just need to add a new json file inside resumes folder.
For example I have 2 resumes, one in English and one in Italian.

The json file must have specific fields, take as an example resumes/cv-en.json.

Once you have your json files, you can start the automatic generation with one simple command:

```sh
docker-compose up --build
```

This command will start a docker container with all the necessary latex and python depencecies. It will automatically output to /output folder one pdf file for every json file you have.

A github workflow is also available and it works this way:

- Push your changes to main branch
- A new github action will start
- It will launch the docker container and generate the pdf files
- A new release will be created, inside the artifacts you can find your pdf files

## Templates

You can change the template for each resume by changing the "template" field inside the json file.
Currently 3 templates are available: alta-en-one-col, alta-en, alta.
They are all based on [AltaCV](https://github.com/liantze/AltaCV).

alta-en-one-col is the only one currently updated, the others may need some changes for them to work correctly.

You can add more templates by adding a new folder in src/templates.
The folder name will be the same you need to use in the json file.

Inside the folder there must be a template.tex file. Inside this file you can write your template as a combination of tex and jinja2.

To make jinja2 works correctly with tex files I had to change block and variables start/end tags. Take alta-en-one-col as an example of how to build a template.

You may want to add new sections or fields. You can just add them in the json and directly reference them in the template.
