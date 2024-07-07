# 给第一步构建阶段取别名 builder
FROM node:14-alpine as builder
WORKDIR '/usr/app'
#COPY .npmrc .
COPY package.json .
RUN npm install
COPY . .
RUN ["npm", "run", "build"]

# FROM 指令划分构建阶段，下面是第二步
FROM nginx
# 指明文件从 builder 阶段产生的镜像中来
COPY --from=builder /usr/app/build /usr/share/nginx/html
