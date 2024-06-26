# Use debian trixie for gcc13
FROM debian:trixie as builder
 
# Set work directory
WORKDIR /download
 
# Configure build container and build llamafile
RUN mkdir out && \
    apt-get update && \
    apt-get install -y curl git gcc make && \
    git clone https://github.com/Mozilla-Ocho/llamafile.git  && \
    curl -L -o ./unzip https://cosmo.zip/pub/cosmos/bin/unzip && \
    chmod 755 unzip && mv unzip /usr/local/bin && \
    cd llamafile && make -j8 LLAMA_DISABLE_LOGS=1 && \ 
    make install PREFIX=/download/out
 
# Create container
FROM debian:stable as out
 
# Create a non-root user
RUN addgroup --gid 1000 user && \
    adduser --uid 1000 --gid 1000 --disabled-password --gecos "" user
 
# Switch to user
USER user
 
# Set working directory
WORKDIR /usr/local
 
# Copy llamafile and man pages
COPY --from=builder /download/out/bin ./bin
COPY --from=builder /download/out/share ./share/man
 
# Expose 8080 port.
EXPOSE 8080
 
# Set entrypoint.
ENTRYPOINT ["/bin/sh", "/usr/local/bin/llamafile"]
 
# Set default command.
CMD ["--server", "--host", "0.0.0.0", "-m", "/model"]