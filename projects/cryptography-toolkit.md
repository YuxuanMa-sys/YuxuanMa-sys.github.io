---
layout: default
title: "CryptoToolkit: Comprehensive Cryptography Implementation"
permalink: /projects/cryptography-toolkit.html
---

<div class="crypto-project">
  <header class="crypto-header">
    <div class="crypto-header-overlay"></div>
    <div class="crypto-header-content">
      <h1>CryptoToolkit</h1>
      <div class="crypto-subtitle">Comprehensive Cryptography Implementation</div>
      <div class="crypto-metadata">
        <div class="crypto-metadata-item">
          <div class="crypto-metadata-icon">
            <svg viewBox="0 0 24 24" width="20" height="20">
              <path fill="currentColor" d="M19,4H18V2H16V4H8V2H6V4H5A2,2 0 0,0 3,6V20A2,2 0 0,0 5,22H19A2,2 0 0,0 21,20V6A2,2 0 0,0 19,4M19,20H5V10H19V20M19,8H5V6H19V8Z" />
            </svg>
          </div>
          <div class="crypto-metadata-text">2023 – Present</div>
        </div>
        <div class="crypto-metadata-item">
          <div class="crypto-metadata-icon">
            <svg viewBox="0 0 24 24" width="20" height="20">
              <path fill="currentColor" d="M12,3L1,9L12,15L21,10.09V17H23V9M5,13.18V17.18L12,21L19,17.18V13.18L12,17L5,13.18Z" />
            </svg>
          </div>
          <div class="crypto-metadata-text">Personal Project</div>
        </div>
      </div>
    </div>
  </header>

  <div class="crypto-intro">
    <div class="crypto-intro-content">
      <p>CryptoToolkit is a comprehensive implementation of various cryptographic primitives and techniques, designed as both a practical tool and an educational resource. The project demonstrates modern cryptographic approaches including symmetric and asymmetric encryption, digital signatures, secure key derivation, and file encryption systems.</p>
    </div>
    <div class="crypto-intro-visual">
      <div class="crypto-visual-container">
        <div class="crypto-animation">
          <div class="crypto-lock">
            <div class="crypto-lock-body">
              <div class="crypto-lock-hole"></div>
            </div>
            <div class="crypto-lock-shackle"></div>
          </div>
          <div class="crypto-bits">
            <div class="crypto-bit"></div>
            <div class="crypto-bit"></div>
            <div class="crypto-bit"></div>
            <div class="crypto-bit"></div>
            <div class="crypto-bit"></div>
            <div class="crypto-bit"></div>
            <div class="crypto-bit"></div>
            <div class="crypto-bit"></div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="crypto-section">
    <h2>Core Components</h2>
    
    <div class="crypto-component-grid">
      <div class="crypto-component">
        <div class="crypto-component-icon">
          <svg viewBox="0 0 24 24" width="28" height="28">
            <path fill="currentColor" d="M18,8H17V6A5,5 0 0,0 12,1A5,5 0 0,0 7,6V8H6A2,2 0 0,0 4,10V20A2,2 0 0,0 6,22H18A2,2 0 0,0 20,20V10A2,2 0 0,0 18,8M8.9,6C8.9,4.29 10.29,2.9 12,2.9C13.71,2.9 15.1,4.29 15.1,6V8H8.9V6M16,16H13V19H11V16H8V14H11V11H13V14H16V16Z" />
          </svg>
        </div>
        <h3>Symmetric Encryption</h3>
        <p>Implementations of AES and ChaCha20 ciphers for secure, fast encryption of data with a shared key. Includes authenticated encryption modes for data integrity.</p>
        <div class="crypto-code-block">
          <pre><code>$ python crypto_toolkit.py symmetric-encrypt \
  --algorithm aes \
  --input "Hello, World!" \
  --password "secure_password"</code></pre>
        </div>
      </div>
      
      <div class="crypto-component">
        <div class="crypto-component-icon">
          <svg viewBox="0 0 24 24" width="28" height="28">
            <path fill="currentColor" d="M9,6A3,3 0 0,1 12,3A3,3 0 0,1 15,6V11A3,3 0 0,1 12,14A3,3 0 0,1 9,11V6M12,1A5,5 0 0,0 7,6V11A5,5 0 0,0 12,16A5,5 0 0,0 17,11V6A5,5 0 0,0 12,1M1,18V20A4,4 0 0,0 5,24H19A4,4 0 0,0 23,20V18H21V20A2,2 0 0,1 19,22H5A2,2 0 0,1 3,20V18H1Z" />
          </svg>
        </div>
        <h3>Asymmetric Encryption</h3>
        <p>RSA implementation for public-key cryptography, enabling secure communication without shared secrets. Includes key generation, encryption, and decryption functions.</p>
        <div class="crypto-code-block">
          <pre><code>$ python crypto_toolkit.py generate-keypair \
  --output keys/

