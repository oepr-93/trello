[![Build Status](https://travis-ci.org/norberteder/trello.svg?branch=master)](https://travis-ci.org/norberteder/trello)

# Trello

## Objetivos del proyecto:
    - Explorar proyectos que no son de tu autoría.
    - Explorar un API Rest de un servicio como trello.
    - Usar Postman para probar un api rest.
    - Cómo funciona el api rest de trello.
    
## Desarrollo del proyecto

Crea un nuevo proyecto de js.
Agregar la siguiente dependencia:

> npm install dotenv --save

Crea un archivo `.env` agregando el API KEY y TOKEN de trello:

`.env`
```javascript
KEY="TrelloKeyHere"
TOKEN="Trellotokenhere"
```

El archivo `.gitignore` debe incluir el archivo `.env` ya que la información sensible no debe versionarse.

Realizar un fork al proyecto [](https://github.com/norberteder/trello)

Agregar la dependencia de Trello: `npm install trello --save`.

Agregar el código en app.js:

`app.js`
```javascript
require('dotenv').config()

if(!process.env.TOKEN && !process.env.KEY){
  throw new Error('No hay configuración con Api Key y con Token')
}

let Trello = require("trello");
let trello = new Trello(process.env.KEY, process.env.TOKEN);

let cardTitle = `Card Nueva ${new Date()}`

trello.addCard(cardTitle, "LaunchX Card Description", "6264e42be72d295e64f5c083",
	function (error, trelloCard) {
		if (error) {
			console.log('Could not add card:', error);
		}
		else {
			console.log('Added card:', trelloCard);
		}
	});
```
Revisar lo siguiente:
- Qué dependencias estan usando.
- Cuál es el archivo principal
- Están usando Common JS o ESM
- Qué framework de pruebas estás usando
- Cómo están diseñadas las pruebas
- Revisa los commits del repo 

Este repsositorio permite lanzar requests a trello con un script de manera local. 

## De acuerdo a la documentación, las funciones disponibles son:

### Add

* addAttachmentToCard 
* addBoard 
* addCard 
* addCardWithExtraParams 
* addChecklistToCard 
* addCommentToCard 
* addCustomField
* addDueDateToCard 
* addExistingChecklistToCard 
* addItemToChecklist 
* addLabelOnBoard 
* addLabelToCard 
* addListToBoard 
* addMemberToBoard 
* addMemberToCard 
* addOptionToCustomField
* addStickerToCard 
* addWebhook 
* copyBoard
* setCustomFieldOnCard

### Delete

* deleteCard 
* deleteLabel 
* deleteLabelFromCard 
* delMemberFromCard
* deleteWebhook 

### Get

* getActionsOnBoard
* getBoardMembers 
* getBoards 
* getCard 
* getCardsForList 
* getCardsOnBoard 
* getCardsOnBoardWithExtraParams 
* getCardsOnList 
* getCardsOnListWithExtraParams
* getCardStickers
* getChecklistsOnCard 
* getCustomFieldsOnBoard 
* getLabelsForBoard 
* getListsOnBoard 
* getListsOnBoardByFilter 
* getMember 
* getMemberCards 
* getOrgBoards 
* getOrgMembers 

### Update

* renameList 
* updateBoardPref 
* updateCard 
* updateCardDescription 
* updateCardList 
* updateCardName 
* updateCardPos
* updateChecklist 
* updateLabel 
* updateLabelColor 
* updateLabelName 

Everything that is not available as a function can be requested by calling `makeRequest`.
