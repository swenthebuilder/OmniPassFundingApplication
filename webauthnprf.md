### WebAuthn PRF Extension
The WebAuthn PRF extension enables authenticators to generate pseudo-random outputs during credential operations. This output serves as the foundation for key derivation.

### Key Aspects:
- **Input and Output**: PRF takes a salt as input and produces a deterministic 32-byte value based on the authenticator's secret.
- **Process Integration**: Invoked during WebAuthn calls like `navigator.credentials.get` or `create`.
- **Role in Derivation**: The output acts as initial keying material (IKM) for HKDF.

**Invocation Example**:
```javascript
const saltBytes = new TextEncoder().encode('my_fixed_salt');
const result = await navigator.credentials.get({
  publicKey: {
    challenge: crypto.getRandomValues(new Uint8Array(32)),
    // ... other params ...
    extensions: { prf: { eval: { first: saltBytes } } }
  }
});
const prfOutput = result.getClientExtensionResults().prf.results.first; // 32-byte Uint8Array
```

### HKDF Overview
HKDF (RFC 5869) derives keys from IKM through two phases: extract (to create a PRK) and expand (to produce final keys with context).

### Phases:
- **Extract**: Mixes IKM with a salt to yield a PRK.
- **Expand**: Uses PRK, info (context), and a counter to generate keys of desired length.

**Why HKDF?** It handles fixed-size PRF outputs, enabling length adjustment and context-based separation.

### The Key Derivation Process
1. **Authenticate and Obtain PRF Output**: Use WebAuthn to get the 32-byte IKM after user verification.
2. **Prepare HKDF Inputs**: Define salt (optional), info (context string), length, and hash (e.g., SHA-256).
3. **Extract PRK**: HMAC(salt, IKM) → PRK.
4. **Expand to Key**: Iteratively HMAC(PRK, previous + info + counter) until length is reached.
5. **Use the Derived Key**: For signing, encryption, etc.

This process ensures deterministic, secure keys without storage.