$ python crypto_toolkit.py asymmetric-encrypt \
  --key keys/public_key.pem \
  --input "Secret message"</code></pre>
        </div>
      </div>
      
      <div class="crypto-component">
        <div class="crypto-component-icon">
          <svg viewBox="0 0 24 24" width="28" height="28">
            <path fill="currentColor" d="M17.81,4.47C17.73,4.47 17.65,4.45 17.58,4.41C15.66,3.42 14,3 12,3C10.03,3 8.15,3.47 6.44,4.41C6.2,4.54 5.9,4.45 5.76,4.21C5.63,3.97 5.72,3.66 5.96,3.53C7.82,2.5 9.86,2 12,2C14.14,2 16,2.47 18.04,3.5C18.29,3.65 18.38,3.95 18.25,4.19C18.16,4.37 17.99,4.47 17.81,4.47M3.5,9.72C3.4,9.72 3.3,9.69 3.21,9.63C3,9.47 2.93,9.16 3.09,8.93C4.08,7.53 5.34,6.43 6.84,5.66C10,4.04 14,4.03 17.15,5.65C18.65,6.42 19.91,7.5 20.9,8.9C21.06,9.12 21,9.44 20.78,9.6C20.55,9.76 20.24,9.71 20.08,9.5C19.18,8.22 18.04,7.23 16.69,6.54C13.82,5.07 10.15,5.07 7.29,6.55C5.93,7.25 4.79,8.25 3.89,9.5C3.81,9.65 3.66,9.72 3.5,9.72M9.75,21.79C9.62,21.79 9.5,21.74 9.4,21.64C8.53,20.77 8.06,20.21 7.39,19C6.7,17.77 6.34,16.27 6.34,14.66C6.34,11.69 8.88,9.27 12,9.27C15.12,9.27 17.66,11.69 17.66,14.66A0.5,0.5 0 0,1 17.16,15.16A0.5,0.5 0 0,1 16.66,14.66C16.66,12.24 14.57,10.27 12,10.27C9.43,10.27 7.34,12.24 7.34,14.66C7.34,16.1 7.66,17.43 8.27,18.5C8.91,19.66 9.35,20.15 10.12,20.93C10.31,21.13 10.31,21.44 10.12,21.64C10,21.74 9.88,21.79 9.75,21.79M16.92,19.94C15.73,19.94 14.68,19.64 13.82,19.05C12.33,18.04 11.44,16.4 11.44,14.66A0.5,0.5 0 0,1 11.94,14.16A0.5,0.5 0 0,1 12.44,14.66C12.44,16.07 13.16,17.4 14.38,18.22C15.09,18.7 15.92,18.93 16.92,18.93C17.16,18.93 17.56,18.9 17.96,18.83C18.23,18.78 18.5,18.96 18.54,19.24C18.59,19.5 18.41,19.77 18.13,19.82C17.56,19.93 17.06,19.94 16.92,19.94M14.91,22C14.87,22 14.82,22 14.78,22C13.19,21.54 12.15,20.95 11.06,19.88C9.66,18.5 8.89,16.64 8.89,14.66C8.89,13.04 10.27,11.72 11.97,11.72C13.67,11.72 15.05,13.04 15.05,14.66C15.05,15.73 16,16.6 17.13,16.6C18.28,16.6 19.21,15.73 19.21,14.66C19.21,10.89 15.96,7.83 11.96,7.83C9.12,7.83 6.5,9.41 5.35,11.86C4.96,12.67 4.76,13.62 4.76,14.66C4.76,15.44 4.83,16.67 5.43,18.27C5.53,18.53 5.4,18.82 5.14,18.91C4.88,19 4.59,18.87 4.5,18.62C4,17.31 3.77,16 3.77,14.66C3.77,13.46 4,12.37 4.45,11.42C5.78,8.63 8.73,6.82 11.96,6.82C16.5,6.82 20.21,10.33 20.21,14.65C20.21,16.27 18.83,17.59 17.13,17.59C15.43,17.59 14.05,16.27 14.05,14.65C14.05,13.58 13.12,12.71 11.97,12.71C10.82,12.71 9.89,13.58 9.89,14.65C9.89,16.36 10.55,17.96 11.76,19.16C12.71,20.1 13.62,20.62 15.03,21C15.3,21.08 15.45,21.36 15.38,21.62C15.33,21.85 15.12,22 14.91,22Z" />
          </svg>
        </div>
        <h3>Digital Signatures</h3>
        <p>Implementation of digital signature algorithms for message authentication and non-repudiation. Ensures data integrity and verifies the sender's identity.</p>
        <div class="crypto-code-block">
          <pre><code>$ python crypto_toolkit.py sign \
  --key keys/private_key.pem \
  --input "Message to sign"

