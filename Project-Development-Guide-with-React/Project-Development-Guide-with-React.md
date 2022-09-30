---

[EN] Project Development Guide with React - Emre MUTLU
Hello,
This guide contains rules that must be followed when developing applications with React. This guide aims to ensure that the codes written by different people are compatible with each other and to produce higher quality codes with fewer errors. In other words, it is aimed that people working in a team coherently writing code.
Note: Take everything here as an opinion, not an absolute. There's more than one way to build software.

---

About the Author
For over two years, I've been developing projects with React. I learned the necessary information to enter this sector on the internet. That's why I want to pay my debt to the community and contribute to the development of the community by sharing the knowledge I have gained on the internet.
"Knowledge grows as it is shared"

---

THINGS TO KNOW BEFORE YOU START READING
There are too many technical terms in the text, so to explain them all, I added a link to the explanation for the subject mentioned in the technical terms. (Underlined phrases are clickable links.)
Be sure to learn the basic Javascript information described in this article: https://www.freecodecamp.org/news/top-javascript-concepts-to-know-before-learning-react/
Be sure to understand the following statement thoroughly.
"Everything is a component in React."

- Well, we use HTML tags (eg: <div>…</div>).

* Actually, it is a React Component; we are using JSX. We do not use HTML.
  For an introduction to JSX, read: https://reactjs.org/docs/introducing-jsx.html
  Note: This guide assumes you are using the functional component. Click to examine the differences between functional components and class components.
  Note: This guide assumes you are using VSCode. If you use Webstorm or any other code editor, you can ignore the VSCode-related parts.
  Why did I choose to use VSCode?
  Because I love VSCode's code snippets system, shortcuts, the repository of add-ons, and customizability.
  You can find detailed information about VSCode at this address: https://code.visualstudio.com/docs/editor/whyvscode#:~:text=With%20support%20for%20hundreds%20of,navigate%20your%20code%20with%20ease.
  If we apply the SOLID principles to REACT:
  S = Single responsibility principle (SRP) => "every function/module/component should do exactly one thing"
  O = Open-closed principle (OCP) => "software entities should be open for extension, but closed for modification"
  L = Liskov substitution principle (LSP) => "subtype objects should be substitutable for supertype objects"
  I = Interface segregation principle (ISP) => "clients should not depend upon interfaces that they don't use."
  D = Dependency inversion principle (DIP) => "one should depend upon abstractions, not concretions"

- For example, you should not do data fetching in a component. The Component's job is to render. It doesn't need to know anything else. For this reason, we should do the data extraction in a different method and only pass the result of this data extraction to the Component.
  WHAT TO DO

1. VSCode Settings
   First of all, it is mandatory to use the "ESLint," "Prettier," and "GitLens" plugins for the VSCode application.
   Why is it mandatory?

- ESLint instantly warns you about your mistakes and prevents you from building incorrectly.
- Prettier allows your codes to be formatted within the framework of your specific settings. (For example: Let a maximum of 120 characters be displayed on a line, more on the bottom line. Or end each variable with a semicolon after it is defined.) (We usually use Prettier at the time of saving.)
- GitLens is a tool that allows you to do your Git operations from the VSCode interface. (You can see which line was added by who and with which commit message. In this way, you can better analyze the purpose of the written code.).

