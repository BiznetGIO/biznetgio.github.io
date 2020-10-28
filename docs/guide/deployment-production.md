Production is final stage when distributed and deliver built applications going public.
Surely, all functional feature already checked and tested by product owner. 



## Production Phase
Same with staging phase deployment, on production we do with autodevops on gitlab ci.
Production pipeline will triggered _when_ project owner or deployment team accept your pull request merge to `master` branch. 

We determine with 3 stage process on production pipeline :

- build
- release
- deploy

<p align="center">
	<img src="../img/pipeline-giov2api-prod.png">
</p>

### 1. build
Jobs will build final contarize image from Dockerfile and tagged same with file `version` on your project folder.
<p align="center">
	<img src="../img/pipeline-giov2api-prod-build.png">
</p>

File `version` convention with semantic versioning 2.0.0, concern this note when you change it. 
<p align="center">
	<img src="../img/version-giov2api-prod.png">
</p>

```
example :
2 = major
1 = minor
2 = patch
```

Given a version number MAJOR.MINOR.PATCH, increment the:

    1. MAJOR version when you make incompatible API changes,
    2. MINOR version when you add functionality in a backwards compatible manner, and
    3. PATCH version when you make backwards compatible bug fixes.

Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

reference: [semantic version v2.0.0](https://semver.org/)    

!!!atention
    Please keep mind, file `version` needed to change if you ready to production, dont change if not ready deploy to production.


### 2. release
Release stage is push/upload successfull built container image to our registry image. 
<p align="center">
	<img src="../img/pipeline-giov2api-prod-release.png">
</p>

### 3. deploy
Deploying will automatically detect `orcinus-production.yml` , this will run on container production enviroment.
<p align="center">
	<img src="../img/pipeline-giov2api-prod-deploy.png">
</p>



## Production Deployment Note
1. On monorepo project, change your version on file `version`
2. On legacy repositories, tag your version and commit push to new version 
```
Given tag <release_date>-<increment_number>
example : 19092020-01
		19092020 = release date 19 September 2020 
		01 = release number 1 base on date
```
3. Assignee your project owner on your pull request to review it 
