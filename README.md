## Installation
1. Clone the repo.
2. Make sure you have [yarn setup](https://yarnpkg.com/en/docs/install#mac-stable).
3. Open the project directory, and type `yarn`. This will install the dependencies.
4. `yarn serve` will start a web server at [`localhost:8080`](localhost:8080).

## Notes
I chose to use Vue because it's the front-end framework I'm most familiar with. It's very similar to React in a lot of ways, just a little more opinionated, and I have a strong preference for Vuex to Redux. It gave me a little more comfort to do some cool stuff.

I've made this to meet my own visual criteria on Chrome, and tested briefly on Safari and Firefox, but not thoroughly. Firefox has some mobile rendering issues, but otherwise all functionality appears to work across those three browsers.

### Bonuses
- **Responsive.** I made the site as responsive as I could without going too deep. We're working with a lot of data to display so I made some design choices to accomodate that. When you don't have enough horizontal table space to display the whole table, it allows you to scroll horizontally, but keep the player names visible, so that you can know whose stats you're looking at. There's also some design changes that occur on portrait screens, including stacking the `sort` buttons, reduced copy, etc.
- **Accessibility.** In order to make sure things are as readable as possible for as wide an audience as possible I've added some accessibility features. I didn't go full `aria-label`, but rather visual choices. Table cells are highlighted on hover, as well as the row to better bring the users eye to the player's name. 
Additionally, all of the table cells have a title on hover so that you know which stat you're looking at if you can't see the table headers.
- **Design.** I tried to mimic the Score's designs as they exist. If you check out the `App.vue` file, you'll see we're using CSS variables that fall in line with the Score's palette. This means we can update our designs/colours in one place and see it cascade throughout the app. I also added some Score blue accents in the buttons and `selected` states for the sort features. I also tried to design it with very classic sports tables in mind aesthetically.
- **Reversible.** All of the sort functions offer a reversible sort if clicked a second time. The caret next to the sorted button tells you which way they're presently sorted.
- **CSV file name.** It wasn't listed in the requirements, but I made it easy to set the file name for the CSV export. That way, in the future, you could add the filter criteria to the name to help organize things.

### Next Steps
If I were to sit down and continue on this, I'd probably add a few features:
- **Query strings.** Given that all our filtering and sorting criteria is straight-forward, I'd add query strings, so that users would be able to share links directly.
- **API powered.** Rather than complicate things by adding a back-end to this, I've chosen to use the JSON provided as if it were provided by the API. I've got the router set-up and ready to support this.
- **Data sanitization.** Your front-end shouldn't need to co-erce any data, and you shouldn't have un-uniform data going into your database. Right now to navigate this the app does some sanitization to work the data correctly, but it won't fail with clean code, so it's not locked into bad behaviour.
- **Anchor table headers.** If I could anchor the table headers on scroll in pure CSS I'd do that for usability with large datasets and small screens.
- **Fuzzy search/filter.** Worth considering, but probably not actually necessary. Filter isn't case sensitive, and I feel, as a user, I'd be frustrated seeing names similar to what I've filtered but not precise. It also adds a lot of weight.
- **Refactoring.** There's a few refactors I see I'd like to make already. For example, given that we have the list of headers already, we could use that to generate the headers dynamically, but I've left it as is because despite it being a straight-forward enough fix, it'd also reduce code readability, and I know the Score is a React company and I didn't want to obfuscate anything.

### Questions?
If you have any questions, let me know! I had fun making this and trying to make it in a way that would resemble what you'd expect in the wild. 