![Image for guide](https://source.unsplash.com/5vGeVxQq9Vs)

### About

- This is a short introduction to typescript and how we can use it in an application built with the popular frontend framework, ReactJS

- to git clone this repo, use: https://github.com/grokkingcoding/super-short-guide-to-typescript-2.git

### Super Short Guide To TS 2

1. So how do we normally use functional components? For example, if we want to render a list, we may want to splt a list component into the following components.

- An Items component

```
const Item = (props) => {
  rewturn<>
  <li>props.username</li>
  </>
};
```

- A List component

```
const List = (props) => {
  rewturn<>
  <ul>
  {
    props.different_users.length > 0 ?
      props.different_users.map(user => (
        <Item props={user}>
      )) : <></>
  }
  </ul>
  </>
};
```

So we have an item and a list component. And we need to do type checking for both the props going into the two components. For the list component, we should check that the props passed in is of type array.

2. How do I use Typescript in a React functional component?

Very often, we usually pass props into a functional component and it is for the props that we pass in that we need to type checking for.

For exmaple, what kind of type checking can we do for the following functional component?

```
const WelcomeBox = (props) => <ul>
<li>props.date</li>
<li>{props.welcome_message + props.username}</li>
</ul>
```

So what should the props object passed into WelcomeBox look like? It should look like the following:

```
let user = {
  username: 'James',
  date: 12332423423,
  welcome_message: 'Welcome back'
}
```

- If we do not specify a type then typescript will give it a type of "any". So in the above component, "props" is given a type of "any".

3. How do we make the "WelcomeBox" component strongly typed?

We would do something like this:

```
const WelcomeBox = (props: { username: string, date: number, welcome_message: string }) => <ul>
<li>props.date</li>
<li>{props.welcome_message + props.username}</li>
</ul>
```

So waht do you think will happen now if we use the "WelcomeBox" component like this:

```
render(<WelcomeBox/>, rootElement);
```

- The answer is we would get a "type error" as no props are passed in.

4. How do we fix the type error? We just need to pass in props like this:

```
render(<WelcomeBox props={{date: 25672356735, username: 'James', welcome_message: 'Welcome back,'}} />, rootElement);
```

5. If we have many props to pass into the functional component, we could do something like this to make our code more readable:

```
type Props = { username: string, date: number, welcome_message: string }
const Hello = ({ username, date, welcome_message }: Props) =>...
```

6. That's it! You now have a strongly typed functional component that makes it easy for other developers to work with.