$ python crypto_toolkit.py verify \
  --key keys/public_key.pem \
  --input "Message to sign" \
  --signature &lt;signature&gt;</code></pre>
        </div>
      </div>
      
      <div class="crypto-component">
        <div class="crypto-component-icon">
          <svg viewBox="0 0 24 24" width="28" height="28">
            <path fill="currentColor" d="M7,14A2,2 0 0,1 5,12A2,2 0 0,1 7,10A2,2 0 0,1 9,12A2,2 0 0,1 7,14M12.65,10C11.83,7.67 9.61,6 7,6A6,6 0 0,0 1,12A6,6 0 0,0 7,18C9.61,18 11.83,16.33 12.65,14H17V18H21V14H23V10H12.65Z" />
          </svg>
        </div>
        <h3>Key Derivation</h3>
        <p>Secure key derivation functions (KDF) for generating cryptographic keys from passwords or shared secrets. Uses industry-standard approaches like PBKDF2 and Argon2.</p>
        <div class="crypto-code-block">
          <pre><code># Internally used for password-based operations
key = pbkdf2_hmac(
    'sha256', 
    password.encode('utf-8'), 
    salt, 
    iterations=100000, 
    dklen=32
)</code></pre>
        </div>
      </div>

      <div class="crypto-component">
        <div class="crypto-component-icon">
          <svg viewBox="0 0 24 24" width="28" height="28">
            <path fill="currentColor" d="M14,2H6A2,2 0 0,0 4,4V20A2,2 0 0,0 6,22H18A2,2 0 0,0 20,20V8L14,2M18,20H6V4H13V9H18V20M10,19L11.5,17.5L9.5,15.5L11.5,13.5L10,12L7,15L10,19M15,15.5L13,13.5L14.5,12L17.5,15L14.5,18L13,16.5L15,15.5Z" />
          </svg>
        </div>
        <h3>File Encryption</h3>
        <p>Tools for securely encrypting and decrypting files with password protection. Includes integrity checks to detect tampering and corruption.</p>
        <div class="crypto-code-block">
          <pre><code>$ python crypto_toolkit.py encrypt-file \
  --input file.txt \
  --output file.enc \
  --password "secure_password"

$ python crypto_toolkit.py decrypt-file \
  --input file.enc \
  --output file.txt \
  --password "secure_password"</code></pre>
        </div>
      </div>

      <div class="crypto-component">
        <div class="crypto-component-icon">
          <svg viewBox="0 0 24 24" width="28" height="28">
            <path fill="currentColor" d="M12,17A2,2 0 0,0 14,15C14,13.89 13.1,13 12,13A2,2 0 0,0 10,15A2,2 0 0,0 12,17M18,8A2,2 0 0,1 20,10V20A2,2 0 0,1 18,22H6A2,2 0 0,1 4,20V10C4,8.89 4.9,8 6,8H7V6A5,5 0 0,1 12,1A5,5 0 0,1 17,6V8H18M12,3A3,3 0 0,0 9,6V8H15V6A3,3 0 0,0 12,3Z" />
          </svg>
        </div>
        <h3>Blockchain Fundamentals</h3>
        <p>Simple blockchain implementation demonstrating cryptographic principles underlying distributed ledger technologies. Includes proof-of-work concept and chain validation.</p>
        <div class="crypto-code-block">
          <pre><code>$ python simple_blockchain.py create \
  --data "Genesis block data"

$ python simple_blockchain.py add \
  --data "Transaction data"

