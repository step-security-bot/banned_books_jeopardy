# Use the official Node.js image for development
FROM node:20-bookworm

# Setup PNPM
ENV PNPM_HOME="/pnpm"
ENV PATH="$PNPM_HOME:$PATH"
RUN corepack enable

# Set the working directory
WORKDIR /app

# Copy only package.json and package-lock.json to cache dependencies
COPY package.json pnpm-lock.yaml ./

# Install dependencies
RUN --mount=type=cache,id=pnpm,target=/pnpm/store pnpm install

# Expose the development server port
EXPOSE 5173

# Run the development server
CMD ["pnpm", "run", "dev", "--", "--host"]
