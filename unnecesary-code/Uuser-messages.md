# User messages not showing up? Guess I will just add it!

I have shortened the code in this example, so that it only shows relevant parts.

The LLM generated this code for the button.click flow, which looks fine.

```python
  ...
  send_btn.click()            
    .then(add_user_msg) // Add the users new message
    .then(chat_stream) // Stream the text to the llm
    .then(end_stream) // Finish stream, close connection
  ...
```

The add_user_msg function has the following line of code, which is expected:

```python
  ...
    chat_state_plain.append(gr.ChatMessage(role='User', content=user_message))
    chat_state_html.append(gr.ChatMessage(role='User', content=user_message))
  ...
```

Until, you realize that chat_stream has the following line of code:

```python
  ...
    chat_state_plain.append(gr.ChatMessage(role='user', content=user_message))
    chat_state_html.append(gr.ChatMessage(role='user', content=user_message))
  ...
```

At first glance, I thought the LLM was simply confused and didn’t realize it was appending the user message twice.
Even though the user message appeared only once in the UI, I assumed that was because the messages were identical 
and the component automatically filtered out duplicates.

So I removed the lines in the chat_stream function... aaaand the user messages were gone.
It turns out, that the llm in fact wrote the append_user_msg function incorrectly by using the keyword 'User' instead of 'user'.
Which means that function was actually doing nothing.

Because I coupled the deletion in chat_stream with _alot_ of other changes (that my bad I suppose...) it took me quite
a while to figure out why the user_messages were not showing up anymore. 

