# GroupHug Quick Start

## 🧬 Introduction

GroupHug is a react component that helps build a live avatar stack in your web applications. Quick deployment, real-time interaction, based on Presencejs and Webtransport.

## 🤹🏻 Quick Start

### Installation

First, you need to install the required dependencies.

by npm:

```bash
npm install --save @yomo/presence @yomo/group-hug-react
```

by yarn:

```bash
$ yarn add @yomo/presence
```

by pnpm:

```bash
$ pnpm i @yomo/presence
```

### Request free dev/test account

Then, login with your Github account on AllegroCloud, create a new project, and you will get a free app_id and publicKey. The app_id and publicKey will be used in subsequent steps.

### Integrate to your project

After installation, you can create a GroupHug.tsx file in your components folder. Then create a GroupHug component in this file. You can copy the following code into GroupHug.tsx:

```tsx
import React, { useState } from "react";
import { createRoot } from "react-dom/client";
import { createPresence } from "@yomo/presence";
import GroupHug from "@yomo/group-hug-react";
import "@yomo/group-hug-react/dist/style.css";

const domContainer = document.querySelector("#app");
const root = createRoot(domContainer);

const userId = "YOUR_USER_ID";
const avatar = "YOUR_AVATAR_URL";
const name = "YOUR_USER_NAME";
const presence = createPresence({
  url: "https://prscd2.allegro.earth/v1",
  publicKey: "YOUR_PUBLIC_KEY",
  id: "YOUR_CONNECTION_ID",
  appId: "YOUR_APP_ID",
});

const App = () => {
  const [darkMode, setDarkMode] = useState(true);
  return (
    <div
      style={{
        padding: "200px",
        background: darkMode ? "black" : "white",
        display: "flex",
        flexDirection: "column",
        alignItems: "start",
        gap: "20px",
      }}
    >
      <button
        style={{ color: darkMode ? "white" : "black" }}
        onClick={() => setDarkMode(!darkMode)}
      >
        {darkMode ? "close dark mode" : "open dark mode"}
      </button>
      <GroupHug
        presence={presence}
        id={userId}
        avatar={avatar}
        name={name}
        darkMode={darkMode}
      />
    </div>
  );
};

root.render(<App />);
```

Don't forget to REPLACE{_YOUR_PUBLICKKEY_} and{_YOUR_APPID_}in the code above with the values you just obtained in AllegroCloud.

You can adjust the position of the component on the page by modifying className:

```html
<div className="“absolute" top-[14px] right-[24px]”>
  <div style="{{}}">// ... ...</div>
</div>
```

Import Appin your project：

```tsx
/*
      ...
      your imports
      ...
      */
import App from "../components/GroupHug";

/*
      ...
      your code
      ...
      */

export default function Home() {
  //... ...
  //Your Code
  //... ...

  return (
    <>
      {/*
      ...
      your code
      ...
      */}
      <App />
    </>
  );
}
```

If you want to customize more attributes, you can refer to the content of the for hackers section
Start dev

```bash
$ npm run dev and go to http://localhost:3000
```

## Deploy

Next, you can deploy your project to cloud platforms such as Vercel, and requests for services such as GroupHug in the project will interact with AllegroCloud. AllegroCloud provides you with the network resources and computing resources required for these components to run. The following will take the deployment on the Vercel platform as an example:
Get your free dev server account from https://presencejs.yomo.run, add them to the Enviroment Variables section of your Allegro Console:

![image](/img/9345b5f5-b416-4b6f-82fe-995946532d24.png)

## 🥷🏼 for hackers

presence: `Promise<IPresence>`: Presence instance.
avatarBorderColor?: string: to set the color of avatar's border.
id: string:to set the users' ID.
avatar?: string`<url>`: the avatars of users.
name: string: to set the names of users.
darkMode?: boolean:to set light/dark mode.Defaults：FALSE
