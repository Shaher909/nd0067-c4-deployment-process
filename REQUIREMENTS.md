# REQUIREMENTS

## Resources needed:

- An S3 bucket
- A PostgreSQL database
- Environment variables
- An Elastic Beanstalk environment

## Working locally

Run the following comamnd for every new terminal when working locally:

```
## Run this command every time you open a new terminal window
cd nd0067-c4-deployment-process-project-starter/udagram/
source set_env.sh
echo $POSTGRES_USERNAME
echo $POSTGRES_HOST
```

-- Mac/Linux users - Save all the variables above in your ~/.bashrc / ~/.profile / ~/.zshrc file and use:

```
source ~/.profile
```
