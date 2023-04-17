# Avoid colab from disconnecting

The google colab runtime would disconnect if the notebook remains inactive. 
Google Colab notebooks have an idle timeout of 90 minutes and absolute timeout of 12 hours. This means, if user does not interact with his Google Colab notebook for more than 90 minutes, its instance is automatically terminated. Also, maximum lifetime of a Colab instance is 12 hours.

GOTO Inspect element console and type in the following code:

```
function ClickConnect(){
console.log("Working"); 
document.querySelector("colab-toolbar-button").click() 
}setInterval(ClickConnect,60000)
```

Source: https://medium.com/@shivamrawat_756/how-to-prevent-google-colab-from-disconnecting-717b88a128c0

For some other solutions, ref: https://stackoverflow.com/questions/57113226/how-can-i-prevent-google-colab-from-disconnecting