$ python simple_blockchain.py verify</code></pre>
        </div>
      </div>

    </div>
  </div>

  <div class="crypto-section">
    <h2>Technical Architecture</h2>
    
    <div class="crypto-architecture">
      <div class="crypto-architecture-diagram">
        <div class="crypto-diagram-container">
          <div class="crypto-module crypto-module-core">
            <span>Core Cryptography Engine</span>
          </div>
          <div class="crypto-module-connections">
            <div class="crypto-module crypto-module-1">
              <span>Symmetric</span>
            </div>
            <div class="crypto-module crypto-module-2">
              <span>Asymmetric</span>
            </div>
            <div class="crypto-module crypto-module-3">
              <span>Hashing</span>
            </div>
            <div class="crypto-module crypto-module-4">
              <span>Key Management</span>
            </div>
          </div>
          <div class="crypto-module-interfaces">
            <div class="crypto-module crypto-module-cli">
              <span>CLI Interface</span>
            </div>
            <div class="crypto-module crypto-module-api">
              <span>API Layer</span>
            </div>
          </div>
          <div class="crypto-module crypto-module-applications">
            <span>Applications (Secure Messaging, Blockchain, File Encryption)</span>
          </div>
        </div>
      </div>
      
      <div class="crypto-architecture-description">
        <h3>Modular Design</h3>
        <p>The toolkit follows a modular architecture that separates concerns between cryptographic primitives, key management, and application interfaces. This design enables flexibility, testability, and security isolation.</p>
        
        <h3>Core Components</h3>
        <ul class="crypto-component-list">
          <li><strong>Cryptography Engine:</strong> Centralized implementation of cryptographic algorithms with consistent interfaces</li>
          <li><strong>Key Management:</strong> Secure generation, storage, and derivation of cryptographic keys</li>
          <li><strong>CLI Interface:</strong> Command-line tools for easy integration with scripts and workflows</li>
          <li><strong>Utility Library:</strong> Helper functions for common operations like encoding, padding, and validation</li>
        </ul>
        
        <h3>Security Considerations</h3>
        <p>The implementation follows cryptographic best practices, including:</p>
        <ul class="crypto-component-list">
          <li>Constant-time operations to prevent timing attacks</li>
          <li>Secure random number generation using system entropy</li>
          <li>Memory zeroization after cryptographic operations</li>
          <li>Integrity verification for encrypted data</li>
          <li>Defense against common implementation vulnerabilities</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="crypto-section">
    <h2>Implementation Examples</h2>
    
    <div class="crypto-tabs">
      <div class="crypto-tab-header">
        <button class="crypto-tab-btn active" data-tab="symmetric">Symmetric Encryption</button>
        <button class="crypto-tab-btn" data-tab="asymmetric">Asymmetric Encryption</button>
        <button class="crypto-tab-btn" data-tab="blockchain">Simple Blockchain</button>
      </div>
      
      <div class="crypto-tab-content active" id="symmetric">
        <div class="crypto-code-snippet">
          <div class="crypto-code-header">
            <span>Implementation of AES encryption with authentication</span>
          </div>
          <pre><code>def encrypt_aes_gcm(data, password, associated_data=None):
    """
    Encrypts data using AES-GCM with a key derived from the password.
    Returns a dict with salt, nonce, ciphertext, and tag.
    """
    if isinstance(data, str):
        data = data.encode('utf-8')
    
    # Generate salt and derive key
    salt = get_random_bytes(16)
    key = derive_key(password, salt)
    
    # Create cipher with random nonce
    nonce = get_random_bytes(12)
    cipher = AES.new(key, AES.MODE_GCM, nonce=nonce)
    
    # Add associated data if provided
    if associated_data:
        cipher.update(associated_data)
    
    # Encrypt and get authentication tag
    ciphertext, tag = cipher.encrypt_and_digest(data)
    
    # Return components needed for decryption
    return {
        'salt': b64encode(salt).decode('utf-8'),
        'nonce': b64encode(nonce).decode('utf-8'),
        'ciphertext': b64encode(ciphertext).decode('utf-8'),
        'tag': b64encode(tag).decode('utf-8')
    }</code></pre>
        </div>
      </div>
      
      <div class="crypto-tab-content" id="asymmetric">
        <div class="crypto-code-snippet">
          <div class="crypto-code-header">
            <span>Implementation of RSA key generation and encryption</span>
          </div>
          <pre><code>def generate_rsa_keypair(key_size=2048):
    """
    Generates an RSA key pair with the specified key size.
    Returns private and public key PEM strings.
    """
    # Generate key pair
    key = RSA.generate(key_size)
    
    # Export private key in PEM format
    private_key = key.export_key()
    
    # Export public key in PEM format
    public_key = key.publickey().export_key()
    
    return private_key, public_key

def encrypt_rsa(data, public_key_pem):
    """
    Encrypts data using RSA public key.
    Uses PKCS#1 OAEP padding for security.
    """
    # Import the public key
    public_key = RSA.import_key(public_key_pem)
    
    # Create cipher with OAEP padding
    cipher = PKCS1_OAEP.new(public_key)
    
    # Convert string to bytes if needed
    if isinstance(data, str):
        data = data.encode('utf-8')
    
    # Encrypt the data
    ciphertext = cipher.encrypt(data)
    
    # Return base64 encoded ciphertext
    return b64encode(ciphertext).decode('utf-8')</code></pre>
        </div>
      </div>
      
      <div class="crypto-tab-content" id="blockchain">
        <div class="crypto-code-snippet">
          <div class="crypto-code-header">
            <span>Simple blockchain implementation with proof-of-work</span>
          </div>
          <pre><code>class Block:
    def __init__(self, index, timestamp, data, previous_hash):
        self.index = index
        self.timestamp = timestamp
        self.data = data
        self.previous_hash = previous_hash
        self.nonce = 0
        self.hash = self.calculate_hash()
    
    def calculate_hash(self):
        block_string = f"{self.index}{self.timestamp}{self.data}{self.previous_hash}{self.nonce}"
        return hashlib.sha256(block_string.encode()).hexdigest()
    
    def mine_block(self, difficulty):
        target = '0' * difficulty
        while self.hash[:difficulty] != target:
            self.nonce += 1
            self.hash = self.calculate_hash()
        print(f"Block mined: {self.hash}")

