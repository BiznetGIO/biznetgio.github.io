
## gitlab-ci for Production
Generate a gitlab-ci file staging with `bgn-dev` tools
```bash
  ./bgn-dev ci generate-production <your-awesome-project>
```

## Production Deployment
1. On monorepo project, change your version on file `version`
2. On legacy repositories, tag your version and commit push to new version 
