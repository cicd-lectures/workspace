FROM mcr.microsoft.com/devcontainers/java:17

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    cowsay \
    fortune \
    fortunes \
    sl \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* \
  && su vscode -c "umask 0002 && . /usr/local/sdkman/bin/sdkman-init.sh && sdk install maven"

# Allow "funny" commands to be used from default PATH
RUN for cli in /usr/games/*;do ln -s "$cli" /usr/local/bin/;done \
  && echo "PATH=/usr/games:\$PATH" >> /etc/environment

# Use "main" as default branch for new git repositories
RUN git config --global init.defaultBranch main
