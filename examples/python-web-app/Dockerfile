FROM ubuntu

# Set the working directory
WORKDIR /app

# Copy the requirements file and the 'devops' directory into the container
COPY requirements.txt /app
COPY devops /app

# Install Python and virtual environment-related packages
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv

# Create a virtual environment inside the container
RUN python3 -m venv /opt/venv

# Activate the virtual environment and install the requirements
RUN /opt/venv/bin/pip install --upgrade pip && \
    /opt/venv/bin/pip install -r requirements.txt

# Set the environment variable to use the virtual environment by default
ENV PATH="/opt/venv/bin:$PATH"

# Expose the necessary port (optional, but useful for network communication)
EXPOSE 8000

# Set entry point to run the application
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]





