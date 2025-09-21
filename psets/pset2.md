# Problem Set 2

## Concept Questions

1. Contexts partition the nonce namespace to allow the same nonce to be used across different domains. A context would be a specific domain so that each domain has its own unique namespace.

2. The NonceGeneration must store used strings to ensure uniqueness. With a counter implementation, the abstraction function is:
  used strings = {string representations of integers 0 through counter-1}.
So if counter = 100, used strings = {"0", "1", ..., "99"}.

3. One advantage of words as nonces is more memorable URLs. One disadvantage is the limited namespace. I would modify NonceGeneration to use a dictionary of words and generate combinations of multiple words joined by hyphens to expand the namespace while maintaining memorability.

## Synchronization Questions

1. The first sync only needs shortUrlBase to generate a nonce for that domain context. The second sync needs both shortUrlBase and targetUrl because it's actually creating the URL shortening mapping that associates the nonce with the target URL.

2. The convention isn't used when the argument name differs from the variable name being bound to it. For example, in the register sync, the nonce result is bound to shortUrlSuffix argument, so it must be explicitly written as "shortUrlSuffix: nonce".

3. The first two syncs respond to user requests to shorten URLs, so they include the request action. The third sync is triggered automatically when a URL is registered, so no request action is needed.

4. Sync:
  ```
  sync generate
  when Request.shortenUrl ()
  then NonceGeneration.generate (context: "bit.ly")
  ```

5. Sync:
  ```
  sync expire
  when ExpiringResource.expireResource (): (resource)
  then UrlShortening.delete (shortUrl: resource)
  ```

## Extending the Design

### Additional Concepts

**concept Analytics [Resource]**
- **purpose**: track access counts for resources
- **principle**: after recording an access, the count increases by one
- **state**: a set of Resources with an accessCount Number
- **actions**:
  - `recordAccess (resource: Resource)`
    - effect increments access count for resource
  - `getCount (resource: Resource): (count: Number)`
    - requires resource exists in analytics
    - effect returns current access count

**concept UserOwnership [User, Resource]**
- **purpose**: associate resources with their owners
- **principle**: only the owner can access their resources
- **state**: a set of Ownerships with owner User and resource Resource
- **actions**:
  - `setOwner (user: User, resource: Resource)`
    - effect associates resource with user as owner
  - `checkOwner (user: User, resource: Resource): (isOwner: Boolean)`
    - effect returns true if user owns resource

### Essential Synchronizations

```
sync trackOwnership
when UrlShortening.register (): (shortUrl)
then UserOwnership.setOwner (user: currentUser, resource: shortUrl)

sync recordLookup
when UrlShortening.lookup (shortUrl)
then Analytics.recordAccess (resource: shortUrl)

sync viewAnalytics
when Request.getAnalytics (user, shortUrl)
     UserOwnership.checkOwner (user, shortUrl): (true)
then Analytics.getCount (resource: shortUrl): (count)
```

### Feature Requests Assessment

1. **Custom short URLs**: Good idea. Add optional parameter to UrlShortening.register to accept user-provided suffix instead of generated nonce. Modify register sync to skip nonce generation when custom suffix provided.

2. **Word-based nonces**: Good idea. Replace NonceGeneration with WordBasedNonceGeneration concept.

3. **Target URL in analytics**: Good idea. Extend Analytics state to include targetUrl. Modify recordLookup sync to pass both shortUrl and targetUrl to Analytics.recordAccess.

4. **Non-guessable URLs**: Good idea. Modify NonceGeneration to use secure random generation instead of sequential counters.

5. **Analytics for unregistered users**: Undesirable feature. Analytics require user authentication to protect privacy. Without user accounts, there's no secure way to verify ownership.

