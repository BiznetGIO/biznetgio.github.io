Orcinus file with extension yaml format (.yml) required to run with orcinus tools.

Then inside your project, we already generated 3 orcinus file. 

1. `orcinus-dev.yml`: orcinus file to run on your local development
2. `orcinus.yml`: orcinus file to run on staging
3. `orcinus-production.yml`: orcinus file to run on productions


### Structure monorepo project is:
```bash
your-awesomeproject    # monorepo project
├── <generated from boilerplate code>
├── orcinus-dev.yml  
├── orcinus.yml  
├── orcinus-production.yml
└── version 
```

File `version` is not auto generated, you need to add this when ready to production. 
Change this file with version base on your history release production.
