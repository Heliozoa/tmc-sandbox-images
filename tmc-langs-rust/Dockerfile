FROM debian:stretch

ARG RUST_CLI_URL

RUN apt-get update && \
    apt-get install -y gnupg2 && \
    ( apt-key adv --keyserver keys.gnupg.net --no-tty --recv-keys 'E19F5F87128899B192B1A2C2AD5F960A256A04AF' || \
    apt-key adv --keyserver keys.openpgp.org --no-tty --recv-keys 'E19F5F87128899B192B1A2C2AD5F960A256A04AF' || \
    apt-key adv --keyserver keyserver.ubuntu.com --no-tty --recv-keys 'E19F5F87128899B192B1A2C2AD5F960A256A04AF' ) && \
    apt-get install -y makedev locales locales-all build-essential g++ nano procps xvfb iproute2 net-tools iputils-ping curl wget rsync libxrender-dev libxtst-dev check pkg-config valgrind libxslt-dev libxml2-dev libreadline-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev libgdbm-dev ncurses-dev automake libtool bison subversion libffi-dev openssl libxrender-dev libxtst-dev xmlstarlet python2.7 python-pip python3-pip python-virtualenv maven python3-numpy python3-scipy python3-matplotlib python3-sklearn python3-skimage python3-tk moreutils python3-pandas libcurl4-openssl-dev libfreetype6 libfreetype6-dev libgl1-mesa-dev libfontconfig1-dev libx11-dev libx11-dev libxext-dev libxfixes-dev libxi-dev libxrender-dev libxcb1-dev libx11-xcb-dev libxcb-glx0-dev software-properties-common libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev zlib1g openjdk-8-jdk openjfx libcglib3-java libdouble-conversion1 libxcb-xkb1 libxcb-render-util0 libxcb-xinerama0 libxcb-image0 libxcb-keysyms1 libxcb-icccm4 libxkbcommon-x11-0 libxcb-xkb1 && \
    echo "deb https://cran.r-project.org/bin/linux/debian stretch-cran35/ >> /etc/apt/sources.list" && \
    apt-get update && \
    apt-get install -y r-base r-base-dev r-recommended && \
    useradd --create-home user && \
    rm -rf /var/lib/apt/lists/*

# Make sure to install packages locales and locales-all in addition to these
ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8

RUN bash -c "mkdir -p /pythonbuild && cd /pythonbuild && wget https://www.python.org/ftp/python/3.8.6/Python-3.8.6.tgz && tar -xzvf Python-3.8.6.tgz && cd Python-3.8.6/ && ./configure && make && make install"

# COPY ./Qt5.12 /opt/qt

# ENV PATH="/opt/qt/bin:${PATH}"

RUN Rscript -e 'install.packages(c("devtools","testthat", "httr", "curl"),repos="https://ftp.eenet.ee/pub/cran/")' && Rscript -e 'devtools::install_github("RTMC/tmc-r-tester/tmcRtestrunner")'

RUN pip3 install spacy numpy scipy matplotlib sklearn scikit-image pandas seaborn lxml matplotlib statsmodels nbformat beautifulsoup4 pillow spacy pygame

WORKDIR /app
RUN chown user /app
USER user

COPY maven-template /app/

RUN mvn -q clean compile test-compile
RUN mvn -q -U dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.6:test || true

COPY maven-template-2 /app/

RUN mvn -q clean compile test-compile
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.6:test || true

COPY maven-template-3 /app/

RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.6:test || true

COPY maven-template-4 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-5 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-6 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-7 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-8 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-9 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-10 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-11 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-12 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-13 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-14 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-15 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-16 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-17 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-18 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-19 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

COPY maven-template-20 /app
RUN mvn -q clean compile test-compile || true
RUN mvn -q dependency:resolve-plugins dependency:go-offline compile dependency:resolve-plugins
RUN mvn -q test || true
RUN mvn -q fi.helsinki.cs.tmc:tmc-maven-plugin:1.12:test || true

ENV M2_HOME="/usr/share/maven"

COPY Dockerfile /Dockerfile

ADD --chown=user ${RUST_CLI_URL} /tmc-langs-cli
RUN chmod +x /tmc-langs-cli && /tmc-langs-cli --version
ADD --chown=user tmc-run /tmc-run

USER user
