FROM node:6

# Home directory for Node-RED application source code.
RUN mkdir -p /usr/src/abuzerbuldozer

# User data directory, contains flows, config and nodes.
RUN mkdir /data

WORKDIR /usr/src/abuzerbuldozer

# Add node-red user so we aren't running as root.
RUN useradd --home-dir /usr/src/abuzerbuldozer --no-create-home abuzerbuldozer \
    && chown -R abuzerbuldozer:abuzerbuldozer /data \
    && chown -R abuzerbuldozer:abuzerbuldozer /usr/src/abuzerbuldozer

USER abuzerbuldozer

# package.json contains Node-RED NPM module and node dependencies
COPY package.json /usr/src/abuzerbuldozer/
RUN npm install

# User configuration directory volume
EXPOSE 1880

# Environment variable holding file path for flows configuration
ENV FLOWS=flows.json
ENV NODE_PATH=/usr/src/abuzerbuldozer/node_modules:/data/node_modules

CMD ["npm", "start", "--", "--userDir", "/data"]
