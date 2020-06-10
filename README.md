# Main BTTK Documentation Repository
## About
**BTTK** (**B**ot **T**ournament **T**ool**K**it) is an extendable web application for bot application tournaments.

This is an open-source tool written as a school project. Right now it's in very early stage of development.
## Documentation
- [Design document](DesignDocument/DESDOC.MD)

## Roadmap
- [ ] Initialize a project
    - [x] Draft a design document
    - [ ] Initialize code repositories
        - [ ] Front-end
        - [ ] Back-end
    - [ ] Write a minimal running boilerplate
    - [ ] Write a minimal test suite
        - [ ] Find a test framework
            - [ ] Python
            - [ ] TS
        - [ ] Write tests
            - [ ] Python
            - [ ] TS
    - [ ] Write a minimal DevOps configuration
        - [ ] GitHub Actions
            - [ ] Write CI Action
        - [ ] Pre-commit hooks
        - [ ] Test coverage
        - [ ] Quality audit
- [ ] Make a working prototype (v0.1.0)
    - [ ] Back-end
        - [ ] Add a bot
        - [ ] Run one competition between bots
    - [ ] Front-end
        - [ ] Add a bot
        - [ ] View bot list
        - [ ] Create a competition
        - [ ] Observe a competition
    - [ ] Create a deployment strategy
        - [ ] Write CD Action
        - [ ] Configure target environment
- [ ] Make a number of quality-of-life improvements (v0.2.0)
    - [ ] Back-end
        - [ ] Delete a bot
        - [ ] Start a tournament
        - [ ] Keep logs of all parties
    - [ ] Front-end
        - [ ] Delete a bot
        - [ ] View a result board
        - [ ] View all party logs from a board
- [ ] Add asynchronous functionality (v1.0.0)
    - [ ] Back-end
        - [ ] Multiple parties at the same time
        - [ ] Multiple tournaments at the same time
        - [ ] Separate party boards and tournament result boards
    - [ ] Front-end
        - [ ] View tournament lists
        - [ ] View party logs
- [ ] Add admin panel (v1.1.0)
    - [ ] Back-end
        - [ ] Add admin functionality with token login
        - [ ] Add admin REST endpoints for manipulating everything
        - [ ] Add bot rename for users
    - [ ] Front-end
        - [ ] Implement admin panel (too vague for details right now)