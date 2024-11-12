
# ByteBuffer Package

This package provides a `ByteBuffer` structure for handling binary data in Go.
It allows for efficient reading and writing of various data types in a binary format, making it suitable for applications such as network communication, file parsing, and low-level data manipulation.

## Features
- **Reading and Writing**: Supports reading and writing various types (e.g., `int8`, `int16`, `int32`, `float32`, `float64`, strings, bytes).
- **Bitwise Operations**: Flush and reset bit positions for efficient data handling.
- **Data Handling**: Initialize with or without data, read remaining data, and reset read/write positions.
- **Custom Stream Handling**: Manages both reading and writing streams.

## Usage

### Creating a New ByteBuffer
You can initialize a new `ByteBuffer` either empty or with existing data.

```go
buffer := NewByteBuffer() // empty buffer
bufferWithData := NewByteBufferWithData([]byte{0x01, 0x02, 0x03}) // buffer with data
```

### Writing Data
Write various data types to the buffer:
```go
buffer.WriteInt8(-1)
buffer.WriteUInt16(65535)
buffer.WriteFloat(3.14)
buffer.WriteCString("Hello")
buffer.WriteBool(true)
```

### Reading Data
Read values from the buffer using corresponding methods:
```go
bufferWithData.ResetReadPos()
value := bufferWithData.ReadInt8() // reads int8
str := bufferWithData.ReadCString() // reads null-terminated string
```

### Additional Functions
- `FlushBits()`: Flush any remaining bits to the buffer.
- `ResetReadPos()`: Reset the read position to the beginning of the buffer.
- `Clear()`: Clear the buffer contents.

### Example
```go
func main() {
	buffer := NewByteBuffer()

	// Writing to the buffer
	buffer.WriteUInt8(0xff)
	buffer.WriteCString("Hello, World!")

	// Reading from the buffer
	buffer.ResetReadPos()
	fmt.Println("Unsigned Int 8:", buffer.ReadUInt8())
	fmt.Println("String:", buffer.ReadCString())
}
```
