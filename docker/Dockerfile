ARG ubuntu_release=22.04
ARG python_version=3.11.7
FROM ubuntu:${ubuntu_release} as base
FROM python:${python_version}

# Create and activate a Python virtual environment
RUN python3 -m venv /venv
ENV PATH="/venv/bin:$PATH"

# TODO:  I think installation should be done this way, which needs requirements.txt. Maybe better to move to open-attribution repo?
# Copy only the necessary files to the working directory
#COPY . /app
# Install the requirements
#RUN pip install --no-cache-dir --upgrade -r /app/requirements.txt

RUN git clone https://github.com/OpenAttribution/open-attribution /open-attribution

# Set the working directory
WORKDIR /open-attribution

# Upgrade pip and install required Python packages
RUN pip install --upgrade pip
RUN pip install --no-cache-dir --upgrade -r /open-attribution/requirements.txt

# Expose the port the app runs on
EXPOSE 8000

# Run the app with the Litestar CLI
CMD ["litestar", "run", "--host", "0.0.0.0", "--port", "8000"]


