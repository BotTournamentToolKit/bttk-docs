# Design Document for BTTK

## End product description

### Basic description

BTTK is an extendable web application for hosting bot tournaments. It is modular, which makes extending it for different games easier.

BTTK consists of two parts: back-end and front-end.

Back-end provides a REST API for managing bots and tournaments as well as observing ongoing games.

Front-end mainly serves as a visualization and control tool, providing UI for users.

### Extendability

Extandability is reached by using abstactions with as litle exposed API as possible. This way the user will not spend as many time on trying to integrate their code into the codebase. Instead, they can write their logic in their own way, only exposing a couple of required methods.

#### Extendability in back-end

For each game, two classes should be written: 
- One implementing `Game`, that stores a game-specific state and can use bots to make turns.
- One implementing `Bot`, that allows a corresponding `Game` to easily manipulate a written application, for example, by traslating a field structure into text, giving it to an actual bot, decoding its answers, then changing `Game` state depending on this

For each bot file format, a class should be written.
It should implement `Executor`, allowing to feed field state to a bot and return a bot's turn.

In pseudocode, these interfaces will look like this:
```python=
class Game:
    @property
    def json_state() -> Map<str, ???>:
        throw NotImplementedError()
        
    def turn():
        throw NotImplementedError()
        
class Bot:
    def turn(field: Field) -> Turn:
        throw NotImplementedError()
    
class Executor:
    def turn(field: str) -> str:
        throw NotImplementedError
```

#### Extendability in front-end

For each game a react component should be written, accepting a `state` prop and rendering it to DOM. As JSON `state` representation is implemented by an extender in `Game::json_state()`, they don't need to adhere to any given standart, which grants them a measure of fluidity.

An example of this:
State JSON representation:
```json=
{
    "count": 15
}
```

Renderer component:

```typescript=
Matches = (props: any) => {
    {state} = props;
    {count} = state;
    
    return <span> Matches: { count } </span>
}
```



## Tech stack

### Back-end

Language: Python 3.7

Language features: `typing`, `asyncio`

Web framework: `sanic`

ORM: `peewee`

### Front-end

HTML+CSS+TypeScript+React.

For request use Fetch API.

### Formatting

- `black` for Python
- `prettier` for TS

### IDE

- `PyCharm` for Python
- `WebStorm` for TS

### Unit Tests

TODO

### DevOps

- GitHub Actions for CI
- CodeCov for coverage reports
- Pre-commit for hooks
- TODO: Maybe other services for something else?

## Commit naming conventions:

- Write in English only
- Write in infinitive 
  Do this
  ```
  add function foo
  ```
  Not this
  ```
  added function foo
  ```
- Make the first commit line (the title) a summary of a commit, 
  then write down details on other lines
  
- If closing some issue, tag it in a commit (TODO Tutorial)

## Branch hygiene:

- Create a branch for every feature you want to add.
- Rules for commit titles apply to branch names
- Use `-` for as word separators, not `_` (`function-foo`, not `function_foo`)
- Use `feature-{name}`, when implementing features, `fix-{name}`, when fixing bugs, `misc-{name}` when doing something else. This list isn't complete - you can propose new prefixes!
- Do not merge to `master` - open a pull request instead! This way your code can be checked before merge.
- Do not, under any circumstances, commit anything to `master`, period. Make a branch, implement a change, make a PR.
  - This does not apply when initializing repositories, obviously. Make a thing that builds, *then* freeze master.
- Mark versions with tags formatted as `v{major}.{minor}.{patch}`. Patches do not change functionality significantly, minor versions don't introduce breaking changes. Consult with others before pushing a tag, please!