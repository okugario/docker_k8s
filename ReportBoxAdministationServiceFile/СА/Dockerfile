FROM golang:alpine as builder
WORKDIR /opt/Projects/ReportBoxAdministartionService
COPY . .
RUN go mod edit -dropreplace github.com/MrAmperage/GoWebStruct
RUN go mod tidy
RUN go mod download
RUN go build -o main .
FROM alpine:latest
WORKDIR /opt/Projects/ReportBoxAdministartionService
COPY . .
COPY --from=builder /opt/Projects/ReportBoxAdministartionService/main .
COPY --from=builder /opt/Projects/ReportBoxAdministartionService/Settings.json .
ENTRYPOINT ./main