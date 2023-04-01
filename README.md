# backseat.nvim
### A neovim plugin that uses GPT to highlight and explain code readability issues
![image](https://user-images.githubusercontent.com/32351696/229299250-1fcb4135-2a6a-4663-9637-13af7c0ee7cd.png)

# Commands
| User Command | Purpose |
| -- | -- |
| `:Backseat`  | Sends the current buffer to OpenAI to highlight readability feedback |
| `:BackseatAsk <question>` | Ask a question about the code in the current buffer (i.e What does the function on line 20 do?, Summarize this code)
| `:BackseatClear` | Clear all Backseat highlighting from the current buffer
| `:BackseatClearLine` | Clear the current line of Backseat highlighting

Requires curl to be installed. If a buffer contains more than 100 lines, it will be split into multiple <= 100 line requests. 
# Install
### Lazy plugin manager
```lua
    {
        name = "james1236/backseat.nvim",
        config = function()
            require("backseat").setup({
                openai_api_key = 'sk-xxxxxxxxxxxxxx', -- Get yours from platform.openai.com/account/api-keys
                openai_model_id = 'gpt-3.5-turbo', --gpt-4
                
                -- additional_instruction = "Respond snarkily", -- (GPT-3 will probably deny this request, but GPT-4 complies)
                -- highlight = {
                --     icon = '', -- ''
                --     group = 'Comment',
                -- }
            })
        end
    },
```
### The result of using `additional_instruction = "Respond snarkily"`
![image](https://user-images.githubusercontent.com/32351696/229297495-6d145848-10bf-43eb-8c2a-ab4264f514b1.png)

# Config 
| Global Name | Setup Table Name | Default | Purpose |
| --- | --- | --- | -- |
`vim.g.backseat_openai_api_key` | `openai_api_key` | `nil` | Your OpenAI API key, needed to access language models
`vim.g.backseat_openai_model_id` | `openai_model_id` | `'gpt-3.5-turbo'` | The model's identifier, such as gpt-3.5-turbo and gpt-4
`vim.g.backseat_additional_instruction` | `additional_instruction`, | `nil` | An additional instruction to give the AI, like "Make your responses more brief"
`vim.g.backseat_highlight_icon` | `highlight.icon` | `''` | The sign column icon to display for each line containing suggestions
`vim.g.backseat_highlight_group` | `highlight.group` | `'String'` | The `:hi` highlight color group for the icon and the suggestion text 
