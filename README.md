# node-dalle2

# Setup
To get access to Dalle-2's API you need to join the waitlist and wait to be accepted which can be found [here](https://labs.openai.com/waitlist).

1. To get the your unique session key you need to go to [https://labs.openai.com/](https://labs.openai.com/).
2. Open the Network Tab in Developer Tools in your browser.
3. Send an image request in the input box.
4. In the network tab you'll find a POST request to [https://labs.openai.com/api/labs/tasks](https://labs.openai.com/api/labs/tasks).
5. In the POST request headers you'll find your session key in the "Authorization" header, it'll look something like "sess-xxxxxxxxxxxxxxxxxxxxxxxxxxxx".

# Usage

```sh
npm i node-dalle2
```

```js
import { Dalle } from "node-dalle2";


// Add Session key
const dalle = new Dalle({ apiKey: "sess-xxxxxxxxxxxxxxxxxxxxxxxxxxxx" });

// Create an async function 
const getDalle2Images = async (caption) => {
    const generatedImages = await dalle.generate(caption);

    return generatedImages;
}

// Call the function with top level await
const { data } = await getDalle2Images("Man in a suit riding a horse during the medieval times");

// Log the response
console.log(data);

// Or use .then syntax
getDalle2Images("Man in a suit riding a horse during the medieval times").then(
  ({ data }) => {
    console.log(data);
  }
);
```
### Output
```
[
  {
    id: 'generation-QyXXdJP165TiSpSrzBqAo6IS',
    object: 'generation',
    created: 1659149946,
    generation_type: 'ImageGeneration',
    generation: {
      image_path: 'https://openailabsprodscus.blob.core.windows.net/private/...'
    },
    task_id: 'task-QCKmkq8rxg0ablIgiXizTn0y',
    prompt_id: 'prompt-IN4gE4yFBTi4MPlEG3GzCE4R',
    is_public: false
  },
  {
    id: 'generation-UNJiRu5dzbvJYo8FVnZs5SCS',
    object: 'generation',
    created: 1659149946,
    generation_type: 'ImageGeneration',
    generation: {
      image_path: 'https://openailabsprodscus.blob.core.windows.net/private/...'
    },
    task_id: 'task-QCKmkq8rxg0ablIgiXizTn0y',
    prompt_id: 'prompt-IN4gE4yFBTi4MPlEG3GzCE4R',
    is_public: false
  },
  {
    id: 'generation-XCqpvMF0araPjFczwwfDGHGv',
    object: 'generation',
    created: 1659149946,
    generation_type: 'ImageGeneration',
    generation: {
      image_path: 'https://openailabsprodscus.blob.core.windows.net/private/...'
    },
    task_id: 'task-QCKmkq8rxg0ablIgiXizTn0y',
    prompt_id: 'prompt-IN4gE4yFBTi4MPlEG3GzCE4R',
    is_public: false
  },
  {
    id: 'generation-sSo1TufL7d4OSGEBTwRTMtxv',
    object: 'generation',
    created: 1659149946,
    generation_type: 'ImageGeneration',
    generation: {
      image_path: 'https://openailabsprodscus.blob.core.windows.net/private/...'
    },
    task_id: 'task-QCKmkq8rxg0ablIgiXizTn0y',
    prompt_id: 'prompt-IN4gE4yFBTi4MPlEG3GzCE4R',
    is_public: false
  }
]
```

### Get the first image URL
```js
const firstImage = data[0].generation.image_path; 
console.log(firstImage);
```
### Output
``` 
'https://openailabsprodscus.blob.core.windows.net/private/...'
```