* Install the "Emre MUTLU - Javascript - Extension Pack" add-on package if you wish.
  Emre MUTLU - Javascript - Extension PackThe standard "Commit" format must be implemented on git. (For example, you can consider the commit messages system here and expand it by adding new rules for your projects. (Example: https://github.com/emremutlu08/react-best-practices/blob/main/common-commit-format/common-commit-format.md)

2. Basic Principles

- The principles of "DRY, KISS, and YAGNI" must be followed.
- It would be best if you put the "Single Responsibility" principle into practice.
- All components must have an id. (This way, it will be easier for us to debug.) These IDs should not conflict with each other.
  Therefore, if the React version used in the project is less than 18, use the expression => id = Math.floor(Math.random() \* 100 + 1) + '-' + FILE_NAME,
  If it's large, you can use the expression id = useId() + '-' + FILE_NAME.
- Everything has to be a component if it will use more than once.
- All props used in the Component FILE_NAME.propTypes = { … props should be added here }
- If mapping on a component array, adding a unique key value to the component in the most inclusive position is mandatory.

3. Naming
   Pay attention to naming conventions.Proper and descriptive nomenclature is mandatory. (For example, instead of typing isModelOneOpen or shortening it to isModOnOp, you should name it isCreateModelOpen long and descriptively.) This way, you don't have to add comments to explain it.
   Filenames must be PascalCase names. (Ex: SubmitFormElement)
   Function names must be camelCase names. (Ex: onSubmit)
   Custom hook names must start with useSmt (Ex: useWindowSize)

4. Formatting
   Write third-party (e.g., npm packages) imports at the top (in alphabetical order if possible). Write the in-app imports at the bottom.
   Common "ESLint" and "Prettier" settings are mandatory for all new projects. (For example, you can use the settings available here: https://github.com/emremutlu08/emre-mutlu---javascript---extension-pack/tree/main/prettier-and-eslint-files)
   Before committing your code, make sure that the formatting is correct.

RECOMMENDED
To prevent frequent state changes, it will be helpful to use input fields within the <form></form> tag and to get the information in case of onSubmit. (React applications "render" happens "on every state change". If this happens too often, it negatively affects application performance.)
Note: You can also use the useMemo hook to avoid unnecessary rendering in different situations.

NOT RECOMMENDED

RECOMMENDEDCreate "VSCode snippets" (code snippets) for frequently used expressions. (This way, you avoid spending too much time on things that must be written repeatedly.)
(You can use this tool to quickly generate snippets: https://snippet-generator.app/)

We type 'fa', and the snipped appears.Leave it the way you want to find it: Someone who came before you may have left the code messy, did copy-paste work, in short, left a poor quality code. You should fix the code whenever you find the opportunity so that you and the people who come after you will encounter more understandable codes.

We want to change this.

To this :)It is recommended to ask for help: After you have done enough research and are sure that you cannot reach the result on your own, you should ask a teammate for help. Because you can get the answer quickly thanks to them saying a keyword you did not think of at that moment.
WHAT NOT TO DO
Anything that will not be used on the current screen should not be called beforehand. (Especially at the beginning, it is necessary not to call everything and reduce the application's performance.)
It is necessary to avoid using strings that appear suddenly in the file called "Magic String".

- For example: (Type item.userTypeId === userTypeEnum.Admin instead of item.userTypeId === 2) should be written so that it is easy to read, and you don't repeatedly look to see what Admin's code was. (At the same time, if the Admin's code changes, you will save yourself the hassle by changing it in one place.)
- Example-2: (Use <button>{EDIT_BUTTON_TEXT}</button> instead of <button>EDIT</button>). (You can also use i18next, which provides convenient localization operations.)
  It is necessary to avoid using "Inline CSS" and proceed based on "Component" as much as possible. Because when there is a CSS change, changing it one by one from everywhere causes big problems.
  Line length in a file should never exceed 500 lines. If you have written more than 300 lines of code, you should check what you wrote, divide it into meaningful parts / use it by separating it into methods. You have to import from different files.
  Do not interfere with an object as directly as possible. You must create a new copy of the object and modify it.
  Do not try to change the state information without using setState.
  Avoid unnecessary if-else statements when you add the return statement in the if; the following statements do not work. So you don't need to use else.
  Instead of array.push(), array restructuring, and appending should be done.
- […previousArray, { newObjectElement1: newObjectElementValue1 }]
  Avoid Props Drilling. (If your props reach more than two component levels, you are doing "Props Drilling".)

I WANT TO CARRY MY REACT KNOWLEDGE FURTHER
MUST READ:

- https://reactjs.org/docs/thinking-in-react.html
- https://alexkondov.com/tao-of-react/
- https://www.patterns.dev/
- Learn the basics of Javascript very well.
- https://reactpatterns.com/
  Last Words:
  We have come to the end of the guide, where I try to convey my experiences with React. I hope you have gained helpful information for yourself and your team in this article.
  If you want to give helpful feedback on this guide, you can reach me on LinkedIn.
  - 
  I want to thank all my friends who helped me develop this guide with their feedback. :)
   -
  I'm thinking of collecting the guide you read in a git repo under "React Best Practices" and sharing it on Github.
  If you want to support me in this work and contribute to the development of the React ecosystem, you can give a star to the Github repo.
  GitHub Repo: https://github.com/emremutlu08/react-best-practices

---

You can join my LinkedIn network with +20,000 followers to follow my daily posts about React and JavaScript: https://www.linkedin.com/in/emremutlujs/
Resources and Examples:
https://code.visualstudio.com/docs/editor/whyvscode#:~:text=With%20support%20for%20hundreds%20of,navigate%20your%20code%20with%20ease.
https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics
https://deviq.com/principles/dont-repeat-yourself
https://www.freecodecamp.org/news/best-practices-for-react/amp/
https://www.freecodecamp.org/news/html-vs-jsx-whats-the-difference/
https://www.freecodecamp.org/news/top-javascript-concepts-to-know-before-learning-react/
https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716
https://gokhana.medium.com/single-responsibility-prensibi-nedir-kod-%C3%B6rne%C4%9Fiyle-soli%CC%87d-c8b1602be602
https://medium.com/dailyjs/applying-solid-principles-in-react-14905d9c5377
https://reactjs.org/docs/getting-started.html#learn-react
https://reactjs.org/docs/introducing-jsx.html
https://reactjs.org/docs/react-component.html#gatsby-focus-wrapper
https://reactjs.org/docs/rendering-elements.html
https://reactjs.org/docs/state-and-lifecycle.html
https://reactjs.org/docs/thinking-in-react.html
