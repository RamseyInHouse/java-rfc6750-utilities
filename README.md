# RFC6750 Java implementation
Java implemented utilities designed to [RFC6750](https://tools.ietf.org/html/rfc6750#section-3.1) specifications.

---

## `WWW-Authenticate` Response Header
> _[RFC2617](https://tools.ietf.org/html/rfc2617)_

### Auth Params
* `realm`
    > _[RFC2617-1.2](https://tools.ietf.org/html/rfc2617#section-1.2)_
RFC6750:
    > `The "realm" is OPTIONAL.`<br/>
    > `The "realm" attribute MUST NOT appear more than once.`

* `scope`
    > _[RFC6749-3.3](https://tools.ietf.org/html/rfc6749#section-3.3)_
RFC6750:
    > `The "scope" is OPTIONAL.`<br/>
    > `The "scope" attribute MUST NOT appear more than once.`

---

#### Error state `auth-params`
RFC6750 states:
> `If the protected resource request included an access token and failed authentication, the resource server SHOULD include the "error" attribute to provide the client with the reason why the access request was declined.`<br/>
(_Therfore these `auth-params` are optional._)<br/>
> `The "error", "error_description", and "error_uri" attributes MUST NOT appear more than once.`

* `error`
    > _[RFC6749-A.7](https://tools.ietf.org/html/rfc6749#appendix-A.7)_
* `error_description`
    > _[RFC6749-A.8](https://tools.ietf.org/html/rfc6749#appendix-A.8)_
* `error_uri`
    > _[RFC6749-A.9](https://tools.ietf.org/html/rfc6749#appendix-A.9)_

#### Other `auth-params`
The `auth-params` listed so far are only the ones described in RFC6750.
Custom `auth-params` or `auth-params` defined in related RFC's, like the ones references in this README, are also allowed; Those other `auth-params` are **optional**, and **can occur more than once** in the `WWW-Authenticate` response header _unless_ otherwise outlined from the respective RFC in which they are defined.

### Note on `auth-param` order within the `WWW-Authenticate` response header
The builder provided in this library imposes an order to the `auth-params` as they are present in the builder at the time of building. That order is the same as the order of appearance in this README which is the same order they are found in RFC6750.
