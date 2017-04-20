Pattern: Weak cryptographic key use

Issue: -

## Description

As computational power increases, so does the ability to break ciphers with
smaller key lengths. The recommended key length size for RSA and DSA
algorithms is 2048 and higher. 1024 bits and below are now considered
breakable. EC key length sizes are recommended to be 224 and higher with 160
and below considered breakable. This rule checks for use of any key
less than those limits and returns a high severity error if lower than the
lower threshold and a medium severity error for those lower than the higher
threshold.

Example of **incorrect** code:

```python

>> Issue: DSA key sizes below 1024 bits are considered breakable.
   Severity: High   Confidence: High
   Location: examples/weak_cryptographic_key_sizes.py:36
35  # Also incorrect: without keyword args
36  dsa.generate_private_key(512,
37   backends.default_backend())
38  rsa.generate_private_key(3,

```

## Further Reading

  - <http://csrc.nist.gov/publications/nistpubs/800-131A/sp800-131A.pdf>
  - <https://security.openstack.org/guidelines/dg_strong-crypto.html>
* [OpenStack - B505: weak_cryptographic_key](https://docs.openstack.org/developer/bandit/plugins/weak_cryptographic_key.html)