# Exercise 1

1. The two invariants are: purchase counts never exceed requested counts for any item, and every purchase corresponds to an existing request. The first invariant is more important as it prevents overselling. The `purchase` action preserves it by checking available count and decrementing the request.

2. The `addItem` action can break the first invariant when adding items that have existing purchases. Fix: Ensure new total requested count >= existing purchase count for that item.

3. Yes, registries can be opened/closed repeatedly. Recipients may wish to temporarily close registries to manage items privately.

4. Yes, missing deletion would matter as it causes system clutter and privacy issues.

5. Two common queries:
a. Owner: "Show purchases by item and purchaser",
b. Giver: "Show available items and quantities".

6. Add `surpriseMode` flag to Registry state and `setSurpriseMode` action. When enabled, hide purchase details from owner until registry closes.

7. Generic Item type provides separation of concerns, flexibility across domains, and better performance by avoiding duplicated metadata.

# Exercise 2

1. State:
```
a set of Users with
  a username String
  a password String
```

2. Actions:
```
register (username: String, password: String): (user: User)
  requires no user exists with this username
  effects create new user with given username and password

authenticate (username: String, password: String): (user: User)
  requires user exists with this username and password
  effects return the matching user
```

3. Essential invariant: Each username maps to exactly one user. Preserved by register checking uniqueness before creating users.

4. Email confirmation extension:
```
state
  a set of Users with
    a username String
    a password String
    a confirmed Flag
  a set of PendingRegistrations with
    a username String
    a password String
    a token String

actions
  register (username: String, password: String): (user: User, token: String)
    requires no user or pending registration exists with this username
    effects create new user with confirmed=false, create pending registration with random token

  confirm (username: String, token: String)
    requires pending registration exists with this username and token
    effects set user.confirmed=true, remove pending registration

  authenticate (username: String, password: String): (user: User)
    requires user exists with this username, password, and confirmed=true
    effects return the matching user
```

# Exercise 3

**PersonalAccessToken concept:**
```
concept PersonalAccessToken
purpose enable access with revocable credentials
principle user creates tokens, uses tokens for API access, and can revoke individual tokens without affecting others
state
  a set of Users with
    a username String
  a set of Tokens with
    an owner User
    a tokenString String
    a scopes set of Permission
    an expiration Date
    a revoked Flag
actions
  createToken (user: User, scopes: set of Permission, expiration: Date): (token: String)
    effects create new token with random string, given scopes and expiration
  
  authenticate (username: String, token: String): (user: User, permissions: set of Permission)
    requires token exists, not revoked, not expired, belongs to user with username
    effects return user and token's permissions
  
  revokeToken (user: User, token: String)
    requires token exists and belongs to user
    effects set token.revoked = true
```

Differences:
- Users can have many active tokens vs. one password
- Tokens grant specific access rights, passwords grant full access
- Individual tokens can be revoked without affecting others
- Tokens have built-in expiration
- Designed for API/script access, not human login

Documentation improvement: GitHub should emphasize that tokens are *additional* credentials for automation, not password replacements.

# Exercise 4

**URL Shortener**
```
concept URLShortener
purpose create easy to remember aliases for long URLs
principle user submits a long URL and optionally a custom suffix,
  receives a short URL that redirects to the original when used
state
  a set of Mappings with
    a shortCode String
    a originalURL String
    a creator User
    a created Date
actions
  shorten (url: String, customCode: String, user: User): (shortURL: String)
    requires customCode is unique or empty
    effects if customCode provided, create mapping with customCode,
      otherwise generate random code and create mapping
  
  redirect (shortCode: String): (originalURL: String)
    requires mapping exists for shortCode
    effects return originalURL
```

**Conference Room Booking**
```
concept ConferenceRoomBooking
purpose reserve meeting spaces for specific time periods
principle user selects available room and time slot,
  creates booking that prevents others from booking same slot
state
  a set of Rooms with
    a name String
    a capacity Number
  a set of Bookings with
    a room Room
    a booker User
    a startTime DateTime
    a endTime DateTime
    a purpose String
actions
  checkAvailability (room: Room, start: DateTime, end: DateTime): (available: Flag)
    effects return true if no overlapping bookings exist
  
  book (room: Room, user: User, start: DateTime, end: DateTime, purpose: String): (booking: Booking)
    requires room available for time period and start < end
    effects create new booking
  
  cancel (booking: Booking, user: User)
    requires user is booker
    effects remove booking
```

**Time-Based One-Time Password (TOTP)**
```
concept TOTP
purpose provide time-sensitive 2FA
principle user and server share secret, both generate same token based on current time, user enters token to prove possession
state
  a set of Users with
    a username String
    a secret String
    a lastUsedTime DateTime
actions
  setup (user: User): (secret: String, qrCode: String)
    effects generate shared secret, return secret and QR code for app setup
  
  generateToken (secret: String, time: DateTime): (token: String)
    effects compute token from secret and time window
  
  verify (user: User, token: String, currentTime: DateTime): (valid: Flag)
    requires user has secret and currentTime > lastUsedTime
    effects return true if token matches expected value for time window,
      update lastUsedTime to prevent replay
```

Notes:
- **URL Shortener**: Handles both custom and auto-generated codes.
- **Room Booking**: Assumes non-overlapping bookings.
- **TOTP**: Time window prevents replay attacks.