class Blockchain:
    def __init__(self, difficulty=4):
        self.chain = [self.create_genesis_block()]
        self.difficulty = difficulty
    
    def create_genesis_block(self):
        return Block(0, datetime.now(), "Genesis Block", "0")
    
    def get_latest_block(self):
        return self.chain[-1]
    
    def add_block(self, data):
        latest_block = self.get_latest_block()
        new_block = Block(
            len(self.chain),
            datetime.now(),
            data,
            latest_block.hash
        )
        new_block.mine_block(self.difficulty)
        self.chain.append(new_block)
    
    def is_chain_valid(self):
        for i in range(1, len(self.chain)):
            current_block = self.chain[i]
            previous_block = self.chain[i-1]
            
            # Verify current block hash
            if current_block.hash != current_block.calculate_hash():
                return False
            
            # Verify chain linkage
            if current_block.previous_hash != previous_block.hash:
                return False
        
        return True</code></pre>
        </div>
      </div>
    </div>
  </div>

  <div class="crypto-section">
    <h2>Security Considerations & Best Practices</h2>
    
    <div class="crypto-security-grid">
      <div class="crypto-security-item">
        <div class="crypto-security-icon">
          <svg viewBox="0 0 24 24" width="24" height="24">
            <path fill="currentColor" d="M12,1L3,5V11C3,16.55 6.84,21.74 12,23C17.16,21.74 21,16.55 21,11V5L12,1M12,5A3,3 0 0,1 15,8A3,3 0 0,1 12,11A3,3 0 0,1 9,8A3,3 0 0,1 12,5M17.13,17C15.92,18.85 14.11,20.24 12,20.92C9.89,20.24 8.08,18.85 6.87,17C6.53,16.5 6.24,16 6,15.47C6,13.82 8.71,12.47 12,12.47C15.29,12.47 18,13.79 18,15.47C17.76,16 17.47,16.5 17.13,17Z" />
          </svg>
        </div>
        <h3>Key Management</h3>
        <p>Secure key management is critical for cryptographic systems. This toolkit implements proper key derivation, secure storage mechanisms, and memory safety to protect sensitive key material.</p>
      </div>
      
      <div class="crypto-security-item">
        <div class="crypto-security-icon">
          <svg viewBox="0 0 24 24" width="24" height="24">
            <path fill="currentColor" d="M10,17L6,13L7.41,11.59L10,14.17L16.59,7.58L18,9M12,1A5,5 0 0,0 7,6V11A5,5 0 0,0 12,16A5,5 0 0,0 17,11V6A5,5 0 0,0 12,1M1,18V20A4,4 0 0,0 5,24H19A4,4 0 0,0 23,20V18H21V20A2,2 0 0,1 19,22H5A2,2 0 0,1 3,20V18H1Z" />
          </svg>
        </div>
        <h3>Authenticated Encryption</h3>
        <p>All encryption operations use authenticated modes (like GCM) to provide both confidentiality and integrity protection. This prevents tampering and related attacks on encrypted data.</p>
      </div>
      
      <div class="crypto-security-item">
        <div class="crypto-security-icon">
          <svg viewBox="0 0 24 24" width="24" height="24">
            <path fill="currentColor" d="M12,12H19C18.47,16.11 15.72,19.78 12,20.92V12H5V6.3L12,3.19M12,1L3,5V11C3,16.55 6.84,21.74 12,23C17.16,21.74 21,16.55 21,11V5L12,1Z" />
          </svg>
        </div>
        <h3>Side-Channel Defense</h3>
        <p>Implementations are designed to resist side-channel attacks by using constant-time operations for sensitive comparisons and operations on secret data.</p>
      </div>
      
      <div class="crypto-security-item">
        <div class="crypto-security-icon">
          <svg viewBox="0 0 24 24" width="24" height="24">
            <path fill="currentColor" d="M12,12H19C18.47,16.11 15.72,19.78 12,20.92V12H5V6.3L12,3.19M12,1L3,5V11C3,16.55 6.84,21.74 12,23C17.16,21.74 21,16.55 21,11V5L12,1Z" />
          </svg>
        </div>
        <h3>Crypto Agility</h3>
        <p>The toolkit architecture supports algorithm agility, allowing for easy updates when vulnerabilities are discovered or when stronger algorithms become available.</p>
      </div>
    </div>
    
    <div class="crypto-warning">
      <svg viewBox="0 0 24 24" width="28" height="28">
        <path fill="currentColor" d="M13,13H11V7H13M13,17H11V15H13M12,2A10,10 0 0,0 2,12A10,10 0 0,0 12,22A10,10 0 0,0 22,12A10,10 0 0,0 12,2Z" />
      </svg>
      <div class="crypto-warning-content">
        <h3>Educational Purpose</h3>
        <p>This toolkit is primarily designed for educational purposes to demonstrate cryptographic concepts. For production systems, consider using established libraries and frameworks with proper security auditing. Always consult cryptography experts when implementing security-critical systems.</p>
      </div>
    </div>
  </div>

  <div class="crypto-section">
    <h2>Skills & Technologies</h2>
    
    <div class="crypto-skills-grid">
      <div class="crypto-skill-category">
        <h3>Cryptography</h3>
        <ul>
          <li>Symmetric Encryption (AES, ChaCha20)</li>
          <li>Public Key Cryptography (RSA)</li>
          <li>Secure Hashing Algorithms</li>
          <li>Key Derivation Functions</li>
          <li>Digital Signatures</li>
        </ul>
      </div>
      
      <div class="crypto-skill-category">
        <h3>Software Development</h3>
        <ul>
          <li>Python</li>
          <li>Object-Oriented Design</li>
          <li>Command-Line Interfaces</li>
          <li>Test-Driven Development</li>
          <li>Security-Focused Coding</li>
        </ul>
      </div>
      
      <div class="crypto-skill-category">
        <h3>Tools & Libraries</h3>
        <ul>
          <li>PyCryptodome</li>
          <li>Hashlib</li>
          <li>Argon2</li>
          <li>Pytest</li>
          <li>Argparse</li>
        </ul>
      </div>
      
      <div class="crypto-skill-category">
        <h3>Security Concepts</h3>
        <ul>
          <li>Side-Channel Attack Prevention</li>
          <li>Secure Random Number Generation</li>
          <li>Blockchain Fundamentals</li>
          <li>Zero-Knowledge Proofs</li>
          <li>Memory Safety</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="crypto-resources">
    <a href="https://github.com/YuxuanMa-sys/Cryptography" class="crypto-resource-link" target="_blank">
      <div class="crypto-resource-icon">
        <svg viewBox="0 0 24 24" width="36" height="36">
          <path fill="currentColor" d="M12,2A10,10 0 0,0 2,12C2,16.42 4.87,20.17 8.84,21.5C9.34,21.58 9.5,21.27 9.5,21C9.5,20.77 9.5,20.14 9.5,19.31C6.73,19.91 6.14,17.97 6.14,17.97C5.68,16.81 5.03,16.5 5.03,16.5C4.12,15.88 5.1,15.9 5.1,15.9C6.1,15.97 6.63,16.93 6.63,16.93C7.5,18.45 8.97,18 9.54,17.76C9.63,17.11 9.89,16.67 10.17,16.42C7.95,16.17 5.62,15.31 5.62,11.5C5.62,10.39 6,9.5 6.65,8.79C6.55,8.54 6.2,7.5 6.75,6.15C6.75,6.15 7.59,5.88 9.5,7.17C10.29,6.95 11.15,6.84 12,6.84C12.85,6.84 13.71,6.95 14.5,7.17C16.41,5.88 17.25,6.15 17.25,6.15C17.8,7.5 17.45,8.54 17.35,8.79C18,9.5 18.38,10.39 18.38,11.5C18.38,15.32 16.04,16.16 13.81,16.41C14.17,16.72 14.5,17.33 14.5,18.26C14.5,19.6 14.5,20.68 14.5,21C14.5,21.27 14.66,21.59 15.17,21.5C19.14,20.16 22,16.42 22,12A10,10 0 0,0 12,2Z" />
        </svg>
      </div>
      <div class="crypto-resource-content">
        <h3>GitHub Repository</h3>
        <p>Access the full source code, documentation, and examples</p>
      </div>
    </a>
  </div>
