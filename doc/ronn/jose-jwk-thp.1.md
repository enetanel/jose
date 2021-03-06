jose-jwk-thp(1) -- Calculates the JWK thumbprint
================================================

## SYNOPSIS

`jose jwk thp` -i JWK [-H ALG] [-o THP]

## OVERVIEW

The `jose jwk thp` command calculates the thumbprint of one or more JWKs.

## OPTIONS

* `-i` _JSON_, `--input`=_JSON_ :
  Parse JWK(Set) from JSON

* `-i` _FILE_, `--input`=_FILE_ :
  Read JWK(Set) from FILE

* `-i` -, `--input`=- :
  Read JWK(Set) standard input

* `-a` _ALG_, `--algorithm`=_ALG_ :
  Use the specified hash algorithm (case sensitive)

* `-a` ?, `--algorithm`=? :
  List available hash algorithms

* `-o` _FILE_, `--output`=_FILE_ :
  Write thumbprint(s) to FILE

* `-o` -, `--output`=- :
  Write thumbprint(s) to standard input

* `-f` _THP_, `--find`=_THP_ :
  Search input keys for JWK with the given thumbprint

## EXAMPLES

Calculate the S1 thumbprint of a newly generated key:

    $ jose jwk gen -i '{"alg":"ES256"}' -a S1 | jose jwk thp -i-
    BzmSH6W8a8LlbQ1mD0iBJdYj4x4

Calculate the S256 thumbprints of a JWKSet containing two keys:

    $ jose jwk thp -i keys.jwkset -a S256
    6HJwXEuRh8gAkTz4BodEvcEj_KXkgjc-7Qez3d4VNMs
    jo_j_O5gqYpKcZKHPp3miTszAeV60MXHvdb_kkjjTWE

Find the input key with the given thumbprint:

    $ jose jwk thp -i keys.jwkset -f HYRNOxxOOHap0amTONoy1bHnS5M -o key.jwk

## AUTHOR

Nathaniel McCallum &lt;npmccallum@redhat.com&gt;

## SEE ALSO

`jose-alg`(1),
`jose-jwk-gen`(1),
