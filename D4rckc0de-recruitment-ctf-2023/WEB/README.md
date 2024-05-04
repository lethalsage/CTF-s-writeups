## CTF
Before the CTF, I downloaded some files because I knew that certain tools would be necessary as this is my second CTF.
# `WEB`
## JWT
### Points
300
### Challenge Description
```
authenticate as user_id 0 to get the flag

NOTE: read up on "JWT" if you have no idea what's going on
```

### Attached Site
[Site](http://ctf.d4rkc0de.iiitd.edu.in:8900/)

### Explanation

As we can see that the name is JWT 

So, i search for it and came to some websites and youtube videos
Some photos from the website ![1st](jwt/img/Screenshot%20from%202023-10-23%2016-43-23.png) and ![2nd](jwt/img/Screenshot%20from%202023-10-23%2017-49-07.png)

Then I came to now some sites which directly decodes the JWT code like [jwt.io](https://jwt.io/)

### Exploitation
When i opened the website it was showing a plain text `Authentication required.`
So by instincts i just jumped to inspect and by juming arround and there was nothing, then i came to cookiese and there was an interesting one named `jwt_session` and it consist of code 

`(eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjotMX0.KYcUKjfqhf6wTJo15Bj445WkN5Y7Fr_12Vk2q-ce87c)`

 this looks like JWT code so i quckly jumped to the the site [jwt.io ](https://jwt.io/) afte putting the code (in cookies) it showd  [this](img/jwtdecode.png).

now i googled more and came to this [website](https://medium.com/debricked/ctf-json-web-tokens-jwt-f39464c675af)
, in this point it was written about [Removing the signature](jwt/img/rmvsig.png)
so i did that, i removed the signature i.e -

```
(eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjotMX0.KYcUKjfqhf6wTJo15Bj445WkN5Y7Fr_12Vk2q-ce87c)
                                          ▼
(eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjotMX0.)
```

 Now, in header i [change the algorithm from `HS256` to `none `](jwt/img/encnone.png) and [changed the payload (user_id= -1) to (user_id = 0)](jwt/img/encode0.png) as suggested in the [ challange descrition.](jwt/img/Screenshot%20from%202023-10-23%2018-04-14.png)

 Then i encoded them in base64 so that i can put it back in the cookie

```
i.e, 
now, header = eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0
     payload = eyJ1c2VyX2lkIjowf

so, new cookie is :
eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0.eyJ1c2VyX2lkIjowf.
```
now , Put this back in the cookie:

it changed form ![this](jwt/img/previous.png) to ![this](jwt/img/after.png)


 Voila!!! the page now shows the flag.

### Flag
`d4rkc0de{n0_s1gn@tur3_r3qu1r3d}`