</div>

<style>
/* Cryptography Project Styling */
.crypto-project {
  font-family: 'Inter', 'Roboto', system-ui, -apple-system, sans-serif;
  color: #333;
  max-width: 1200px;
  margin: 0 auto;
  line-height: 1.6;
}

/* Header Styling */
.crypto-header {
  position: relative;
  padding: 4rem 2rem;
  margin-bottom: 3rem;
  overflow: hidden;
  text-align: center;
}

.crypto-header-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
  z-index: -1;
}

.crypto-header-overlay:after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M11 18c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm48 25c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm-43-7c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm63 31c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM34 90c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm56-76c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM12 86c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm28-65c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm23-11c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-6 60c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm29 22c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-9-21c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM60 91c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM35 41c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM12 60c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2z' fill='%23ffffff' fill-opacity='0.1' fill-rule='evenodd'/%3E%3C/svg%3E");
}

.crypto-header-content {
  position: relative;
  z-index: 1;
}

.crypto-header h1 {
  color: white;
  font-size: 3rem;
  margin: 0 0 0.5rem;
  font-weight: 700;
}

.crypto-subtitle {
  color: rgba(255, 255, 255, 0.85);
  font-size: 1.2rem;
  margin-bottom: 1.5rem;
}

.crypto-metadata {
  display: flex;
  justify-content: center;
  gap: 2rem;
  color: rgba(255, 255, 255, 0.7);
}

.crypto-metadata-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.crypto-metadata-icon {
  display: flex;
  align-items: center;
}

/* Introduction Section */
.crypto-intro {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  margin-bottom: 3rem;
  align-items: center;
  padding: 0 2rem;
}

.crypto-intro-content {
  flex: 1;
  min-width: 300px;
}

.crypto-intro-content p {
  font-size: 1.1rem;
  margin: 0;
}

.crypto-intro-visual {
  flex: 1;
  min-width: 300px;
  display: flex;
  justify-content: center;
}

