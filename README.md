# MinLoginRegister
Minimal example of express server login/registration/member-only system with: 
  * hashing for registration(Bcrypt.hash)
  * hash-comparison for login(Bcrypt.compare) 
  * login sessions(JWT.sign)
  * Member activity(JWT.verify)

# Routes

* Home Page
  * / 
  * GET
  * Shows JWT of member if any member is logged in.  
    Shows list of accounts in accounts.json.  
    3 Forms for Registration, Login, Member-only-activity
* Registration
  * /register
  * POST
  * Input: username, password
  * `Bcrypt.hash` hash password to get passHash which gets written to accounts.json  
* Login
  * /login
  * POST
  * INPUT: username, password
  * `Bcrypt.compare` to compare password in request to accounts.json passHash.  
    `jwt.sign` which takes username as input and gives a session token.  
* Member-only-activity Area
  * /dostuff
  * GET
  * INPUT: none
  * `jwt.verify` to decode JWT
    Member does stuff like ask server to modify their blog.  
    All Server gets is a JWT token; Server needs to decode JWT to get username to do stuff on behalf of member.
