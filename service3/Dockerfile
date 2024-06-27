# Use an official Golang runtime as a parent image
FROM golang:1.16

# Set the working directory in the container
WORKDIR /go/src/app

# Copy go.mod file
COPY go.mod ./

# Check if go.sum exists and copy it if it does
RUN if [ -f go.sum ]; then cp go.sum ./; fi

# Download all dependencies. Dependencies will be cached if the go.mod and go.sum files are not changed
RUN go mod download

# Copy the rest of the application code
COPY . .

# Build the Go app
RUN go build -o /app

# Make port 8080 available to the world outside this container
EXPOSE 8080

# Run the app
CMD ["/app"]
