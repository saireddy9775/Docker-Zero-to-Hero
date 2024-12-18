FROM ubuntu:latest

# Install Python and required tools
RUN apt-get update && apt-get install -y \
    python3 python3-pip python3-venv python3-full

# Set up a working directory
WORKDIR /app

# Create a virtual environment
RUN python3 -m venv /app/venv

# Upgrade pip and install dependencies
COPY requirements.txt /app/
RUN /app/venv/bin/python -m pip install --upgrade pip setuptools wheel && \
    /app/venv/bin/python -m pip install -r requirements.txt

# Set the PATH to use the virtual environment by default
ENV PATH="/app/venv/bin:$PATH"

# Copy the application code
COPY . /app/

# Command to run the application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
