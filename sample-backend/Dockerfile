# Build stage
FROM golang:1.21-alpine AS builder

# Set working directory
WORKDIR /app

# Copy go mod file
COPY go.mod ./

# Download dependencies (if any)
RUN go mod download

# Copy source code
COPY . .

# Build the application
RUN CGO_ENABLED=0 GOOS=linux go build -o sample-backend

# Final stage
FROM alpine:3.18

# Set working directory
WORKDIR /app

# Copy the binary from builder
COPY --from=builder /app/sample-backend .

# Expose port (default to 8080 if PORT env var is not set)
ENV PORT=8080
EXPOSE $PORT

# Command to run the application
CMD ["./sample-backend"]
