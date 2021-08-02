Bootstrap: docker
From: rocker/geospatial:4.1.0
Stage: build

############################################
%post
############################################

##### install packages #########
Rscript -e install.packages(c("data.table","labelled","terra","batchtools", "here", "intervalaverage", "renv"))
Rscript -e "devtools::install_github('kaufman-lab/survivaltools',ref='a9c75521fa58961e59d3c884681862f44c7683d6')"


######set user library to somewhere other than home, to avoid library conflicts with the local machine######
#this affects all R sessions, not just rstudio server sessions. 
echo "R_LIBS_USER=/pseudohome/R/packages" >> usr/local/lib/R/etc/Renviron.site  #note that /pseudohome doesn't exist. you need to bind it when running the image.


#####rstudio server defaults#########
echo "session-save-action-default=no" >> /etc/rstudio/rsession.conf #don't save workspace by default.
echo "session-quit-child-processes-on-exit=1" >> /etc/rstudio/rsession.conf #quit child processes on exit

