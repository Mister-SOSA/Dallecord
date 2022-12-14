## Installation

### Dependencies
- [Python-Dalle](https://pypi.org/project/Python-DALLE/)
- [PyCord](https://docs.pycord.dev/en/stable/)

### Loading the Cog
To install this cog, place `dallecord.py` in the directory that your bot loads other cogs from.
This directory should be defined in your main script.
In most cases, the directory is simply `./cogs/`

You can also load the cog manually like so:
```py
client.load_extension(f'dallecord')
```

### Obtaining a SESS key
To use the Dalle2 API, you must obtain your session key from the OpenAI website.
1) Create an account or log in to an existing one at the [Dalle2 Homepage](https://openai.com/dall-e-2/)
2) Navigate to the [Generation Page](https://labs.openai.com/)
3) Open the developer tools (F12) and navigate to the Network tab
4) Type in a prompt and click the `Generate` button
5) In the Network tab, find the request to `https://labs.openai.com/api/labs/tasks`
6) Scroll down to the `Request Headers` section and copy the value of the `Authorization` header. You only need the value after `Bearer `.
   
Once you have your session key, you can set it in the cog like so:
```py
dalle = Dalle2('SESS-KEY') # Replace with your session key
```
Ideally, you should keep your session key in a separate file and load it dynamically.
This is to prevent your session key from accidentally being published or leaked.

## Customizing the Command
Near the top of the file, you will find a few variables that you can customize.
```py
cmd_metadata = {
    'name': 'dalle2',
    'aliases': ['dalle'],
    'description': 'Generates an image from a prompt.'
}
```
This is the metadata for the command. You can change the name, aliases, and description to whatever you want.

`name` is the name of the command. This value will appear in the list of application commands when you initiate one with `/` in a channel.

`aliases` is a list of aliases for the command. These are alternative names that you can use to invoke the command. An alias cannot be the same as the name or you will get an error.

`description` is the description of the command. This will appear in the list of application commands when you initiate one with `/` in a channel.

## Usage
Once you have the cog loaded, you can invoke the command like so:
```
/dalle2 <prompt>
```
The prompt can be anything you want. It can be a sentence, a paragraph, or even a whole story. The prompt is what the model will use to synthesize the image.

The command requires a prompt to be provided. If you do not provide one, the command will not be invoked.
This will prevent any unintentional requests to the API.

![No Prompt Provided Image](https://github.com/Mister-SOSA/Dallecord/blob/main/readme/no_prompt.png?raw=true)

The results will appear in the channel as an embed. The embed will contain the prompt, and four images generated by the model.
## Examples
```
/dalle2 A photorealistic image of an astronaut eating a hotdog at the bottom of the ocean
```
![Querying Image](https://github.com/Mister-SOSA/Dallecord/blob/main/readme/querying.png?raw=true)

The bot will send this embed until the server responds. Once the server responds, the embed will be updated with the results.

![Results Image](https://github.com/Mister-SOSA/Dallecord/blob/main/readme/result.png?raw=true)
