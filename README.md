# CodeHaven
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Simple Chat</title>
</head>
<body>
<h1>Chat Room</h1>
<input type="text" id="messageInput" placeholder="Type a message">
<button onclick="sendMessage()">Send</button>
<ul id="messages"></ul>
 
    <script>
        const ws = new WebSocket('ws://localhost:3000');
        ws.onmessage = (event) => {
            const messages = document.getElementById('messages');
            const newMessage = document.createElement('li');
            newMessage.textContent = event.data;
            messages.appendChild(newMessage);
        };
 
        function sendMessage() {
            const input = document.getElementById('messageInput');
            ws.send(input.value);
            input.value = '';
        }
</script>
</body>
</html>
