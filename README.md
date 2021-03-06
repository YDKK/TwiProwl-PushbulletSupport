# Instruction 

Version : 2.2 with Pushbullet support by YDKK

1. install some ruby libraries

 for Ruby 1.8
  - openssl
  - json (deb or rubygems)
  - hmac-ruby (deb or rubygems)
  - oauth (from rubygems)

```
$ sudo apt-get install libopenssl-ruby1.8 libjson-ruby1.8 libhmac-ruby1.8
```
or
```
$ sudo gem install --no-rdoc --no-ri oauth
```

 for Ruby >= 1.9.1 (recommend >= 1.9.2)
  - openssl
  - ruby-hmac >= 0.4.0 (from rubygems)
  - oauth (from rubygems)

```
$ sudo apt-get install rubygems1.9.1 libopenssl-ruby1.9.1
```
or
```
$ sudo gem1.9.1 install --no-rdoc --no-ri ruby-hmac oauth
```

  If you want to use Growl, you should install growl.gem and growlnotify(1).

2. copy config.yml to ~/.twiprowl.conf and edit it.
3. run twiprowl


## config.yml 
```yaml
LogDir: /tmp               # Log Directory
Debug: false               # Debugging ouput to log.
Daemon: true               # Daemon mode.
ProxyURI:                  # URI for http proxy.

Prowl:
 APIKey: xxxxxxxxxxxxxxxx  # the Prowl API Key

NMA:
 APIKey: xxxxxxxxxxxxxxxx  # the NMA's API Key

Pushbullet:
 AccessToken: xxxxxxxxxxx  # the Pushbullet's AccessToken

Growl:
 Sticky: 0                 # lowest priority to use sticky option.

Accounts:
 -
  Application: <application name (optional)> 
  NotifyMethods:           # notify methods you want to use.
   - prowl
   - nma
   - pushbullet
   - growl
  User: <Twitter username>
  UseProxy: false          # <= use Prowl::ProxyURL
  Mentions:                # Event on Mentions
    Enable: false          # Enable, true or false
    Priority: 0            # Prowl priority, -2 to 2
    IgnoreSelf: false      # Ignore Mention from myself
  Direct:                  # Event on Direct Messages
    Enable: false
    Priority: 0
    IgnoreSelf: false      # Ignore DM from myself
  Retweets:                # Event on Retweets
    Enbale: false
    Priority: 0
    IgnoreSelf: false      # Ignore RT by myself
  Membership:              # Event on List Membership
    Enable: false
    Priority: 0
    IgnoreSelf: false      # Ignore event by myself
    IgnoreNegative: false  # Ignore removal event
  Unfollowed:              # Event on Unfollowed, requires API rate
    Enable: false
    Priority: 0
    Interval: 90
  Favorite:                # Event on Favorite/Unfavorite
    Enable: false
    Priority: 0
    IgnoreSelf: false      # Ignore favorite event by myself
    IgnoreNegative: false  # Ignore Unfavorite event
  RegexpMatch:             # notify when match with Regexp
    -
      User: "^hogehoge.*"  # Regexp for screen name
      Text: "hugahuga"     # Regexp for body text
      Enable: true
      Priority: 0
    -                      # all user and text contains "TwiProwl"
      Text: "TwiProwl"
      Enable: true
    -                      # all of takuo_jp's post.
      User: "takuo_jp"
      Enable: true
 - 
  <Other account config here>
```