.crypto-visual-container {
  background: #1e272e;
  width: 100%;
  max-width: 400px;
  height: 280px;
  border-radius: 8px;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

/* Crypto Lock Animation */
.crypto-animation {
  position: relative;
  width: 200px;
  height: 200px;
}

.crypto-lock {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.crypto-lock-body {
  width: 60px;
  height: 42px;
  background: #4CAF50;
  border-radius: 5px;
  position: relative;
  box-shadow: 0 0 20px rgba(76, 175, 80, 0.5);
}

.crypto-lock-hole {
  width: 15px;
  height: 15px;
  background: #1e272e;
  border-radius: 50%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.crypto-lock-shackle {
  width: 40px;
  height: 30px;
  border: 10px solid #4CAF50;
  border-bottom: none;
  border-radius: 20px 20px 0 0;
  position: absolute;
  bottom: 40px;
  left: 10px;
  box-shadow: 0 0 20px rgba(76, 175, 80, 0.5);
}

.crypto-bits {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
}

.crypto-bit {
  position: absolute;
  width: 6px;
  height: 6px;
  background: #4CAF50;
  border-radius: 50%;
  box-shadow: 0 0 10px rgba(76, 175, 80, 0.7);
  animation: float 5s infinite ease-in-out;
}

.crypto-bit:nth-child(1) {
  top: 20%;
  left: 10%;
  animation-delay: 0s;
}
.crypto-bit:nth-child(2) {
  top: 30%;
  left: 80%;
  animation-delay: 0.5s;
}
.crypto-bit:nth-child(3) {
  top: 70%;
  left: 20%;
  animation-delay: 1s;
}
.crypto-bit:nth-child(4) {
  top: 50%;
  left: 90%;
  animation-delay: 1.5s;
}
.crypto-bit:nth-child(5) {
  top: 80%;
  left: 50%;
  animation-delay: 2s;
}
.crypto-bit:nth-child(6) {
  top: 10%;
  left: 50%;
  animation-delay: 2.5s;
}
.crypto-bit:nth-child(7) {
  top: 60%;
  left: 30%;
  animation-delay: 3s;
}
.crypto-bit:nth-child(8) {
  top: 40%;
  left: 60%;
  animation-delay: 3.5s;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0) translateX(0);
  }
  25% {
    transform: translateY(-10px) translateX(5px);
  }
  50% {
    transform: translateY(0) translateX(10px);
  }
  75% {
    transform: translateY(10px) translateX(5px);
  }
}

/* Section Styling */
.crypto-section {
  margin-bottom: 3rem;
  padding: 0 2rem;
}

.crypto-section h2 {
  color: #0f2027;
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
  position: relative;
  padding-bottom: 0.5rem;
}

.crypto-section h2:after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 60px;
  height: 3px;
  background: linear-gradient(to right, #4CAF50, #2196F3);
}

/* Component Grid Styling */
.crypto-component-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.crypto-component {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  position: relative;
  overflow: hidden;
}

.crypto-component:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.12);
}

.crypto-component:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(to right, #4CAF50, #2196F3);
}

.crypto-component-icon {
  color: #4CAF50;
  margin-bottom: 1rem;
}

.crypto-component h3 {
  margin-top: 0;
  color: #0f2027;
  margin-bottom: 1rem;
  font-size: 1.3rem;
}

.crypto-component p {
  margin: 0 0 1.5rem;
  color: #555;
  line-height: 1.6;
}

/* Code Block Styling */
.crypto-code-block {
  background: #1e272e;
  border-radius: 6px;
  padding: 1rem;
  overflow-x: auto;
}

.crypto-code-block pre {
  margin: 0;
}

.crypto-code-block code {
  font-family: 'Fira Code', 'Courier New', monospace;
  font-size: 0.85rem;
  color: #e2e8f0;
}

/* Architecture Diagram Styling */
.crypto-architecture {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  margin: 2rem 0;
}

.crypto-architecture-diagram {
  flex: 1;
  min-width: 300px;
}

.crypto-diagram-container {
  background: white;
  border-radius: 8px;
  padding: 2rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  align-items: center;
}

.crypto-module {
  background: #f5f7fa;
  border: 1px solid #e2e8f0;
  border-radius: 6px;
  padding: 1rem;
  text-align: center;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
  width: 100%;
}

