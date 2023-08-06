# Q1. Async & Defer execution order

Put the scripts in the right order of execution
A. <script async src="async1.js" /> // Loads in 300 ms
B. <script defer src="defer1.js" /> // Loads in 200 ms
C. <script defer src="defer2.js" /> // Loads in 300 ms
D. <script async src="async2.js" /> // Loads in 50 ms
E. <script async defer src="asyncdefer1.js" /> // Loads in 60 ms

R:
D. <script async src="async2.js" /> // Loads in 50 ms
E. <script async defer src="asyncdefer1.js" /> // Loads in 60 ms
A. <script async src="async1.js" /> // Loads in 300 ms
B. <script defer src="defer1.js" /> // Loads in 200 ms
C. <script defer src="defer2.js" /> // Loads in 300 ms

Async -> not blocking the parsing of html, it runs the script as soon as it finds it, whithout blocking the parsing

Defer -> waiting for html parsing to be done and after it's starting to run

# Q2. Rendering Pipeline & Composition

Which statements are true?

A. The render tree contains all elements from the DOM and CSSOM combined

B. Compositing is the process of separating layers based on z-index, which are then combined to form the final image displayed on the screen

C. The layout process asigns colors and images to visual elements in the render tree

D. The compositing process happens on the compositor thread

E. Elements that aren't visible on the page, for example display: hidden, aren't part of the DOM tree

R:
Only D is true. (The compositor thread is a thread in the browser that leverages the GPU to create the final version of the page seen on the screen)

# Q3. Resolving Domain Requests

1. Browser sends request to Recursive DNS Resolver
2. Recursive DNS Resolver queries Root Name Server
3. Root Name Server responds with Top Level Domain Name Server IP Address
4. Recursive DNS Resolver queries Top Level Domain Name Server
5. Top Level Domain Name Server responds with Authoritative Name Server IP Address
6. Recursive DNS Resolver queries Authoritative Name Server
7. Authoritative Name Server responds with website's IP Address.

# Q.4 Call Stack & Event Loop

What gets logged?

    setTimeout(() => console.log(1))

    Promise.resolve().then(() => console.log(2))

    Promise.resolve().then(() => setTimeout(() => console.log(3)))

    new Promise(() => console.log(4))

    setTimeout(() => console.log(5))

It gets logged: 4 2 1 5 3

# Q.5 Resource Hints

Match the resource hints with their definitions

dns-prefetch -> performs domain name resolution in the background

preconnect -> proactively performs DNS resolution and TCP/TLS handshake

prefetch -> downloads resources that are likely to be needed in the future

preload -> prioritizes fetching of critical resources needed for the current navigation

# Q.6 Object Reference & Destructuring

What's the output?

    const member = {
    name: "Jane",
    address: { street: "101 Main St" }
    }

    const member2 = { ...member }

    member.address.street = "102 Main Str"
    member.name = "Sarah"

    console.log(member2)

R:

    {
    name: "Jane",
    address: { street: "102 Main Str" }
    }

# Q.7 Performance Navigation Timing

Put the performance navigation timings in the right order

1. fetchStart
2. connectEnd
3. domInteractive
4. domContentLoadedEventStart
5. domComplete
6. loadEventStart

# Q.8 Cache Directives

1. no-cache -> validates a cached response with the origin server before using it, even if it is still fresh
2. must-revalidate -> validate a stale response with the origin server before using it
3. no-store -> doesn't cache any part of the request or response
4. private -> prevents caching on shared catches
5. stale-while-revalidate -> serves stale content while validating the cached response with the origin server

# Q.9 Garbage Collection

What is true about this code block?
function addMember(name) {
return { name, createdAt: Date.now() }
}

    let obj1 = addMember("John");
    let obj2 = addMember("Sarah);

    obj1.friend = obj2;
    obj2.friend = obj1;
    obj1 = null;
    obj2 = null;

R:

1. obj1 and obj2 objects will not be garbage collected, learing to memory leak
2. obj1 and obj2 objects will be garbage collected imediatelly after setting them to null
3. obj1 and obj2 will only be garbage collected after closing the browser tab
4. obj1 and obj2 objects can be garbage collected during the next garbage collection cycle

Correct Response: 4

# Q.10 Animation Cost

When animating the following properties which have the correctly listed rendering costs?

width: Layout > Paint > Composite TRUE

opacity: Paint > Composite

background-image: Composite

left: Layout > Paint > Composite TRUE

transform: Paint > Composite

# Q.11 Event Propagation

What gets logged when clicking the button?

    <div class="outer">
        <div class="inner">
            <button>Click me!</button>
        </div>
    </div>

    outer.addEventListener("click", () => log("A"), true)
    outer.addEventListener("click", () => log("B"))
    inner.addEventListener("click", () => log("C"), true)
    inner.addEventListener("click", (e) => {
    log("D");
    e.stopPropagation();
    log("E")
    })

    button.addEventListener("click", () => log("F"))
    button.addEventListener("click", () => log("G"), true);

It gets logged:
A C G F D E

# Q.12 CSS Specificity

Order the CSS selectors by specificity
(highest to lowest)
