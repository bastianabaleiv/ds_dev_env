FROM rocker/rstudio:4.2.1

LABEL Bastian Aballay <bastian.aballayleiva@gmail.com>

# renv version
ENV RENV_VERSION 0.15.5

# Dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
  curl \
  nano \
  libcurl4-gnutls-dev \ 
  libxml2-dev \
  libxt6 \
  fonts-firacode && \
  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install RStudio theme
RUN curl https://raw.githubusercontent.com/gadenbuie/rsthemes/main/inst/themes/night-owl.rstheme > /etc/rstudio/themes/night-owlish.rstheme

# Copy RStudio preferences file
COPY rstudio-prefs.json /etc/rstudio

# Install remotes & renv packages
RUN R -e "install.packages('remotes', repos = c(CRAN = 'https://cloud.r-project.org'))"
RUN R -e "remotes::install_github('rstudio/renv@${RENV_VERSION}')"