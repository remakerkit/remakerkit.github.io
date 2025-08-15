# Install

### Option 1: Build from source

```bash
# Clone the repository
git clone https://github.com/remakerkit/remaker.git

# Build the project
cd remaker
go build -o remaker ./cmd/remaker

# Move the binary to your PATH (optional)
mv remaker /usr/local/bin/
```

### Option 2: Direct installation with Go

```bash
# Install directly using go install
go install github.com/remakerkit/remaker/cmd/remaker@latest
```

This will install the `remaker` binary to your `$GOPATH/bin` directory, which should be in your PATH.