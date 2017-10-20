#Kongreso en Twitter
Quieres descargar el feed completo de tus Kongresistas favoritos, acá te dejo la formula.

Anda al perfil de twitter de tu Kongresista. Presiona *Crtl (Cmd) + Shift + C*, aparecera la herramienta de inspección de elementos. Anda a la pestaña *Console* e inserta el siguiente código.

setInterval(function(){ scrollTo(0, document.body.scrollHeight) }, 2500)

Lo que hará sera recorrer hasta el final del perfil de tu Kongresista, puede tomar un rato dependiendo de la cantidad de tweets que le ha ocurrido enviar. Una vez que llegué al final, inserta el siguiente código para copiar todo el feed. 

var allTweets = []; var tweetElements = document.querySelectorAll('li.stream-item'); for (var i = 0; i < tweetElements.length; i++) { var el = tweetElements[i]; var text = el.querySelector('.tweet-text').textContent; allTweets.push({ id: el.getAttribute('data-item-id'), timestamp: el.querySelector('a.tweet-timestamp').getAttribute('data-original-title') || el.querySelector('a.tweet-timestamp').getAttribute('title'), text: text, link: 'https://twitter.com' + el.querySelector('div.tweet').getAttribute('data-permalink-path'), is_retweet: el.querySelector('.js-retweet-text') ? true : false, retweets: el.querySelector('.js-actionRetweet .ProfileTweet-actionCountForPresentation').textContent, favorites: el.querySelector('.js-actionFavorite .ProfileTweet-actionCountForPresentation').textContent, replies: el.querySelector('.js-actionReply .ProfileTweet-actionCountForPresentation').textContent, }); } copy(allTweets);

Una vez ejecutado, anda a un archivo de texto y pégalo (Crtl + V). Guardalo con el nombre que quieras y con la extensión .json y listo.