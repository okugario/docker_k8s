FROM golang:alpine as builder
WORKDIR /opt/Projects/ReportBoxRouterService
COPY . .
RUN go mod edit -dropreplace github.com/MrAmperage/GoWebStruct
RUN go mod tidy
RUN go mod download
RUN go build -o main .
FROM alpine:latest
WORKDIR /opt/Projects/ReportBoxRouterService
COPY . .
COPY --from=builder /opt/Projects/ReportBoxRouterService/main .
COPY --from=builder /opt/Projects/ReportBoxRouterService/Settings.json .
ENTRYPOINT ./main