```
try {
    var params = JSON.parse(value);
    var req = new HttpRequest();

    req.addHeader('Content-Type: application/json');

    var mensaje = {
        chat_id: params.To,
        text: params.Subject + "\n" + params.Message
    };

    var url = 'https://api.telegram.org/bot' + params.Token + '/sendMessage';
    var response = req.post(url, JSON.stringify(mensaje));

    if (req.getStatus() != 200) {
        throw 'Error ' + req.getStatus() + ': ' + response;
    }

    return 'OK';
} catch (error) {
    throw 'Fallo en el script: ' + error;
}
```