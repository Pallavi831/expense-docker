#FROM node:20
# IC-1
# FROM node:20.18.3-alpine3.21 As builder
# # On top of IC-1 instruction-2 is exected , and save this as layer 2 image, IC-1 is removed
# # RUN addgroup -S expense && adduser -S expense -G expense && \
# # # create IC-2, on top of IC-2 instuction-3 is executed, and save this as layer 3 image , IC-2 is removed
# #      mkdir /opt/backend && \
# #      chown -R expense:expense /opt/backend
# WORKDIR /opt/backend
# ENV DB_HOST="mysql"
# #ENV DB_HOST="localhost"
# USER expense
# COPY package.json ./
# COPY *.js ./
# RUN npm install
# CMD ["node","index.js"]

#FROM node:20
FROM node:20.18.3-alpine3.21 As builder
WORKDIR /opt/backend
COPY package.json ./
COPY *.js ./
RUN npm install

FROM node:20.18.3-alpine3.21
RUN addgroup -S expense && adduser -S expense -G expense && \
    mkdir /opt/backend && \
    chown -R expense:expense /opt/backend
ENV DB_HOST="mysql"
WORKDIR /opt/backend
USER expense
COPY --from=builder /opt/backend /opt/backend
CMD ["node","index.js"]
    




