### Job Listing


- Just Utah Coders is hiring three entry level interns as part of an ongoing education program for bootcamp graduates (or similar experience level). We are a nonprofit that builds software for other nonprofits and the government.

- is internship is structured as a "labor for tuition" arrangement. Just Utah Coders is experimenting with this format for the first time, with the following structure:

- Bootcamp or similar level of experience required. Our target audience is those who have graduated from bootcamp but have not found a software development job yet.

- 2 weekly hours of instruction from Daniel Kesler (@dckesler) in a classroom setting. Dan is a developer with several years of professional software development experience, as 2 weekly hours of mentoring from Daniel, Joel Denning (Executive Director and software well as professional software instruction experience developer), and others from Just Utah Coders.

- 10 hours of weekly coding hours expected from the interns, working on real projects for Just Utah Coders. These can be done remotely.

- All code written by the interns will be reviewed by experienced software developers at Just Utah Coders, providing you with consistent and valuable feedback on the code you author.

- This internship is unpaid and includes no health or other benefits. Laptops and other equipment will not be provided. The classroom instruction and personalized mentoring is what Just Utah Coders is offering in exchange for the 10 hours of labor.

- The internship can (of course) be put on your resume in your search for full time employment in a "Software Developer" position. It will last for 4 months (or until you get a full time software development job), with potential for extending it if both sides desire.

- The schedule for this internship is a bit non-standard, to fit the schedule of Just Utah Coders instructor, volunteers, and full time employees. Interns will be expected to be available in-person in the Salt Lake Area at the following times: Tuesday 10-12am, Wednesday 6-8pm, Sunday 3-5pm. Optional meetings include Tuesday at 6:30pm. All other hours are flexible and up to the intern.

## Joel is a Champion of 

1. https://single-spa.js.org/ which is a js router for front end microservices

2. this is a link to what front end micro services are and how it stacks up to other setups https://micro-frontends.org/ // THIS IS A MUST READ esp. how to create a custom element

            Lets take the buy button as an example. Team Product includes the button simply adding <blue-buy sku="t_porsche"></blue-buy> to the desired position in the markup. For this to work, Team Checkout has to register the element blue-buy on the page.

            class BlueBuy extends HTMLElement {
            connectedCallback() {
                this.innerHTML = `<button type="button">buy for 66,00 €</button>`;
            }

            disconnectedCallback() { ... }
            }
            window.customElements.define('blue-buy', BlueBuy);

            
            Now every time the browser comes across a new blue-buy tag, the connectedCallback is called. this is the reference to the root DOM node of the custom element. All properties and methods of a standard DOM element like innerHTML or getAttribute() can be used.

            Custom Element in Action

            When naming your element the only requirement the spec defines is that the name must include a dash (-) to maintain compatibility with upcoming new HTML tags. In the upcoming examples the naming convention [team_color]-[feature] is used. The team namespace guards against collisions and this way the ownership of a feature becomes obvious, simply by looking at the DOM.

![GitHub Logo](/monolith.png)
Format: ![microservices](url)

3. this is in regards to a twitter posting regarding import mapping and how they use it in their code. that import mapping was what i was describing looking at their code. 
https://github.com/WICG/import-maps


### Core Ideas behind Micro Frontends
- Be Technology Agnostic
Each team should be able to choose and upgrade their stack without having to coordinate with other teams. Custom Elements are a great way to hide implementation details while providing a neutral interface to others.
- Isolate Team Code
Don’t share a runtime, even if all teams use the same framework. Build independent apps that are self contained. Don’t rely on shared state or global variables.
- Establish Team Prefixes
Agree on naming conventions where isolation is not possible yet. Namespace CSS, Events, Local Storage and Cookies to avoid collisions and clarify ownership.
- Favor Native Browser Features over Custom APIs
Use Browser Events for communication instead of building a global PubSub system. If you really have to build a cross team API, try keeping it as simple as possible.
- Build a Resilient Site
Your feature should be useful, even if JavaScript failed or hasn’t executed yet. Use Universal Rendering and Progressive Enhancement to improve perceived performance.

