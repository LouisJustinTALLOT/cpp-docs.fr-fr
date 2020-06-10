---
title: "Comment : ajouter des contrôles de ruban et des gestionnaires d'événements"
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: 560524c36dbf57faec3b4b6372cade047f9fe7de
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618484"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Comment : ajouter des contrôles de ruban et des gestionnaires d'événements

Les contrôles de ruban sont des éléments, tels que des boutons et des zones de liste modifiable, que vous ajoutez aux panneaux. Les panneaux sont des zones de la barre du ruban qui affichent un groupe de contrôles connexes.

Dans cette rubrique, vous allez ouvrir le concepteur de ruban, ajouter un bouton, puis lier un événement qui affiche « Hello World ».

### <a name="to-open-the-ribbon-designer"></a>Pour ouvrir le concepteur de ruban

1. Dans Visual Studio, dans le menu **affichage** , cliquez sur **affichage des ressources**.

1. Dans **affichage des ressources**, double-cliquez sur la ressource du ruban pour l’afficher sur l’aire de conception.

### <a name="to-add-a-button-and-an-event-handler"></a>Pour ajouter un bouton et un gestionnaire d’événements

1. À partir de la **barre d’outils**, cliquez sur **bouton** et faites-le glisser sur un panneau de l’aire de conception.

1. Cliquez avec le bouton droit sur le bouton, puis cliquez sur **Ajouter un gestionnaire d’événements**.

1. Dans l' **Assistant gestionnaire d’événements**, confirmez les paramètres par défaut et cliquez sur **Ajouter et modifier**. Pour plus d’informations, consultez [Assistant gestionnaire d’événements](../ide/event-handler-wizard.md).

1. Dans l’éditeur de code, ajoutez le code suivant à la fonction du gestionnaire :

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>Voir aussi

[Exemple RibbonGadgets : application gadgets de ruban](../overview/visual-cpp-samples.md)<br/>
[Concepteur de ruban (MFC)](ribbon-designer-mfc.md)
