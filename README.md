# Message Coder/Decoder

A JavaScript-based encryption/decryption web application using the Theijssen code/decode principle. This is a standalone HTML application that can be used in any web browser without internet connection.

## Features

- **Text Encryption/Decryption**: Secure XOR-based encryption with Base64 encoding
- **File Encryption/Decryption**: Support for any file type (images, PDFs, documents, etc.)
- **Multi-language Support**: 7 languages (Dutch, German, English, Spanish, French, Russian, Chinese)
- **Dark/Light Theme**: Theme switching with localStorage persistence
- **Key File Generation**: Generate random 1000-2000KB key files for maximum security
- **Offline Operation**: Can run completely offline for maximum privacy

## How It Works

### Encryption Principle
The application uses XOR cipher encryption combined with Base64 encoding:

```javascript
// XOR encryption process
const xorBytes = new Uint8Array(inputBytes.length);
for (let i = 0; i < inputBytes.length; i++) {
  xorBytes[i] = inputBytes[i] ^ keyBytes[i % keyLength];
}
const encoded = btoa(xorString);
```

### File Encryption Process
1. **File Upload**: User uploads any file type (max 10MB)
2. **Byte-level XOR**: File bytes are XORed with key bytes
3. **JSON Packaging**: File metadata (type, name) and encrypted data are packaged in JSON
4. **Double Encryption**: The JSON package is encrypted again for transport safety
5. **Base64 Output**: Final encrypted output is Base64 encoded

### Security Features
- **XOR Cipher**: Byte-level XOR operation for basic obfuscation
- **Key Splitting**: Key is split across entire message length using modulo operation
- **No External Dependencies**: All processing happens client-side
- **Local Storage**: No data sent to servers

## Usage

### Text Encryption
1. Enter your message in the "Message to encrypt" field
2. Provide a secret key (or upload a key file)
3. Click "Encode" to generate encrypted output
4. Copy the encrypted text and share it securely

### File Encryption
1. Upload any file via the file upload field
2. Provide a secret key
3. Click "Encode" to generate encrypted output
4. Share the encrypted text with the recipient

### Decryption
1. Paste the encrypted text in the decoder tab
2. Enter the same key used for encryption
3. Click "Decode"
4. For files: Click "Download file" to get the decrypted file

### Key File Generation
- Click "Generate key file (1000-2000KB)" to create random ASCII key files
- Recommended for maximum security instead of short passwords
- Share key files securely via USB stick

## Security Recommendations

### Best Practices
1. **Use Key Files**: Generate 1000-2000KB key files instead of short passwords
2. **Secure Sharing**: Share key files via USB stick or other offline methods
3. **Local Operation**: Run the HTML file locally without internet connection
4. **Large Keys**: Larger key files provide better security

### Privacy Guarantee
- No internet connection required
- All processing happens in your browser
- No data sent to external servers
- Complete client-side encryption/decryption

## Technical Details

### Supported File Types
- **Images**: JPEG, PNG, GIF, BMP, WebP, SVG, TIFF
- **Documents**: PDF, DOC, DOCX, XLS, XLSX, PPT, PPTX, TXT, CSV, RTF
- **Archives**: ZIP, RAR, 7Z, TAR, GZ
- **Audio**: MP3, WAV, OGG, AAC, FLAC
- **Video**: MP4, MPEG, OGV, WebM, AVI, MOV

### Browser Compatibility
- Modern browsers with JavaScript support
- File API support for file operations
- LocalStorage for theme persistence

### File Size Limits
- Maximum file size: 10MB
- Key file generation: 1000-2000KB
- No limits on text encryption

## Deployment

### Local Usage
1. Download `encode_decode.html`
2. Open in any web browser
3. Use offline for maximum privacy

### Web Deployment
- Can be hosted on any web server
- Example: https://hodc.nl/endecrypt_zb.html

## Development

### Code Structure
- Single HTML file with embedded CSS and JavaScript
- Bootstrap 5 CSS embedded inline
- Multi-language translation system
- Theme switching with localStorage

### Customization
- Add new languages by extending the translations object
- Modify file size limits in the JavaScript code
- Extend supported file types in the MIME type mapping

## License

Open source - can be used and modified freely.

## Contributing

Feel free to submit issues and enhancement requests.