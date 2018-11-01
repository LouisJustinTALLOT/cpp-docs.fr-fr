---
title: "Comment : ajouter des contrôles de ruban et des gestionnaires d'événements"
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: 7f5b85fad181dba147c2135784d237bccdceb422
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637994"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Comment : ajouter des contrôles de ruban et des gestionnaires d'événements

Contrôles de ruban sont des éléments, tels que des boutons et des zones de liste déroulante, que vous ajoutez aux panneaux. Les panneaux sont des zones de la barre du ruban qui affichent un groupe de contrôles connexes.

Dans cette rubrique, vous ouvrez le Concepteur de ruban, ajouter un bouton et ensuite lier un événement qui affiche « Hello World ».

### <a name="to-open-the-ribbon-designer"></a>Pour ouvrir le Concepteur de ruban

1. Dans Visual Studio, sur le **vue** menu, cliquez sur **affichage des ressources**.

1. Dans **affichage des ressources**, double-cliquez sur la ressource de ruban pour l’afficher sur l’aire de conception.

### <a name="to-add-a-button-and-an-event-handler"></a>Pour ajouter un bouton et un gestionnaire d’événements

1. À partir de la **barre d’outils**, cliquez sur **bouton** et faites-la glisser sur un panneau dans l’aire de conception.

1. Cliquez avec le bouton droit, puis cliquez sur **ajouter un gestionnaire d’événements**.

1. Dans le **Assistant Gestionnaire d’événements**, confirmez les paramètres par défaut et cliquez sur **ajouter et modifier des**. Pour plus d’informations, consultez [Assistant Gestionnaire d’événements](../ide/event-handler-wizard.md).

1. Dans l’éditeur de code, ajoutez le code suivant dans la fonction de gestionnaire :

```
    MessageBox((LPCTSTR)L"Hello World");

```

## <a name="see-also"></a>Voir aussi

[Exemple RibbonGadgets : Application de Gadgets de ruban](../visual-cpp-samples.md)<br/>
[Concepteur de ruban (MFC)](../mfc/ribbon-designer-mfc.md)

