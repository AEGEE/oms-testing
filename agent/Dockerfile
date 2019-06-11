FROM jetbrains/teamcity-agent

# installing all required packaged
RUN apt-get update && apt-get install -y git sudo curl bash netcat

# installing node
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN apt-get install -y nodejs

RUN node -v
RUN npm -v