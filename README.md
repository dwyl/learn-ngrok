# Learn `ngrok`

:cloud: Learn how to use **`ngrok`**
***`so that`*** you can share
a **Web App/Site** running on your "**localhost**"
with _anyone_ online!

## _Why?_

You are working on a Web App/Site on your **`localhost`**,
but it's "not yet ready" to be "deployed"

> _**Note**: once you are **ready**
to make your App/MVP "**official**",
you should consider using **Heroku**
as it does not require you to have your `localhost` running_
(_and it has good logging, "monitoring", "free tier", etc._). <br />
See:
[github.com/dwyl/**learn-heroku**](https://github.com/dwyl/learn-heroku)


## _What?_

The **_official_ description**
on the website https://ngrok.com/product is:

> "_**`ngrok`** exposes **`local`** servers behind NATs and firewalls
to the **`public`** internet over secure tunnels_."

In _**plain** (beginner friendly) **English**_:

> _**`ngrok`** is a small piece of software
that lets you **run** a **web application** <br />
on your **`local` computer**
and (securely) **share it** with the world
on a **`public` address** ("URL")_.

![intro-image](https://user-images.githubusercontent.com/194400/37253733-66c637dc-252d-11e8-9083-84a553ba9d24.png)

## _Who?_

Anyone working on a Web App/Site
and needs a quick/easy way to _show_ or _test_ it <br >
without "_deploying_" it. e.g: you are _actively_ developing something
and deploying it to
[**Heroku**](https://github.com/dwyl/learn-heroku)
would be _too time consuming_.


## _When?_

### When _Should_ I Use **`ngrok`**?

A _great_ use-case is when you are in "**development mode**",
you have "**live-reloading**" enabled on your `locahost`
and you want any changes you make on your to be reflected
a _mobile_ device without having to re-deploy.

#### Developing Somewhere with "Strict" Firewall Rules?

Often you will be on a network with strict firewall rules
(_blocked TCP ports_)
that do not _allow_ you to share your app with your Mobile device!
e.g: in Coffee Shops, Libraries or "Corporate" Networks.

In these cases **`ngrok`** is a _great_ choice!

### When _Not_ to Use **`ngrok`**?

Avoid using **`ngrok`** when your app
is being _actively_ used by people.
i.e: once your "MVP" is ready to be tested by "real users",
deploy it somewhere that is _not_ your `localhost`
e.g: [**Heroku**](https://github.com/dwyl/learn-heroku)


## _How?_

The official "getting started" guide is:
https://dashboard.ngrok.com/get-started
Is a _good_ place to start, however we have "_condensed_"
it down into just **4 steps**!

### 1. Download & Install

First step on our quest is to download **`ngrok`** from the website:
https://ngrok.com/download

#### Mac?

If you use a **Mac** computer (_and "homebrew"_)
there's an **easy** way;
Run the following command in your terminal:
```sh
brew cask install ngrok
```
![ngrok-installed](https://user-images.githubusercontent.com/194400/37255696-e7901170-2547-11e8-9086-047db238ee7c.png)


Once you have successfully downloaded and installed **`ngrok`**.




### 2. Connect Your **`ngrok`** "Account" to Your `locahost`

If you have not _already_ authenticated with **`ngrok`**
visit: https://dashboard.ngrok.com/user/login

We use our GitHub account to authenticate with **`ngrok`**
because they only asks for **_basic_ access**:

![github-auth-ngrok](https://user-images.githubusercontent.com/194400/37255798-8d2f9442-2549-11e8-9c6e-ee4cf7af4d86.png)

Once authenticated, you should see a "Dashboard":
https://dashboard.ngrok.com/get-started

If you scroll down you will see a section entitled:
"***Connect your account***"
e.g: <br />
![connect-ngrok-account](https://user-images.githubusercontent.com/194400/37255883-db2b06c6-254a-11e8-8fa2-96f99d07a65e.png)

Copy-pasge and _run_ the command in your terminal <br />
(_including your **unique** `authtoken`,
  which you should not share BTW!_)
```sh
./ngrok authtoken 56hth5o3bbkewDmHSZEHQ_39VJe8koVu
```
> _Don't worry, this example is not a "valid" token,
it's just for demo purposes_.

#### Trouble-shooting  ...

if you see an error:
```sh
-bash: ./ngrok: No such file or directory
```
simply _remove_ the `./` in front of the `ngrok` command:
![ngrok-not-found](https://user-images.githubusercontent.com/194400/37256103-20cbea26-254e-11e8-93f6-14bd79c53721.png)
> Thanks to: https://stackoverflow.com/questions/30188582/ngrok-command-not-found/43492639


### 3. Run Your app

Now it's time to _run_ your app on your `localhost`.
Run which ever command you need (e.g: `npm start` or `mix phx.server`)
to start your app.

Make a note of the TCP Port your app is running on for step 4 below.

#### Don't Have an App?

If you don't _already_ have an "App" to try/test **`ngrok`**,
you can simply "clone" this repository and try the "demo" App!

Copy-paste and run the following command:

```sh
git clone https://github.com/dwyl/learn-ngrok.git && cd learn-ngrok && npm install
```
(_note: it take a few seconds for that command
  to run because it's installing
the "**live-server**" dependency for running the app, be patient ..._)

In your Terminal window you should see something like this:<br />
![npm-start](https://user-images.githubusercontent.com/194400/37256155-b66becde-254e-11e8-8170-e7b6545ef727.png)

Once the command has run it will start the "app"
and open it in your `default` web browser. e.g: <br />
![hello-world-in-browser](https://user-images.githubusercontent.com/194400/37256135-7652625e-254e-11e8-823a-a59ac7c0f128.png)

### 4. Start the **`ngrok`** "Tunnel"

Create the **`ngrok`** "tunnel" to your app
by running the following command
in a _`new`_ terminal window
(_different from the one where your app is running_):
```sh
./ngrok http 4000
```
or (_on Mac OSX_):
```sh
ngrok http 4000
```
you should now see something similar to this: <br />
![ngrok-tunnel-terminal](https://user-images.githubusercontent.com/194400/37256183-2392fa1e-254f-11e8-8a78-40b8c5664819.png)

This confirms that the **`ngrok`** forwarding the given URL
to your `locahost` on TCP Port `4000`.

In our case the **`ngrok`** URL is https://f00ead01.ngrok.io
but yours will be a different random string as the sub-domain.


### 5. Visit the `ngrok` URL in your Web Browser

Open your Web Browser and visit: https://f00ead01.ngrok.io
![voila](https://user-images.githubusercontent.com/194400/37256874-92fad422-2558-11e8-934f-be6e6efcd547.png)


***Voilà***! Your App on the `public` Internet!
(_not that you had any doubt it would work ..._) <br />

To Quit **`ngrok`** simply use the `Ctrl+C` command.

> _**Note**: if you **`quit` `ngrok`**
the URL of your app will change.
That's why the URL in the GIF below
is different from this one ...
if you want a **fixed** URL,
you will need to **pay** for it._

### 6. But _Wait_, There's _More_!

Open the **`ngrok`** "inspector" http://localhost:4040
a new tab or browser window:

![ngrok-inspector](https://user-images.githubusercontent.com/194400/37256355-5cc1f4f0-2551-11e8-86b2-6ed3468012a9.png)

#### 6.1 Make a Change in your App

If you make a simple change in your App,
you should see it update in the browser!
(_the "demo" App has "**live reloading**"
if yours does not, simple refresh the browser window._)
e.g: <br />
![update-app-live-reload-gif](https://user-images.githubusercontent.com/194400/37256787-85f2ac6a-2557-11e8-9a1c-f123647460f2.gif)


That's it!

> Obviously **`ngrok`** has many more "advanced" features,
we _encourage_ you to read the docs
if you need something _specific_: https://ngrok.com/docs


## Any Questions?

If you have any questions, get "stuck"
or want a more "advanced example",
please open an issue: https://github.com/dwyl/learn-ngrok/issues