.crypto-module-core {
  background: linear-gradient(135deg, #4CAF50, #2196F3);
  color: white;
  font-weight: 600;
}

.crypto-module-connections {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  width: 100%;
}

.crypto-module-interfaces {
  display: flex;
  gap: 1rem;
  width: 100%;
}

.crypto-module-interfaces .crypto-module {
  flex: 1;
  background: #e3f2fd;
  border-color: #bbdefb;
}

.crypto-module-applications {
  background: #e8f5e9;
  border-color: #c8e6c9;
}

.crypto-architecture-description {
  flex: 1;
  min-width: 300px;
}

.crypto-architecture-description h3 {
  color: #0f2027;
  margin-top: 0;
  margin-bottom: 1rem;
  font-size: 1.3rem;
}

.crypto-component-list {
  margin: 0 0 1.5rem;
  padding-left: 1.5rem;
}

.crypto-component-list li {
  margin-bottom: 0.5rem;
  color: #555;
}

/* Tabs Styling */
.crypto-tabs {
  background: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  margin-top: 2rem;
}

.crypto-tab-header {
  display: flex;
  background: #f5f7fa;
  border-bottom: 1px solid #e2e8f0;
}

.crypto-tab-btn {
  padding: 1rem 1.5rem;
  border: none;
  background: none;
  font-size: 1rem;
  font-weight: 500;
  cursor: pointer;
  transition: background-color 0.3s, color 0.3s;
  color: #555;
  outline: none;
}

.crypto-tab-btn:hover {
  background: #e3f2fd;
  color: #2196F3;
}

.crypto-tab-btn.active {
  background: white;
  color: #4CAF50;
  border-bottom: 2px solid #4CAF50;
}

.crypto-tab-content {
  display: none;
  padding: 0;
}

.crypto-tab-content.active {
  display: block;
}

/* Code Snippet Styling */
.crypto-code-snippet {
  width: 100%;
}

.crypto-code-header {
  background: #1a2a36;
  color: #e2e8f0;
  padding: 0.8rem 1rem;
  font-size: 0.9rem;
  border-radius: 8px 8px 0 0;
}

.crypto-code-snippet pre {
  margin: 0;
  padding: 1rem;
  background: #1e272e;
  border-radius: 0 0 8px 8px;
  overflow-x: auto;
}

.crypto-code-snippet code {
  font-family: 'Fira Code', 'Courier New', monospace;
  font-size: 0.85rem;
  color: #e2e8f0;
}

/* Security Grid Styling */
.crypto-security-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 1.5rem;
  margin: 2rem 0;
}

.crypto-security-item {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
}

.crypto-security-icon {
  color: #4CAF50;
  margin-bottom: 1rem;
}

.crypto-security-item h3 {
  margin-top: 0;
  color: #0f2027;
  margin-bottom: 1rem;
  font-size: 1.3rem;
}

.crypto-security-item p {
  margin: 0;
  color: #555;
}

/* Warning Box Styling */
.crypto-warning {
  background: #fff8e1;
  border-left: 4px solid #ffc107;
  padding: 1.5rem;
  display: flex;
  gap: 1rem;
  border-radius: 0 8px 8px 0;
  margin-top: 2rem;
}

.crypto-warning svg {
  color: #ffc107;
  flex-shrink: 0;
}

.crypto-warning-content h3 {
  margin-top: 0;
  color: #0f2027;
  margin-bottom: 0.5rem;
  font-size: 1.2rem;
}

.crypto-warning-content p {
  margin: 0;
  color: #555;
}

/* Skills Grid Styling */
.crypto-skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 1.5rem;
  margin-top: 2rem;
}

.crypto-skill-category {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
}

.crypto-skill-category h3 {
  margin-top: 0;
  color: #0f2027;
  margin-bottom: 1rem;
  font-size: 1.1rem;
  border-bottom: 1px solid #e2e8f0;
  padding-bottom: 0.5rem;
}

.crypto-skill-category ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

.crypto-skill-category li {
  margin-bottom: 0.8rem;
  position: relative;
  padding-left: 1.2rem;
  color: #555;
}

.crypto-skill-category li:before {
  content: "•";
  position: absolute;
  left: 0;
  color: #4CAF50;
  font-size: 1.2rem;
  line-height: 1;
}

/* Resources Styling */
.crypto-resources {
  margin: 3rem 0;
}

.crypto-resource-link {
  display: flex;
  gap: 1.5rem;
  background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
  color: white;
  padding: 1.5rem;
  border-radius: 8px;
  text-decoration: none;
  align-items: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.crypto-resource-link:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.crypto-resource-icon {
  flex-shrink: 0;
}

.crypto-resource-content h3 {
  margin-top: 0;
  margin-bottom: 0.5rem;
  color: white;
  font-size: 1.3rem;
}

.crypto-resource-content p {
  margin: 0;
  color: rgba(255, 255, 255, 0.8);
}
</style>

<script>
// Initialize tabs when the document is fully loaded
document.addEventListener('DOMContentLoaded', function() {
  const tabBtns = document.querySelectorAll('.crypto-tab-btn');
  const tabContents = document.querySelectorAll('.crypto-tab-content');
  
  tabBtns.forEach(btn => {
    btn.addEventListener('click', function() {
      // Remove active class from all buttons and contents
      tabBtns.forEach(b => b.classList.remove('active'));
      tabContents.forEach(c => c.classList.remove('active'));
      
      // Add active class to clicked button
      this.classList.add('active');
      
      // Show corresponding content
      const tabId = this.getAttribute('data-tab');
      document.getElementById(tabId).classList.add('active');
    });
  });
});
</script> 