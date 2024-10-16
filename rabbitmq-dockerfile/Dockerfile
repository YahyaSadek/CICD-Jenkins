FROM rabbitmq:management
LABEL "Project"="Vprofile"
LABEL "Author"="Yahya"

# Expose RabbitMQ ports (5672 for messaging, 15672 for management)
EXPOSE 5672 15672

# Set default RabbitMQ environment variables for username and password
ENV RABBITMQ_DEFAULT_USER=guest
ENV RABBITMQ_DEFAULT_PASS=guest