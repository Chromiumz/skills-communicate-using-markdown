# Index

![Image of My Avatar](https://avatars.githubusercontent.com/u/32971814?v=4&size=64)

``` javascript
var clientTracker = {
    getKnowledgeMultiplier : function() {
        game.highestKnowledge.div(3).pow(0.7).add(1)
    },
    getTier : function() {
        return document.getElementById("knowledgeLevelInput").value;
    },
    currentTier : Number(document.getElementById("knowledgeLevelInput").value),
    currentMultiplier : game.highestKnowledge.div(3).pow(0.7).add(1),
}

var autoknowledge = setInterval(function() {
    if(game.knowledge.mul(0.2).gte(game.knowledgeUpgradeCosts[0])) {
        buyKnowledgeUpgrade(1);
    }

    if(game.knowledge.mul(0.001).gte(game.knowledgeUpgradeCosts[1])) {
        buyKnowledgeUpgrade(2);
    }

    if(game.knowledge.mul(0.001).gte(game.tomeCost)) {
        buyTome();
    }
    
    if(clientTracker.currentMultiplier.mul(1.55).lte(game.highestKnowledge.div(3).pow(0.7).add(1))) {
        clientTracker.currentTier++;
        document.getElementById("knowledgeLevelInput").value = clientTracker.currentTier;
        clientTracker.currentMultiplier = game.highestKnowledge.div(3).pow(0.7).add(1);
        updateKnowledgeTradeLevel(2);
    } else {
        purchaseKnowledgeTrade(2);
    }
},50);
```
