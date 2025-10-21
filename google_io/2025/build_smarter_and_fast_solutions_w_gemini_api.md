# Build Smarter and Faster Smarter Models w/ Gemini API

- `response_modalities`
    - When using `imagen` you just get an image
    - When using `gemini` you can use different modalities
        - E.g. `text` + `image` gives images and text inter-mingled (e.g. cookbook) 
- analysing video
    - E.g. pass YT video and ask questions:
        - "How many times does the person say "x"
        - "Summarise the video"
    - Clipping via `start_offset` and `end_offset`
    - Limit frame size via `resolution`
    - Limit frames analysed via `fps`
- agents
    - using adk
    - deployable via cloud run, k8s, anything
    - user experience is like a regular chatbot but behind we have a lot more control
