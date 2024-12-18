# Use a Python base image to avoid system-level restrictions
FROM python:3.12-slim

# Set the working directory inside the container
WORKDIR /app

# Copy requirements.txt first to leverage Docker's layer caching
COPY requirements.txt /app/

# Install required Python packages
RUN pip install --upgrade pip setuptools wheel && \
    pip install -r requirements.txt

# Copy the rest of the application code
COPY . /app/

# Expose the application port
EXPOSE 8000

# Define the default command to run the application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
