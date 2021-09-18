# matric-vm
Packer scripts for creating a matric VM

## Steps for hand-crafted AMI

1. Use the AMI's here as a starting point https://www.louisaslett.com/RStudio_AMI/; I picked `US East, Virginia`
2. Get ready to launch an instance. Ensure that your ‘security group’ settings allow incoming HTTP (port 80) traffic. Wait for the instance to actually be ready (it takes a while).
3. See https://www.louisaslett.com/RStudio_AMI/ for details for logging in
4. You will need to clean up the apt-get cache because it is messed up; I tried a bunch of things and not sure what worked.
5. `sudo apt-get install git-lfs` to install GitLFS


Other notes
1. Run `git lfs install` in each repo that needs it, and then `git lfs fetch` and `git lfs pull` to actually get the files
2. Run `sudo chown 777 -R` on any directory you want to access but can't. The sudo password is the same as for RStudio.
3. Gzip is not automatically available with the `arrow` package. You will need to do this
```r
Sys.setenv(ARROW_S3="ON")
Sys.setenv(NOT_CRAN="true")
install.packages("arrow", repos = "https://arrow-r-nightly.s3.amazonaws.com")
```
4. Use GitHub [PAT](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) for accessing repos.
5. ssh using `ubuntu` but then switch over to `rstudio` using `sudo login rstudio`. The sudo password is the same as for RStudio.

