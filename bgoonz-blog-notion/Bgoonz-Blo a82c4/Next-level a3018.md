# Next-level component showcasing with Storybook controls - LogRocket Blog

[https://blog.logrocket.com/next-level-component-showcasing-with-storybook-controls/](https://blog.logrocket.com/next-level-component-showcasing-with-storybook-controls/)

![Next-level%20a3018/next-level-component-showcasing-with-storybook-controls-nocdn.png](Next-level%20a3018/next-level-component-showcasing-with-storybook-controls-nocdn.png)

## What are Storybook controls?

[Storybook controls](https://storybook.js.org/) constitutes a mechanism to display graphical UI controls (e.g., a color picker) on a dedicated Storybook panel to interact with your React components dynamically. As an example, thereby, the user can easily change the background color or font size of a component for manual testing or demonstration purposes.

![Next-level%20a3018/storybook-color-picker-control.gif](Next-level%20a3018/storybook-color-picker-control.gif)

Dynamically change the font color using Storybook's color picker control

The important aspect here is that you do not have to code these demonstration use cases as part of the component's codebase, which means you don't have to mix these separate concerns and can instead avoid watering down your React component.

It's actually quite the opposite — Storybook provides an elegant way to let these "interaction UI elements" be configured directly in the story code. Furthermore, in contrast to using [Storybook knobs](https://storybook.js.org/addons/@storybook/addon-knobs/), which is now largely considered obsolete in favor of controls, you don't have to write a ton of code to do the trick.

This is because the new controls mechanism relies on intelligent analysis of your React component's code by leveraging static code analysis tools, such as [react-docgen](https://github.com/reactjs/react-docgen) or [react-docgen-typescript](https://github.com/styleguidist/react-docgen-typescript).

If you are already familiar with Storybook knobs, or you're curious about the differences between these mechanisms, I'll show you a comparison of the same use case implemented with knobs at the end of this article. For now, let's look into working the new way, with Storybook controls.

## Set up Storybook and controls with `sb init`

The easiest way to install Storybook is with the help of [npx and the sb package](https://github.com/storybookjs/storybook/tree/main/app/react). Additional ways to get it up and running can be found in [the Storybook for React tutorial](https://storybook.js.org/tutorials/intro-to-storybook/react/en/get-started/).

```
$ npx sb init
```

Storybook will detect the project type automatically when added to an existing project — in our case, it's a React project. As you can see from the next screenshot, you can start with an opinionated React project betting on CSS files and SVG images with Storybook up and running.

![Next-level%20a3018/result-sb-init-command-534x1024.png](Next-level%20a3018/result-sb-init-command-534x1024.png)

The result of the sb init command

Currently, [Storybook controls](https://github.com/storybookjs/storybook/tree/next/addons/controls) do not come out of the box with the above installation script. Thus, we need to install the addon manually.

```
$ npm i -D @storybook/addon-controls
```

Since Storybook is a [Lerna](https://github.com/lerna/lerna) [monorepo project](https://doppelmutzi.github.io/monorepo-lerna-yarn-workspaces/), all addons are located in sub-projects with additional `Readme.md` files that document how to install and integrate them in your Storybook project.

![Next-level%20a3018/addons-storybook-project.png](Next-level%20a3018/addons-storybook-project.png)

The `sb` script has already created a `.storybook/main.js` file with a couple of inbuilt addons for us. We have to add our controls addon to this file, too. The following config is sufficient for our use case.

```
"addons": [
    '@storybook/addon-controls',
    "@storybook/addon-essentials"
  ]
```

In addition, the `sb` script added npm scripts to `package.json`. With `npm run storybook`, we can test if everything is working.

```
"scripts": {
  // ...
  "storybook": "start-storybook -p 6006",
  "build-storybook": "build-storybook"}
```

## About our companion project

To demonstrate how to use Storybook controls, I created a [companion GitHub project](https://github.com/doppelmutzi/companion-project-react-storybook) that consists of a React application and stories that heavily use controls. The React app is heavily inspired by [todomvc](https://todomvc.com/examples/react/#/active).

![Next-level%20a3018/demo-react-companion-project.gif](Next-level%20a3018/demo-react-companion-project.gif)

After you clone the GitHub repo, install the dependencies and then start the React [dev server](http://localhost:3000/) to run the demo app.

```
$ npm i
$ npm run dev
```

To [open Storybook](http://localhost:6006/), execute the following command.

```
$ npm run storybook
```

### Webpack 5 support

At the time of this writing, Storybook does not work out of the box with [webpack 5](https://webpack.js.org/concepts/).

![Next-level%20a3018/storybook-does-not-support-webpack-5.png](Next-level%20a3018/storybook-does-not-support-webpack-5.png)

Because we'll be using webpack 5 in this demo project, we need to take [some extra steps](https://github.com/storybookjs/storybook/blob/next/MIGRATION.md#webpack-5). First, we have to install two additional packages: `[@storybook/builder-webpack5](https://www.npmjs.com/package/@storybook/builder-webpack5)` and `[@storybook/manager-webpack5](https://www.npmjs.com/package/@storybook/manager-webpack5)`.

```
$ npm i -D @storybook/builder-webpack5 @storybook/manager-webpack5
```

Finally, we need to add the webpack 5 builder to our `.storybook/main.js` file.

```
  core: {
      builder: 'webpack5',
  }
```

The final result looks like this:

```
// .storybook/main.js
module.exports = {
  core: {
    builder: "webpack5",
  },
  stories: ["../src/**/*.stories.mdx", "../src/**/*.stories.@(js|jsx|ts|tsx)"],
  addons: ["@storybook/addon-essentials", "@storybook/addon-controls"],};
```

## Examining our first, basic story using controls

Let's take a look at our first story, which is based on the `Headline` component. On the right side of the below screenshot, you can see the component as it will appear as part of the demo app. On the left side, you see a story in the section **App Headline** named **Basic**. The story is set up to use a single color-picker control to dynamically adjust the font color of the headline.

![Next-level%20a3018/story-with-color-picker-control.png](Next-level%20a3018/story-with-color-picker-control.png)

Story with a color picker control

The following code is all you need to add the color picker control to the story and wire it to the `Headline` component.

```
// src/stories/Headline.stories.jsximport Headline from "../Headline";export default {
  component: Headline,
  title: "App Headline",};export const Basic = ({ color })=> <Headline color={color} />;Basic.args = {
  color: "#516dd0",};
```

Although it's not part of Storybook controls, I would like to say a few words about the structure of the story.

As you can read in [Storybook's docs about story structure](https://storybook.js.org/docs/react/writing-stories/introduction), the default export defines metadata about your component. We override the default name (Headline) of the Storybook node with the `title` property. Additionally, every named export constitutes a story — in our case, we just have one named Basic. The name is derived from the variable that gets exported.

## How controls work

You may wonder where the reference to controls is. The underlying [controls concept](https://storybook.js.org/docs/react/essentials/controls) is to write stories [using args](https://storybook.js.org/docs/react/writing-stories/introduction#using-args). Storybook will automatically generate UI controls based these args and what it can infer about your component.

Below, I slightly rewrote the above story code to make it more clear how controls work.

```
// src/stories/Headline.stories.jsx// ...export const Basic = (args)=> <Headline {...args} />;Basic.args = {
  color: "#516dd0",};
```

The following snippet shows the implementation of the `Headline` component. The demo project uses [styled components](https://blog.logrocket.com/benefits-using-styled-components-react/) as a CSS library, but this is beyond the scope of this article.

```
// src/Headline.jsximport styled from "styled-components";const Headline = styled.h1`
  color: ${(props) => props.color};
  font-size: 100px;
  font-weight: 100;
  text-align: center;
`;const HeadlineComponent = ({ color })=> {
  return <Headline color={color}>todos</Headline>;};
```

As you can see, the `Headline` component just has a `color` prop of type `string` as input. To get the color picker control working, we need to export a function that accepts `args` as single-method arguments, and pass it to the actual React component.

In the second example, we spread all args into the component by `(args) =><Headline {...args} />`. Since we know that we have only one color argument, we can also make it more explicit, as shown in the first example: `({ color }) =><Headline color={color} />`.

How does Storybook know that we want to show a color picker control? It makes the decision based on the initial value of the arg.

```
Basic.args = {
  color: "#516dd0",};
```

### Custom control type matcher

If you understand why this is enough information for Storybook, then I'll provide you with the last part of the puzzle, which is [configured in `.storybook/preview.js`](https://storybook.js.org/docs/react/configure/overview#configure-story-rendering).

```
// .storybook/preview.jsexport const parameters = {
  controls: {
    matchers: {
      color: /(background|color)$/i,
      date: /Date$/,
    },
  },
  // ...}
```

The `.storybook/preview.js` file, along with this code, was generated by the aforementioned `sb` script. With the help of this file, you can [control the way things are rendered](https://storybook.js.org/docs/react/configure/overview#configure-story-rendering) in stories — for example, you can [configure the layout](https://storybook.js.org/docs/react/configure/story-layout#global-layout) of stories so that components will be centered inside of them.

From a control's point of view, the important part is the `controls` property, as you can see above. Whenever Storybook recognizes an arg named as specified in the regex, it uses the [custom control type matcher](https://storybook.js.org/docs/react/essentials/controls#custom-control-type-matchers) `color` to display a color picker UI control. In addition, we will see an example for a date picker control later in this article.

## Examining advanced controls with `argTypes`

In the next story example, we will see that using only args is not sufficient. We have to configure the controls further with the help of `[argTypes](https://storybook.js.org/docs/react/api/argtypes)`.

As the below screenshot shows, two stories display `TodoItem` components and let the user interact with them via controls.

![Next-level%20a3018/advanced-story-using-arg-types.png](Next-level%20a3018/advanced-story-using-arg-types.png)

### Some words about the demo app architecture

In my opinion, it is not possible to explain Storybook concepts without reference to the underlying project design. How to write your stories depends on the React concepts you used to build your components.

As an example, in contrast to components that just accept React props (as with our `Headline` component), you need to do some extra work if components rely on [the React Context API](https://beta.reactjs.org/learn/passing-data-deeply-with-context#context-an-alternative-to-passing-props).

Before we get to the story implementation, let's take a look at some key aspects of the `TodoItem` component that we need to take care of first, before we get to configuring our controls.

```
// src/TodoItem.jsxconst Container = styled.div`
  height: 30px;
  // ...
`;const TodoItem = ({ todo })=> {
  const { todos, setTodos } = useContext(AppContext);
  const [hover, setHover] = useState(false);
  const [checkHover, setCheckHover] = useState(false);
  return (
    <Container
      onMouseEnter={()=> setHover(true)}
      onMouseLeave={()=> setHover(false)}>// skip implementation for reasons of clarity </Container>
  );};
```

The important takeaway of this snippet is that the component [makes use of React Context](https://blog.logrocket.com/react-context-api-deep-dive-examples/), and therefore, we need to provide `todos` and `setTodos` in our story. Concretely, we need to provide the context values to `AppContext.Provider`, which is part of the `Todos` component. Our `TodoItem` component gets rendered as part of the `TodoList` component.

```
// src/Todos.jsx // ...const Todos = ()=> {
  const [todos, setTodos] = useState([]);
  const [filterIndex, setFilterIndex] = useState(0);
  return (
    <AppContext.Providervalue={{
        todos,
        setTodos,
        filterIndex,
        setFilterIndex,
        theme: theme.LIGHT,
        translation,}}><Container><TodoInput/><TodoList/>{todos.length >0&&<ActionBar/>}</Container></AppContext.Provider>);};
```

### Providing context in the story

In contrast to the `Headline` component that used a single prop, writing this story is a little bit more complicated. Take a look at the following code snippet that wraps the UI component (`TodoItem`) in two containers (`StyleAndContextProvider`, `StorySpecificContainer`).

```
// src/stories/TodoItem.stories.jsximport TodoItem from "../TodoItem";// ...const TodoItemWithProvider = ({ label,checked, date,...ctxValues })=> (
  <StyleAndContextProvider{...ctxValues}><StorySpecificContainer styles={{ width: commonStoryContainerWidth }}><TodoItem
        todo={{
          id:1,
          date:newDate(date).toDateString(),
          label,checked,}}/></StorySpecificContainer></StyleAndContextProvider>);
```

The most important part is the props parameter of the `TodoItemWithProvider` React component. In our example, we directly destructure the relevant information into variables because we need to pass them as arguments to different components.

As I'll describe soon, `label`, `checked`, and `date` are the Storybook args that are responsible for rendering the UI controls in the controls panel (notice the `label`, `creation date`, and `checked controls` in the previous screenshot).

With `...ctxValues`, we take all remaining properties defined in the props object and collect them in the `ctxValues` variable.

Let's take a look at the two wrapper components. First, we examine the `StyleAndContextProvider`. We provide all properties of `ctxValues` as props by spreading them into the component by `{...ctxValues}`.

```
// src/storie/storyHelper.jsimport { GlobalStyle } from "../App";import AppContext from "../AppContext";export const commonStoryContainerWidth = 750;export const StyleAndContextProvider = ({ children,...ctxValues })=> (
  <AppContext.Provider
    value={{...ctxValues,}}><GlobalStyle/>{children}</AppContext.Provider>);
```

This code is the "glue code" that makes sure that we wrap our UI component (`children`) in a container that passes the required context values (`ctxValues`) to the `AppContext.Provider`, as it is also used in the application code (in the `Todos` component).

In addition, `GlobalStyle` is imported and rendered to initialize the global styles (e.g., styles and margins of the body element). For the sake of clarity, I do not show these styles.

The second container (`StorySpecificContainer`) can be used by stories to provide additional styles that are important to render the isolated UI component appropriately inside of a story.

```
// src/stories/storyHelper.js/*
    since every component is layout-agnostic and streteches 100% of parent
    width, we need to take care of a container with appropriate width.
    Therefore, we can define styles, e.g., width or height.
*/export const StorySpecificContainer = ({ children, styles })=> (
  <div style={styles}>{children}</div>);
```

With that said, let's move on to the actual control-specific code.

## Configuring controls with the help of `argTypes`

With the following code, Storybook renders the text input, date picker, and boolean controls to the panel. In combination with the "glue code" described in the last section, we can interact with our `TodoItem` component.

```
// stories/TodoItem.stories.jsx// ...// some meta informationexport default {
  component: TodoItem,
  title: "Todo item",};// code for the story "Initially Unchecked"/*
  provide context values for component:
  - todos array with one todo item
  - Mocked setTodos function to prevent crashes
*/const ctxProps = {
  todos: [{
      id: 1,
      date: new Date(Date.now()).toDateString(),
      label: "LogRocket rocks",
      checked: false,
    }],
    setTodos: ()=> {
      // mock impl
    },};export const InitiallyUnchecked = (args)=> (
  <TodoItemWithProvider{...args}{...ctxProps}/>);InitiallyUnchecked.argTypes ={
  date:{
    name:"creation date",
    description:"Creation date of an todo entry.",
    table:{
      type:{ summary:"Date.toDateString() result"},
      defaultValue:{ summary:"Date.now()"},},
    control:"date",},};InitiallyUnchecked.args ={
  label:"read a LogRocket article",
  date:newDate(),checked:false,};
```

Let's break down this code in pieces. The `ctxProps` object is required for our application design to provide additional context values to the context provider. If you recall from the code of the `TodoItem` component, `todos` and `setTodos` are pulled out of the context (`const { todos, setTodos } = useContext(AppContext)`).

The following code creates a concrete story and delegates these `ctxProps` to the `TodoItemWithProvider` component. In addition, we also spread the `args` to the component. These `args` constitute the controls.

```
export const InitiallyUnchecked = (args)=> (
  <TodoItemWithProvider{...args}{...ctxProps}/>);
```

In summary, `args` represent the values needed to initialize the Storybook controls and pass them to the context provider. The `ctxProps` are the other values passed to the context provider to initialize the `TodoItem` component completely.

The last part of the setup is the configuration of `args` and `argTypes`.

```
InitiallyUnchecked.argTypes = {
  date: {
    name: "creation date",
    description: "Creation date of an todo entry.",
    table: {
      type: { summary: "Date.toDateString() result" },
      defaultValue: { summary: "Date.now()" },
    },
    control: "date",
  },};InitiallyUnchecked.args = {
  label: "read a LogRocket article",
  date: new Date(),
  checked: false,};
```

The `args` section provides both the initial values for the story and the information for the controls addon to infer concrete controls. From the point of view of the text input control (`label`), and the boolean control (`checked`), this is all that is necessary. Based on the data types of every properties of the `args` object, Storybook can decide what controls to render. That's why `label`, which is of type *string*, gets rendered as a text field and `date`, which is of type date, gets rendered as date picker.

Let's recall the `TodoItemWithProvider` component. `label` and `checked` are used to initialize the `todo` prop that is the input for the `TodoItem` component.

```
const TodoItemWithProvider = ({ label, checked, date,...ctxValues })=> (
      // skip containers
      <TodoItem
        todo={{
          id: 1,
          date: new Date(date).toDateString(),
          label,
          checked,
        }}
      />);
```

To setup the date picker control, we need to do some extra work once more, with the help of `[argTypes](https://storybook.js.org/docs/react/api/argtypes)`. `control: "date"` is required to tell Storybook to render a date picker instead of a text input field.

```
InitiallyUnchecked.argTypes = {
  date: {
    name: "creation date",
    control: "date",
    // ignore the rest for now
  },};
```

The initial value for the date picker has to be specified in the `args` object.

```
InitiallyUnchecked.args = {
  // initialize date picker with current time and date
  date: new Date(),
  // skip other args};
```

Basically, that's all!

### `ArgTypes` and `ArgsTable`

The following screenshot shows [how our date picker control is rendered](https://storybook.js.org/docs/react/writing-docs/introduction).

![Next-level%20a3018/example-argtable.png](Next-level%20a3018/example-argtable.png)

With the `InitiallyUnchecked.argTypes` object, we can provide additional information to specify the story in more detail.

```
InitiallyUnchecked.argTypes = {
  date: {
    name: "creation date",
    description: "Creation date of an todo entry.",
    table: {
      type: { summary: "Date.toDateString() result" },
      defaultValue: { summary: "Date.now()" },
    },
    control: "date",
  },};
```

The `name`, `description`, and `table` properties are used in this example to provide more information to the so-called [ArgsTable](https://storybook.js.org/docs/react/writing-docs/doc-blocks#argstable).

## Some more use cases of advanced controls

The following screenshot shows an [overview](https://storybook.js.org/docs/react/essentials/controls#annotation) of available controls and how they map to the data types.

![Next-level%20a3018/overview-available-controls.png](Next-level%20a3018/overview-available-controls.png)

### Radio buttons example

The second story we looked at, Initially Checked, differs from the previous story in how the **checked** control is implemented.

![Next-level%20a3018/custom-mapping-radio-button-control.png](Next-level%20a3018/custom-mapping-radio-button-control.png)

The implementation of this story's checked control demonstrates how to work with the data type enum and how to map it to an `inline-radio` control type with custom labels.

```
// src/stories/TodoItem.stories.jsx// ...export const InitiallyChecked = InitiallyUnchecked.bind({});InitiallyChecked.argTypes = {
  ...InitiallyUnchecked.argTypes,
  checked: {
    options: ["openTodo", "completedTodo"],
    mapping: {
      openTodo: false,
      completedTodo: true,
    },
    control: {
      // Type 'select' is automatically inferred when 'options' is defined
      type: "inline-radio",
      labels: {
        openTodo: "todo is open",
        completedTodo: "todo is completed",
      },
    },
  },};InitiallyChecked.args = {
  ...InitiallyUnchecked.args,
  checked: "completedTodo",};
```

First, we define a new, named export to create a new story by cloning the former story with [Storybook's preferred technique](https://storybook.js.org/docs/react/writing-stories/introduction#using-args) (`InitiallyUnchecked.bind({})`).

The goal with our custom control is to map the radio button values to boolean values that are passed as a `checked` prop to the `TodoItem` component. Therefore, we need a combination of `options`, `mapping`, and `labels` to make this happen. It's important that the string values of the enum (`options`) match with the property keys of `mapping` and `labels`.

`options` and `mapping` are sufficient to initialize the custom control. However, without setting `type: "inline-radio"`, Storybook would render the default control (**select**). If we do not provide the `labels` object, the string values of `options` are used as the labels for the radio control.

It's also important to provide an initial value for the radio control with the help of the `args` object (`checked: "completedTodo"`), otherwise, neither radio button is initially selected.

### Select box example

The second story — called Interactive, for its Action bar — demonstrates two more controls. As you can see in the next screenshot, I added a control with the name "list of todos" with the data type object. Storybook infers a control type of `object` and, therefore, renders a JSON editor control.

![Next-level%20a3018/custom-mapping-select-control.png](Next-level%20a3018/custom-mapping-select-control.png)

This is another, more technical way to provide interactive data to the component. Depending on the use case and the user type, this control might be appropriate.

If your stories are used by stakeholders without a development background, this "JSON control" may be unclear for use. As an example, a less flexible dropdown control that enables the user to select from a few values to showcase the relevant use cases may be more appropriate.

To find out more about this "Standard" story for the `Action bar` component, take a look at the source code of the companion project.

![Next-level%20a3018/locate-standard-story-action-bar-component.png](Next-level%20a3018/locate-standard-story-action-bar-component.png)

However, for the "JSON control" we need to set the control type to "object" `Interactive.argTypes.todos`. To set the initial value, we assign a list of todos to `Interactive.args.todos`.

```
export const Interactive = (args)=> (
  <ActionBarWithProvider{...args}{...ctxProps}/>);Interactive.argTypes ={
  todos:{
    name:"list of todos",
    description:"Status component shows number of unchecked todos.",
    control:{ type:"object"},},
  theme:{
    name:"theme variant",
    description:"There exists a dark and light theme with different background and foreground colors.",
    options:["light","dark"],
    mapping:{
      light: theme.LIGHT,
      dark: theme.DARK,},
    control:{
      type:"select",
      labels:{
        light:"light theme",
        dark:"dark theme",},},},};Interactive.args ={
  todos:[{
      id:Date.now(),
      date:newDate(Date.now()).toDateString(),
      label:"a todo",
      checked:false,},],
  theme:"dark",};
```

Let's look at the second control named "theme variant". As a reminder, the theme can be set as context value, so we need to provide an arg with the key of `theme`.

```
// src/Todos.jsx// ...<AppContext.Provider
      value={{
        todos,
        setTodos,
        filterIndex,
        setFilterIndex,
        theme: theme.LIGHT,
        translation,
      }}
    >
    // ...</AppContext.Provider>
```

To configure the select control to switch the theme variant, we again utilize `options`, `mapping`, and `control.labels` as properties of the `Interactive.argTypes.theme` object. We could omit the `control.type` because "select" is the default. The initial value of the control is set with `Interactive.args.theme`.

## The difference between controls and knobs

You may not know, but Storybook [knobs](https://github.com/storybookjs/addon-knobs) have been deprecated in favor of controls. According to this [discussion](https://github.com/storybookjs/storybook/discussions/15060), the biggest advantage of controls over knobs is that they are based on `args`, so Storybook can infer information to render controls.

However, there are still use cases where knobs may be required, e.g., to archive type-safety and IDE support in TypeScript projects. According to the same discussion linked above, Storybook is working on removing these shortcomings.

To give you an idea of the differences, here is a knobs example: `TodoItemKnobs.stories.jsx`, of the same use case we already implemented with controls, `TodoItem.stories.jsx`.

```
// src/stories/TodoItemKnobs.stories.jsximport TodoItem from "../TodoItem";import { withKnobs, text, boolean, date } from "@storybook/addon-knobs";import {
  StorySpecificContainer,
  StyleAndContextProvider,
  commonStoryContainerWidth,} from "./storyHelper";export default {
  component: TodoItem,
  title: "Todo item (Knobs)",
  decorators: [withKnobs],};const exampleTodo = {
  id: 1,
  date: new Date(Date.now()).toDateString(),
  label: "hello",
  checked: false,};const TodoItemWithProvider = (ctxValues)=> (
  <StyleAndContextProvider {...ctxValues}>
    <StorySpecificContainer styles={{ width: commonStoryContainerWidth }}>
      <TodoItem
        todo={{
          ...exampleTodo,
          date: new Date(date("creation date", new Date())).toDateString(),
          label: text("label", "a todo"),
          checked: boolean("checked", false),
        }}
      />
    </StorySpecificContainer>
  </StyleAndContextProvider>);// provide context to prevent crashes in event handlersconst ctxProps = {
  todos: [{ ...exampleTodo }],
  setTodos: () => {
    // mock impl
  },};export const InitiallyUncheckedKnobs = () => (
  <TodoItemWithProvider {...ctxProps} />);
```

The code above implements the same story, InitiallyUnchecked, from `TodoItem.stories.jsx` with the help of the [knobs addon](https://github.com/storybookjs/addon-knobs). To get this running, we first have to install the addon.

```
$ npm i -D @storybook/addon-knobs
```

The main difference from controls is that, with knobs, the code is more explicit, meaning you have to use more API functions.

```
import { withKnobs, text, boolean, date } from "@storybook/addon-knobs";
```

In our example, we want to create three knobs; therefore, we imported the three data types — `text`, `boolean`, and `date` — to render a text input, a checkbox, and a date picker, respectively. The `withKnobs` function is also important, because we have to add a decorator to the default export of the story.

```
export default {
  component: TodoItem,
  title: "Todo item (Knobs)",
  decorators: [withKnobs],};
```

In contrast to controls, the story is written without `args`, so the function of the named export does not have an argument.

```
export const InitiallyUncheckedKnobs = ()=> (
  <TodoItemWithProvider{...ctxProps}/>);
```

Another difference is that we do not pass in the data (along with initial values) to the React component. Instead, we have to calculate them inside of the component with the help of the above imported data type functions.

```
const TodoItemWithProvider = (ctxValues)=> (
  // ...
      <TodoItem
        todo={{
          ...exampleTodo,
          date: new Date(date("creation date", new Date())).toDateString(),
          label: text("label", "a todo"),
          checked: boolean("checked", false),
        }}
      />
  // ...);
```

The first arguments of the function constitute the label for the knobs, and the second one provides the initial value.

## Conclusion

This article focus on Storybook controls. After a short ramp-up time, the principles of `args` and `argTypes` quickly become clear. Due to the concept of [convention over configuration](https://en.wikipedia.org/wiki/Convention_over_configuration), developing with controls does not require a lot of code. As you saw in the last section, using knobs does not confer the benefit of inferring data types — thus, every knob needs to be explicitly implemented with the help of data type functions.

In my opinion, the controls approach scales better for bigger projects and in the long run.

The examples shown in this article focus on a small but realistic use case to demonstrate most of data types and control types. If you still need more inspiration, feel free to check out the [companion project](https://github.com/doppelmutzi/companion-project-react-storybook) that provides even more stories.

## Full visibility into production React apps

Debugging React applications can be difficult, especially when users experience issues that are hard to reproduce. If you're interested in monitoring and tracking Redux state, automatically surfacing JavaScript errors, and tracking slow network requests and component load time, [try LogRocket](https://www2.logrocket.com/react-performance-monitoring).

![Next-level%20a3018/1d0cd-1s_rmyo6nbrasp-xtvbaxfg.png](Next-level%20a3018/1d0cd-1s_rmyo6nbrasp-xtvbaxfg.png)

[LogRocket](https://www2.logrocket.com/react-performance-monitoring) is like a DVR for web and mobile apps, recording literally everything that happens on your React app. Instead of guessing why problems happen, you can aggregate and report on what state your application was in when an issue occurred. LogRocket also monitors your app's performance, reporting with metrics like client CPU load, client memory usage, and more.

The LogRocket Redux middleware package adds an extra layer of visibility into your user sessions. LogRocket logs all actions and state from your Redux stores.

Modernize how you debug your React apps — [start monitoring for free](https://www2.logrocket.com/react-performance-monitoring).
