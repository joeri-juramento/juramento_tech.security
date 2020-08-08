

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

PIV refers to Yubikey 'app-portion' of SmartCards, only available on the Yubico's Yubikey 5+ not Yubico's blue Security keys.

### Itty bitty details

Notice that Passwordless login is most of the time is equivalent to not needing to type in password nor the username! Imagine the effort and errors saved if people don't have to type in their password or their username.
(Power users might need to pick a username from a list in case of multiple identities.)





![Picture of Security Key NFC and Phone](https://www.yubico.com/wp-content/uploads/2019/01/sky-3-img-2.png)



## Background information | Why this table?

Paragraphs have been made <u>**skim-compatible** 🤓, read headers and underlined part to get the **gist**</u>.

#### Cause of Quest

I have been a Yubikey user for some time, but the FIDO2 support was added in the later models. I started this 'quest' to experience and test the benefit of Passwordless logon, but also for my parents because they are becoming of age and <u>passwords, pins and secrets are **overwhelming**</u> them. Additionally more users around me could benefit from Passwordless login because that are simply not a fan (or capable) of remembering passwords.

Personally I have been getting by with a **Password-vault**, but managing such a vault is not for everyone. I have observed <u>**users struggling** because of application complexity or human-error</u> by not being precise. 

#### Bandaid Design

Though very potentially very useful, a password manager or vault is a bandaid design solution to the negative cascade effect of the world of Passwords. Passwords try to solve the problem of secure authentication / identification. If you are reading this you know that <u>passwords are not solving that problem most elegantly</u> even though historically it makes total sense we (humans) started there. 

I think Passwordless (or Credential-less) logons are the next generation of authentication where there is no (encrypted) shared secret between client-user and server like a password (which can be stolen, re-used, shared etc). I recognise Steve Gibson's SQRL technology and <u>Yubico's & Microsoft's **FIDO2** integration as such next-generation technologies</u>. This article focuses on SecurityKey authentication.

#### Today

Using a <u>YubiKey (5+) or Security Key is a Passwordless option that is **available today**</u>, though, as you might have surmised from this article – referencing the big table – <u>it is not integrated yet as seamless as one would desire</u>, but hopefully support will continue to grow. At the moment, one cannot give the user a serviced Yubikey, without sharing the account password because the Yubikey-authentication is not supported on every contact-point in the Microsoft services world. <u>The **Password remains mandatory** in some situations.</u> (Timestamped statement 8th of August, 2020)

#### Transition

We have been using physical keys to open our homes for decades, but in the digital world it has been "something you know" in stead of "something you have". I think the transition to something physical (can also be on your phone) can solve the problem of authentication or at least make the interaction more pleasant and costing less effort while being more secure. 

> *"If the key only works on 90% of the services-contactpoints, it is not a replacement of a password."*

The tricky part will be the last 10%. <u>If the key only works on 90% of the service-contactpoints, **it is not a replacement of a password**</u>, it is a contextual available alternative path... meaning that it works most of the times, but not always, resulting in user frustration. Furthermore, you just added complexity by needing the user to remember three different authentication methods. 

#### Current status quo

That being said, if you (or your users) can get passed the one-time mandatory password setups, <u>one could balance Passwordless logins **between the Authenticator app and the Security Key** as long as mobile platforms[^or-other] do not support FIDO2[^CTAP] yet</u> (timestamped, 8th of August 2020). Additionally, on platforms where the Security Key logon is supported, please take note that <u>the Security Key logon option is **not presented as the default or an equal alternative** in the graphical user interface</u> and if the user is not educated or informed, the user will type in their e-mail address and go the authenticator push-route in stead of the FIDO2 Security Key route which requires them clicking on an alternative button below the e-mail address field. Take a look:

[^or-other]: Or an application or a package or server support or service-provider-support or whatever in the chain that needs to be aligned for FIDO2 keys to work on mobile devices.  ↩
[^ctap]: Apparently there is CTAP version 1.1 and 2.0; the last one is required for Passwordless login. I might add more information, at the moment my mental model of FIDO2 and the relation to CTAP2.0 is not complete. I learned about these trying to figure out why Security Key logon on Mac in Firefox and Safari is not working, but Brave, Edge for Mac are supporting the Security Key. It is still a bit confusing to me to be honest.  https://bugzilla.mozilla.org/show_bug.cgi?id=1530370

![ms-logon-securitykey-button-marked](ms-logon-securitykey-button-marked.png)

In this screenshot the Security Key option is presented as a *depended alternative path*, meaning the lay-out / design of the screen may cause the user to:

* fill-out their e-mail, hit enter and be confronted with a password prompt or push prompt. Completely skipping or missing the FIDO2 logon.
* fill-out their be-mail before clicking *"Sign in with security key"*. But filling out the e-mail is not required for the Security Key. The complete identity is on the Security Key! 

We are not required to fill out anything here, which is why this design has these undesirable consequences. The logon experience must be updated to improve the experience, but this is what we have got to work with today. I need to mention it, because technical support and integration is not the only thing that has to be overcome.

The table helps me identify those must-enter-password dialogs and keep an eye on the progress of FIDO2/Security key support. I could not find this information elsewhere.

#### Future

Now I can ask my serviceproviders and suppliers what is exactly blocking a certain row. It makes it far easier to refer to a page and row and ask what the blocking (upstream) issue is.



•••



Joeri • Juramento



 

