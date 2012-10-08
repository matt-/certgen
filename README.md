certgen
=======

A wrapper around the openssl utility for programatically generating signed certificates. All underlying I/O operations are asynchronous, so this is safe to use in a latency-sensitive server program.

The main function is `generate_cert_buf`. Given a signing key and cert, and a hash containing the desired subject distinguished name information, the function creates a certificate, signs it, and opens buffers to the certificate. The buffers can then be supplied to https.createServer().

The hash may contain properties with the following key names:
* 'C' (Country)
* 'ST' (State)
* 'L' (Locality)
* 'O' (Organization)
* 'OU' (Organization Unit)
* 'CN' (Common Name)

Function prototype:

```
/*
 * Generate a signed certificate from supplied information.
 * 
 * prefix: Temporary file prefix. 
 * keepFiles: Whether to keep generated files upon process exit.
 * hash: Object containing subject's distinguished name information
 * caKeyPath: the signer's key
 * caCertPath: the signer's certificate
 * cb: a callback of the form cb(err, keyBuf, certBuf)
 */
exports.generate_cert_buf = function (prefix, keepFiles, hash, caKeyPath, caCertPath, cb) {
}
```
