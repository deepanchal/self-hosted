FROM alpine:latest

ARG tarballUrl
RUN test -n "$tarballUrl"

# add dependency to execute a golang binary with dynamic linking
RUN apk add --no-cache \
  libc6-compat \
  gcompat \
  wget

WORKDIR /dnote

# Fetching the tarball from the URL
RUN wget -Oq dnote.tar.gz "$tarballUrl" \
  && tar -xvzf dnote.tar.gz

COPY entrypoint.sh .
ENTRYPOINT ["./entrypoint.sh"]

CMD ["./dnote-server", "start"]

EXPOSE 3000
