---
title: I created the exact same app in React and Vue. Here are the differences
author: oscar-raygoza
tags:
  - Development
  - Design
excerpt: REST
date: 2022-02-24T18:28:38.917Z
featuredImage: uploads/1-wrzdzndjcduhwqgopwmbhq.png
---
> [](https://sunilsandhu.medium.com/?source=post_page-----e9a1ae8077fd-----------------------------------)
>
> [](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fbookmark%2Fp%2Fe9a1ae8077fd&operation=register&redirect=https%3A%2F%2Fjavascript.plainenglish.io%2Fi-created-the-exact-same-app-in-react-and-vue-here-are-the-differences-e9a1ae8077fd&source=post_actions_header--------------------------bookmark_preview--------------)Having used Vue at work, I had a fairly solid understanding of it. I was, however, curious to know what the grass was like on the other side of the fence — the grass in this scenario being React.
>
> I’d read the React docs and watched a few tutorial videos and, while they were great and all, what I really wanted to know was how different React was from Vue. By “different”, I didn’t mean things such as whether they both had virtual DOMS or how they went about rendering pages. I wanted someone to take the time to explain the code! I wanted to find an article that took the time to explain this so that someone new to either Vue or React (or Web Development as a whole) could gain a better understanding of the differences between the two.
>
> Unfortunately, I couldn’t find anything that tackled this. So I came to the realisation that I would have to go ahead and build this myself in order to see the similarities and differences. In doing so, I thought I’d document the whole process so that an article on this will finally exist.
>
> *Note: there is a new version of this article that can be found here:*
>
> ## \[I created the exact same app in React and Vue. Here are the differences. [2021 Edition]](https://javascript.plainenglish.io/i-created-the-exact-same-app-in-react-and-vue-here-are-the-differences-2021-edition-a7ebfc19a9d)
>
> ### [React vs Vue. A side-by-side code comparison between Vue and React! 🎉](https://javascript.plainenglish.io/i-created-the-exact-same-app-in-react-and-vue-here-are-the-differences-2021-edition-a7ebfc19a9d)
>
> [javascript.plainenglish.io](https://javascript.plainenglish.io/i-created-the-exact-same-app-in-react-and-vue-here-are-the-differences-2021-edition-a7ebfc19a9d)
>
> ![](https://miro.medium.com/max/60/1*WRzDZndJCduHwqgOpWmbhQ.png?q=20)
>
> ![](https://miro.medium.com/max/700/1*WRzDZndJCduHwqgOpWmbhQ.png)
>
> Who wore it better?
>
> I decided to try and build a fairly standard To Do App that allows a user to add and delete items from the list. Both apps were built using the default CLIs (create-react-app for React, and vue-cli for Vue). *CLI stands for Command Line Interface by the way*. 🤓
>
> # Anyway, this intro is already longer than I’d anticipated. So let’s start by having a quick look at how the two apps look:
>
> ![](https://miro.medium.com/max/1400/1*mJ-qdNqldpgae2U5oS0qDg.png)
>
> Vue vs React: The Irresistible Force meets The Immovable Object
>
> The CSS code for both apps are exactly the same, but there are differences in where these are located. With that in mind, let’s next have a look at the file structure of both apps:
>
> ![](https://miro.medium.com/max/60/1*rahCwWEIXM7Wblk4L9ExYA.png?q=20)
>
> ![](https://miro.medium.com/max/700/1*rahCwWEIXM7Wblk4L9ExYA.png)
>
> Who wore it better?
>
> You’ll see that their structures are almost identical as well. The only difference here is that the React app has three CSS files, whereas the Vue app doesn’t have any. The reason for this is because, in create-react-app, a React component will have an accompanying file to hold its styles, whereas Vue CLI adopts an all encompassing approach, where the styles are declared inside the actual component file.
>
> Ultimately, they both achieve the same thing, and there is nothing to say that you can’t go ahead and structure your CSS differently in React or Vue. It really comes down to personal preference - you’ll hear plenty of discussion from the dev community over how CSS should be structured. For now, we’ll just follow the structure laid out in both CLIs.
>
> But before we go any further, let’s take a quick look at what a typical Vue and React component look like:
>
> ![](https://miro.medium.com/max/60/1*yQS8va-QXM2poiP-RqasOw.png?q=20)
>
> ![](https://miro.medium.com/max/700/1*yQS8va-QXM2poiP-RqasOw.png)
>
> Vue on the left. React on the right
>
> Now that’s out of the way, let’s get into the nitty gritty detail!
>
> **\*By the way if you’re enjoying this content so far,** I’ve just launched a YouTube channel! It would be amazing if you could support me by **[subscribing to my YouTube channel](https://www.youtube.com/channel/UCtipWUghju290NWcn8jhyAw?sub_confirmation=true)!***
>
> # **How do we mutate data?**
>
> But first, what do we even mean by “mutate data”? Sounds a bit technical doesn’t it? It basically just means changing the data that we have stored. So if we wanted to change the value of a person’s name from John to Mark, we would be ‘mutating the data’. So this is where a key difference between React and Vue lies. While Vue essentially creates a data object, where data can freely be updated, React creates a state object, where a little more legwork is required to carry out updates. Now React implements the extra legwork with good reason, and we’ll get into that in a little bit. But first, let’s take a look at the **data** object from Vue and the **state** object from React:
>
> ![](https://miro.medium.com/max/602/1*b9BjPHgneHv2K6ZYlAoe8A.png)
>
> ![](https://miro.medium.com/max/584/1*asy_vlGoZgtA3sAA7Dw4CA.png)
>
> Vue data object on the left. React state object on the right.
>
> So you can see that we have passed the same data into both, but they’re simply labelled differently. So passing initial data into our components is very, very similar. But as we’ve mentioned, how we go about changing this data differs between both frameworks.
>
> Let’s say that we have a data element called **name: ‘Sunil’**.
>
> In Vue, we reference this by calling **this.name**. We can also go about updating this by calling **this.name** **\= ‘John’**. This would change my name to John. I’m not sure how I feel about being called John, but hey ho, things happen! 😅
>
> In React, we would reference the same piece of data by calling **this.state.name**. Now the key difference here is that we cannot simply write **this.state.name** = ‘John’, because React has restrictions in place to prevent this kind of easy, care-free mutation-making. So in React, we would write something along the lines of **this.setState({name: ‘John’})**.
>
> While this essentially does the same thing as we achieved in Vue, the extra bit of writing is there because Vue essentially combines its own version of setState by default whenever a piece of data gets updated. So in short, React requires setState and then the updated data inside of it, whereas Vue makes an assumption that you’d want to do this if you were updating values inside the data object. So Why does React even bother with this, and why is setState even needed? Let’s hand this over to [Revanth Kumar](https://medium.com/@revanth0212) for an explanation:
>
> > “This is because React wants to re-run certain life cycle hooks, \[such as] componentWillReceiveProps, shouldComponentUpdate, componentWillUpdate, render, componentDidUpdate, whenever state changes. It would know that the state has changed when you call the setState function. If you directly mutated state, React would have to do a lot more work to keep track of changes and what lifecycle hooks to run etc. So to make it simple React uses setState.”
>
> ![](https://miro.medium.com/max/1136/1*IugEwe6Lkm5iFB-Q9zvc5w.jpeg)
>
> Bean knew best
>
> Now that we have mutations out of the way, let’s get into the nitty, gritty by looking at how we would go about adding new items to both of our To Do Apps.
>
> \*Enjoying this article? If so, get more similar content by **[subscribing to Decoded, my YouTube channel](https://www.youtube.com/channel/UCtipWUghju290NWcn8jhyAw)!***
>
> # **How do we create new To Do Items?**
>
> ## **React**:
>
> ```
>
> ```
>
> ## How did React do that?
>
> In React, our input field has an attribute on it called **value.** This value gets automatically updated through the use of a couple of functions that tie together to create something that feels similar to how Vue handles **two-way binding** (if you’ve never heard of this before, there’s a more detailed explanation in the ‘*How did Vue do that’* section after this). We create this by having an additional **onChange event listener** attached to the **input** field. Let’s quickly take a look at the **input** field so that you can see what is going on:
>
> ```
>
> ```
>
> The handleInput function is run whenever the value of the input field changes. It updates the **todo** that sits inside the state object by setting it to whatever is in the input field. This function looks as such:
>
> ```
>
> ```
>
> Now, whenever a user presses the **+** button on the page to add a new item, the **createNewToDoItem** function essentially runs this.setState and passes it a function. This function takes two parameters, the first being the entire **list** array from the state object, the second being the **todo** (which gets updated by the **handleInput** function). The function then returns a new object, which contains the entire **list** from before and then adds **todo** at the end of it. The entire list is added through the use of a spread operator (Google this if you’ve not seen this before — it’s ES6 syntax).
>
> Finally, we set **todo** to an empty string, which automatically updates the **value** inside the **input** field.
>
> ## **Vue:**
>
> ```
> createNewToDoItem = () => {
>     this.setState( ({ list, todo }) => ({
>       list: [
>           ...list,
>         {
>           todo
>         }
>       ],
>       todo: ''
>     })
>   );
> };
> ```
>
> ## **How did Vue do that?**
>
> In Vue, our **input** field has a handle on it called **v-model**. This allows us to do something known as **two-way binding**. Let’s just quickly look at our input field, then we’ll explain what is going on:
>
> ```
> createNewToDoItem = () => {
>     this.setState( ({ list, todo }) => ({
>       list: [
>           ...list,
>         {
>           todo
>         }
>       ],
>       todo: ''
>     })
>   );
> };
> ```
>
> V-Model ties the input of this field to a key we have in our data object called toDoItem. When the page loads, we have toDoItem set to an empty string, as such: **todo: ‘’**. If this had some data already in there, such as **todo: ‘add some text here’**, our input field would load with *add some text here* already inside the input field. Anyway, going back to having it as an empty string, whatever text we type inside the input field gets bound to the value for **todo**. This is effectively two-way binding (the input field can update the data object and the data object can update the input field).
>
> So looking back at the **createNewToDoItem()** code block from earlier, we see that we push the contents of **todo** into the **list** arrayand then update **todo** to an empty string.
>
> # **How do we delete from the list?**
>
> ## **React:**
>
> ```
> createNewToDoItem = () => {
>     this.setState( ({ list, todo }) => ({
>       list: [
>           ...list,
>         {
>           todo
>         }
>       ],
>       todo: ''
>     })
>   );
> };
> ```
>
> ## How did React do that?
>
> So whilst the deleteItem function is located inside **ToDo.js**, I was very easily able to make reference to it inside **ToDoItem.js** by firstly, passing the **deleteItem()** function as a prop on **<ToDoItem/>** as such:
>
> ```
> createNewToDoItem = () => {
>     this.setState( ({ list, todo }) => ({
>       list: [
>           ...list,
>         {
>           todo
>         }
>       ],
>       todo: ''
>     })
>   );
> };
> ```
>
> This firstly passes the function down to make it accessible to the child. You’ll see here that we’re also binding **this** as well as passing the key parameter, as key is what the function is going to use to be able to differentiate between which **ToDoItem** is attempting to delete when clicked. Then, inside the **ToDoItem** component, we do the following:
>
> ```
> createNewToDoItem = () => {
>     this.setState( ({ list, todo }) => ({
>       list: [
>           ...list,
>         {
>           todo
>         }
>       ],
>       todo: ''
>     })
>   );
> };
> ```
>
> All I had to do to reference a function that sat inside the parent component was to reference **this.props.deleteItem**.
>
> ## Vue:
>
> ```
> createNewToDoItem = () => {
>     this.setState( ({ list, todo }) => ({
>       list: [
>           ...list,
>         {
>           todo
>         }
>       ],
>       todo: ''
>     })
>   );
> };
> ```
>
> ## How did Vue do that?
>
> A slightly different approach is required in Vue. We essentially have to do three things here:
>
> Firstly, on the element we want to call the function:
>
> ```
> createNewToDoItem = () => {
>     this.setState( ({ list, todo }) => ({
>       list: [
>           ...list,
>         {
>           todo
>         }
>       ],
>       todo: ''
>     })
>   );
> };
> ```
>
> Then we have to create an emit function as a method inside the child component (in this case, **ToDoItem.vue**), which looks like this:
>
> ```
> createNewToDoItem = () => {
>     this.setState( ({ list, todo }) => ({
>       list: [
>           ...list,
>         {
>           todo
>         }
>       ],
>       todo: ''
>     })
>   );
> };
> ```
>
> Along with this, you’ll notice that we actually reference a **function** when we add **ToDoItem.vue** inside of **ToDo.vue**:
>
> ```
> createNewToDoItem = () => {
>     this.setState( ({ list, todo }) => ({
>       list: [
>           ...list,
>         {
>           todo
>         }
>       ],
>       todo: ''
>     })
>   );
> };
> ```
>
> This is what is known as a custom event-listener. It listens out for any occasion where an emit is triggered with the string of ‘delete’. If it hears this, it triggers a function called **onDeleteItem**. This function sits inside of **ToDo.vue,** rather than **ToDoItem.vue**. This function, as listed earlier, simply filters the **todo array** insidethe **data object** to remove the item that was clicked on.
>
> It’s also worth noting here that in the Vue example, I could have simply written the **$emit** part inside of the **@click** listener, as such:
>
> ```
>
> ```
>
> This would have reduced the number of steps down from 3 to 2, and this is simply down to personal preference.
>
> In short, child components in React will have access to parent functions via **this.props** (providing you are passing props down, which is fairly standard practice and you’ll come across this loads of times in other React examples), whilst in Vue, you have to emit events from the child that will usually be collected inside the parent component.
>
> # **How do we pass event listeners?**
>
> ## React:
>
> Event listeners for simple things such as click events are straight forward. Here is an example of how we created a click event for a button that creates a new ToDo item:
>
> ```
>
> ```
>
> Super easy here and pretty much looks like how we would handle an in-line onClick with vanilla JS. As mentioned in the Vue section, it took a little bit longer to set up an event listener to handle whenever the enter button was pressed. This essentially required an onKeyPress event to be handled by the input tag, as such:
>
> ```
>
> ```
>
> This function essentially triggered the **createNewToDoItem** function whenever it recognised that the ‘enter’ key had been pressed, as such:
>
> ```
>
> ```
>
> ## **Vue:**
>
> In Vue it is super straight-forward. We simply use the **@** symbol, and then the type of event-listener we want to do. So for example, to add a click event listener, we could write the following:
>
> ```
>
> ```
>
> Note: **@click** is actually shorthand for writing **v-on:click**. The cool thing with Vue event listeners is that there are also a bunch of things that you can chain on to them, such as .once which prevents the event listener from being triggered more than once. There are also a bunch of shortcuts when it comes to writing specific event listeners for handling key strokes. I found that it took quite a bit longer to create an event listener in React to create new ToDo items whenever the enter button was pressed. In Vue, I was able to simply write:
>
> ```
>
> ```
>
> ## **How do we pass data through to a child component?**
>
> ## React:
>
> In react, we pass props onto the child component at the point where it is created. Such as:
>
> ```
>
> ```
>
> Here we see two props passed to the **ToDoItem** component. From this point on, we can now reference them in the child component via this.props. So to access the **item.todo** prop, we simply call **this.props.item**.
>
> ## Vue:
>
> In Vue, we pass props onto the child component at the point where it is created. Such as:
>
> ```
>
> ```
>
> Once this is done, we then pass them into the props array in the child component, as such: **props: \[ ‘todo’ ]**. These can then be referenced in the child by their name — so in our case, **‘todo**’.
>
> # **How do we emit data back to a parent component?**
>
> ## React:
>
> We firstly pass the function down to the child component by referencing it as a prop in the place where we call the child component. We then add the call to function on the child by whatever means, such as an **onClick**, by referencing **this.props.whateverTheFunctionIsCalled**. This will then trigger the function that sits in the parent component. We can see an example of this entire process in the section *‘How do we delete from the list’.*
>
> ## Vue:
>
> In our child component, we simply write a function that emits a value back to the parent function. In our parent component, we write a function that listens for when that value is emitted, which can then trigger a function call. We can see an example of this entire process in the section *‘How do we delete from the list’.*
>
> # **And there we have it!** 🎉
>
> We’ve looked at how we add, remove and change data, pass data in the form of props from parent to child, and send data from the child to the parent in the form of event listeners. There are, of course, lots of other little differences and quirks between React and Vue, but hopefully the contents of this article has helped to serve as a bit of a foundation for understanding how both frameworks handle stuff 🤓
>
> If you found this useful, be sure to give lots and lots of claps 👏 . *Hint, you can leave up to 50!* You can also get more similar content by **[subscribing to my YouTube channel](https://www.youtube.com/channel/UCtipWUghju290NWcn8jhyAw?sub_confirmation=true)!**
>
> ## Translations
>
> *[Chinese](https://zhuanlan.zhihu.com/p/41623240)*
>
> *[Indonesian](https://medium.com/@fauzanlubis23/membuat-aplikasi-yang-sama-dengan-menggunakan-react-dan-vue-inilah-perbedaannya-202ae7784cd2)*
>
> *[Japanese](https://medium.com/@ochrotomys.nuttalli/react%E3%81%A8vue%E3%81%A7%E5%90%8C%E3%81%98%E3%82%A2%E3%83%97%E3%83%AA%E3%82%92%E4%BD%9C%E6%88%90%E3%81%97%E3%81%A6%E3%82%8F%E3%81%8B%E3%81%A3%E3%81%9F%E3%81%93%E3%81%A8-%E9%81%95%E3%81%84%E3%81%AF%E3%81%93%E3%81%93%E3%81%AB%E3%81%82%E3%81%A3%E3%81%9F-8013cfedf9f0)*
>
> *[Korean](https://medium.com/@erwinousy/%EB%82%9C-react%EC%99%80-vue%EC%97%90%EC%84%9C-%EC%99%84%EC%A0%84%ED%9E%88-%EA%B0%99%EC%9D%80-%EC%95%B1%EC%9D%84-%EB%A7%8C%EB%93%A4%EC%97%88%EB%8B%A4-%EC%9D%B4%EA%B2%83%EC%9D%80-%EA%B7%B8-%EC%B0%A8%EC%9D%B4%EC%A0%90%EC%9D%B4%EB%8B%A4-5cffcbfe287f)*
>
> *[Persian](http://blog.loremsaz.com/%D8%A7%DB%8C%D8%AC%D8%A7%D8%AF-%DB%8C%DA%A9-%D8%A8%D8%B1%D9%86%D8%A7%D9%85%D9%87-%DB%8C%DA%A9%D8%B3%D8%A7%D9%86-%D8%AF%D8%B1-vue-%D9%88-react-%D8%AA%D9%81%D8%A7%D9%88%D8%AA-%D8%AF%D8%B1-%DA%86%DB%8C/)*
>
> *[Polish](https://geek.justjoin.it/napisalem-aplikacje-vue-reactcie-zobaczie-roznice/)*
>
> *[Portuguese](https://medium.com/javascript-in-plain-english/criei-o-mesmo-app-em-react-e-vue-eis-as-diferen%C3%A7as-2455d86d173c)*
>
> *[Russian](https://habr.com/company/ruvds/blog/419373/)*
>
> *[Spanish](https://medium.com/@marianvilla/cre%C3%A9-la-misma-aplicaci%C3%B3n-en-react-vue-aqu%C3%AD-las-diferencias-605465a2e18c)*
>
> [Taiwanese](https://ithelp.ithome.com.tw/articles/10201091)
>
> *If you are interested in making this article more accessible by translating into another language, please feel free to do so* — *let me know if you do so that I can add a link to it on this page.* 😄
>
> ## Why didn’t you use React Hooks or the Vue Composition API?
>
> There is actually an updated version of this article that uses them both! **[The latest edition be read here](https://sunilsandhu.com/posts/i-created-the-exact-same-app-in-react-and-vue-2020-edition)**! But before you click the link, be sure to leave some claps on this article if you enjoyed reading it, as they help to support the work that we are doing.
>
> ## Where’s the Angular comparison?
>
> I’m glad you asked! Because
>
> [Sam Borick](https://medium.com/u/64aa2d000776?source=post_page-----e9a1ae8077fd-----------------------------------)
>
> has written [Part 2](https://medium.com/javascript-in-plain-english/i-created-the-exact-same-app-in-react-and-vue-part-2-angular-39b1aa289878) of this article.
>
> ## Now do it in Svelte!
>
> Already done — [It’s right here](https://medium.com/javascript-in-plain-english/i-created-the-exact-same-app-in-react-and-svelte-here-are-the-differences-c0bd2cc9b3f8)!
>
> ## What about \[insert framework/library]?
>
> [HyperApp](https://dev.to/citizen428/fighting-boredom-with-a-hyperapp-experiment-12a)
>
> [AppRun](https://medium.com/@yiyisun/i-also-created-the-exact-same-app-using-apprun-dd1860cb8112)
>
> [LitElement](https://medium.com/@westbrook/litelement-to-do-app-1e08a31707a4)
>
> [Hyperstack](https://medium.com/@mitch_23203/the-exact-same-app-in-hyperstack-7f281cef46ca)
>
> [Stimulus + Rails](https://mariochavez.io/desarrollo/2019/12/23/i-created-the-same-app-with-rails-and-javascript.html)
>
> If you’re interested in forking the styles used in this article and want to make your own equivalent piece, please feel free to do so! And be sure to let me know so that I can add a link to your article 👍
>
> ## Github links to both apps:
>
> Vue ToDo: <https://github.com/sunil-sandhu/vue-todo>
>
> React ToDo: <https://github.com/sunil-sandhu/react-todo>
>
> ## I recently spoke about this article at London Web Performance
>
> Watch the talk here! <https://www.youtube.com/watch?v=dnNF8szmxXg>
>
> ## **A note from the Plain English team**
>
> Did you know that we have three publications? Show some love by giving them a follow: **[JavaScript in Plain English](https://medium.com/javascript-in-plain-english)**, **[AI in Plain English](https://medium.com/ai-in-plain-english)**, **[Python in Plain English](https://medium.com/python-in-plain-english)** — thank you and keep learning!
>
> And as always, Plain English wants to help promote good content. If you have an article that you would like to submit to any of our publications, send an email to **[submissions@plainenglish.io](mailto:submissions@plainenglish.io)** with your Medium username and what you are interested in writing about and we will get back to you!