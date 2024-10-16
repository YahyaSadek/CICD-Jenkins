FROM memcached:alpine
LABEL "Project"="Vprofile"
LABEL "Author"="Yahya"

# Expose Memcached default port
EXPOSE 11211

# Run Memcached server with default settings
CMD ["memcached", "-m", "64", "-c", "1024", "-v"]