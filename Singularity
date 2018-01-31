Bootstrap: docker
From: ubuntu:16.04
% labels
  R_Version 3.4.3

% apprun R
  exec R "${@}"

% apprun Rscript
  exec Rscript "${@}"

% runscript
  exec R "${@}"

% post
  # R version
  export R_VERSION=3.4.3

  #  Update get and set depends
  apt-get update
  apt-get install -y --no-install-recommends \
    locales

  # Config locale defaults
  echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen
  locale-gen en_US.utf8
  /usr/sbin/update-locale LANG=en_US.UTF-8
  export LC_ALL=en_US.UTF-8
  export LANG=en_US.UTF-8

  # R install
  echo "deb http://cran.r-project.org/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/r.list
  apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
  apt-get update
  apt-get install -y --no-install-recommends \
    r-base=${R_VERSION}* \
    r-base-dev=${R_VERSION}* \
    r-recommended=${R_VERSION}* \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    wget \

  # Clean up
  rm -rf /var/lib/apt/lists/*
