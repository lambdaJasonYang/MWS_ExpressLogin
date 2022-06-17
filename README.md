# MinLoginRegister
Minimal example of express server login/registration/member-only system with: 
  * hashing for registration(Bcrypt.hash)
  * hash-comparison for login(Bcrypt.compare) 
  * login sessions(JWT.sign)
  * Member activity(JWT.verify)

# Routes

* Home Page
  * GET: `http://localhost:3300/` 
  * Shows JWT of member if any member is logged in.  
    Shows list of accounts in accounts.json.  
    3 Forms for Registration, Login, Member-only-activity
* Registration
  * POST: `http://localhost:3300/register`
  * Input: username, password
    * Example Payload: {"username" : "bob", "password" : "suprsecret"}
  * `Bcrypt.hash` hash password to get passHash which gets written to accounts.json  
* Login
  * POST: `http://localhost:3300/login`
  * INPUT: username, password
    * Example Payload: {"username" : "bob", "password" : "suprsecret"} 
  * `Bcrypt.compare` to compare password in request to accounts.json passHash.  
    `jwt.sign` which takes username as input and gives a session token.  
* Member-only-activity Area
  * GET: `http://localhost:3300/dostuff`
  * INPUT: none
  * `jwt.verify` to decode JWT  
    Ex Scenario: Member does stuff like ask server to modify their blog.  
    But all Server sees is a JWT token; Server needs to decode JWT to get username to do stuff on behalf of member.
