FROM ubuntu:latest

# Install necessary packages including Python and virtual environment tools
RUN apt-get update && apt-get install -y python3 python3-pip python3-venv

# Set up a virtual environment
WORKDIR /app
RUN python3 -m venv /app/venv

# Upgrade pip and install the required packages inside the virtual environment
COPY requirements.txt /app/requirements.txt
RUN /app/venv/bin/pip install --upgrade pip && \
    /app/venv/bin/pip install -r /app/requirements.txt

# Set the environment to use the virtual environment by default
ENV PATH="/app/venv/bin:$PATH"

# Copy application code
COPY . /app

CMD ["manage.py", "runserver", "0.0.0.0:8000"]
