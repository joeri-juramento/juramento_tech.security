

# Compatibility Matrix

## Passwordless login 

This table show the compatibility of several Microsoft services among several platforms while working towards Passwordless logins. 

Set-up default: Login with Username & Password.
Nudged default: Passwordless login by Authenticator "Push Login" 
**Desired default: Passwordless login by Security Key NFC (or YubiKey 5+) "FIDO2"**

![Picture of Yubico's Blue Security Key](https://www.yubico.com/wp-content/uploads/2019/10/security_key_series_web_op.png)



Testcase OK means: *"User can login with Security Key without needing the password."*

| Description                | OK/NOK?  |     Password login | Push login | Security-Key login | Context                                        | Test Date |
| -------------------------- | :------: | -----------------: | :--------- | :----------------- | :--------------------------------------------- | :-------- |
| Edge on Mac                |   OK 🟢   |          Surpassed | Default    | Optional           | outlook.live.com or  login.microsoftonline.com | 2020 July |
| Edge Windows               | OK 🟢 RT  |          Surpassed | Default    | Optional           | outlook.live.com or login.microsoftonline.com  | 2020 July |
| Firefox on Mac             | NOK 🔴 ⁉️  |          Surpassed | Default    | Impossible         | outlook.live.com or login.microsoftonline.com  | 2020 July |
| Firefox Windows            |   OK 🟢   |          Surpassed | Default    | Optional           | outlook.live.com or login.microsoftonline.com  | 2020 July |
| Brave on Mac               |   OK 🟢   |          Surpassed | Default    | Optional           | outlook.live.com or login.microsoftonline.com  | 2020 July |
| Brave Windows              |   OK 🟢   |          Surpassed | Default    | Optional           | outlook.live.com or login.microsoftonline.com  | 2020 July |
| Safari (Mac)               | NOK 🔴 ⁉️  |          Surpassed | Default    | Impossible         | outlook.live.com or login.microsoftonline.com  | 2020 Aug  |
| OneDrive on Mac            |  NOK 🔴   |          Mandatory | Impossible | Impossible         | Login OneDrive app                             | 2020 July |
| Outlook for Mac            |    RT    |                    |            |                    |                                                |           |
| Outlook Windows            |    RT    |                    |            |                    |                                                |           |
| Mail & Calendar app        |    RT    |                    |            |                    | Add account in Win 10 App,  "this app only".   |           |
| Outlook for iOS            |  NOK 🔴   |         Impossible | Default    | Impossible         | Adding or re-auth account                      | 2020 July |
| Outlook for Android        |    RT    |         Impossible | Default    | ?                  | Adding or re-auth account                      |           |
| Authenticator  (MS) iOS    |  NOK 🔴   | Mandatory 1st time | Default    | Impossible         | Adding account MSA ID                          | 2020 July |
| Authenticator (MS) Android | NOK 🔴 RT | Mandatory 1st time | Possible   | Impossible         | Adding account MSA ID                          | --        |
| Mail app iOS               | NOK 🔴 RT |  Auth app required | Default    | Impossible         | Exchange / Outlook integration.                | 2020 July |
|                            |          |                    |            |                    |                                                |           |
|                            |          |                    |            |                    |                                                |           |
|                            |          |                    |            |                    |                                                |           |

OK = Okay. NOK = Not okay. RT = Re-test, re-verify.

### Machine login

| Description          |      OK/NOK?      |      Password login | Push login              | Security-Key login            | Context                                     | Test Date |
| -------------------- | :---------------: | ------------------: | :---------------------- | :---------------------------- | :------------------------------------------ | :-------- |
| Windows (AzAD)       |       OK 🟢        | Surpassed, Fallback | Surpassed, Fallback=RT! | Default                       | Login Azure-AD-joined machine               | 2020 July |
| Windows (MSA ID) RT  |         ?         |                     |                         |                               |                                             |           |
| Windows (standalone) |         ?         |                     |                         |                               |                                             |           |
| Mac (standalone)     | OK🟡PIV NOK🔴 FIDO2 |             Default | Impossible              | FIDO2: Unknown Yubikey PIV:OK | Login Mac, smartcard, requires cert PINcode | 2020 July |
| Mac (AzAD)           |         ?         |                     |                         |                               |                                             |           |

PIV refers to Yubikey 'app-portion' of SmartCards, only available on the Yubico's Yubikey 5+ not Yubico's Security keys.

### Itty bitty details

Notice that Passwordless login is most of the time is equivalent to not needing to type in password nor the username! Imagine the effort and errors saved if people don't have to type in their password or their username.
(Power users might need to pick a username from a list in case of multiple identities.)





![Picture of Security Key NFC and Phone](https://www.yubico.com/wp-content/uploads/2019/01/sky-3-img-2.png)



### If you need more background information...

Paragraphs have been made **skim-compatible** 🤓

#### Cause of Quest

I have been a Yubikey user for some time, but the FIDO2 support was added in the later models. I started this 'quest' to experience and test the benefit of Passwordless logon, but also for my parents because they are becoming of age and <u>passwords, pins and secrets are **overwhelming**</u> them. Additionally more users around me could benefit from Passwordless login because that are simply not a fan of remembering passwords.

Personally I have been getting by with a **Password-vault**, but managing such a vault is not for everyone. I have observed <u>**users struggling** because of application complexity or human-error</u> by not being precise. 

#### Bandaid Design

Though very potentially very useful, a password manager or vault is a bandaid design solution to the negative cascade effect of the world of Passwords. Passwords try to solve the problem of secure authentication / identification. If you are reading this you know that <u>passwords are not solving that problem most elegantly</u> but historically it makes total sense we (humans) started there. 

I think Passwordless (or Credential-less) logons are the next generation of authentication where there is no (encrypted) shared secret between client-user and server like a password. I recognise Steve Gibon's SQRL technology and <u>Yubico's & Microsoft's **FIDO2** integration as such next-generation technologies</u>. This article focuses on SecurityKey authentication.

#### Today

Using a <u>YubiKey (5+) or Security Key is a Passwordless option that is **available today**</u>, though, as you might have surmised from this article – referencing the big table – <u>it is not integrated yet as seamless as one would desire</u>, but hopefully support will continue to grow. At the moment, one cannot give the user a serviced Yubikey, without sharing the account password because the Yubikey-authentication is not supported on every contact-point in the Microsoft services world. <u>The **Password remains mandatory** in some situations.</u>

#### Transition

We have been using physical keys to open our homes for decades, but in the digital world it has been "something you know" in stead of "something you have". I think the transition to something physical (can also be on your phone) can solve the problem of authentication or at least make the interaction more pleasant and costing less effort while being more secure. 

> *"If the key only works on 90% of the services-contactpoints, it is not a replacement of a password."*

The tricky part will be the last 10%. <u>If the key only works on 90% of the service-contactpoints, **it is not a replacement of a password**</u>, it is a contextual available alternative path... meaning that it works most of the times, but not always, resulting in user frustration. Furthermore, you just added complexity by needing the user to remember three different authentication methods. 

#### Current status quo

That being said, if you (or your users) can get passed one-time mandatory password setups, one could balance Passwordless logins between the Authenticator app and the Security Key as long as mobile platforms (or apps) do not support FIDO2 yet (timestamped, 8th of August 2020). 

The table helps me identify those must-enter-password dialogs and keep an eye on the progress of FIDO2/Security key support. I could not find this information elsewhere.

#### Future

Now I can ask my serviceproviders and suppliers what is exactly blocking a certain row. It makes it far easier to refer to a page and row and ask what the blocking (upstream) issue is.



•••



Joeri • Juramento

