FROM mcr.microsoft.com/devcontainers/ruby:3

# Install git-lfs
RUN apt-get update && \
	apt-get install -y git-lfs && \
	git lfs install


# Copy Gemfile first for better Docker layer caching
# We copy to a temp location and install gems, which will be cached in the image
COPY Gemfile Gemfile.lock* /tmp/bundle/
WORKDIR /tmp/bundle

# Install dependencies (this layer will be cached if Gemfile doesn't change)
# Gems are installed to the system/user location, so they'll be available in the workspace
RUN bundle install
WORKDIR /workspace

