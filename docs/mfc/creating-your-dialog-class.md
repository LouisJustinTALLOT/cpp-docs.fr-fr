---
title: Création de votre classe de boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: 924cf2d79056d958aad775f92a6d0df2d45c8a70
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536577"
---
# <a name="creating-your-dialog-class"></a>Création de votre classe de boîte de dialogue

Pour chaque boîte de dialogue dans votre programme, créez une nouvelle classe de boîte de dialogue pour travailler avec la ressource de boîte de dialogue.

[Ajout d’une classe](../ide/adding-a-class-visual-cpp.md) explique comment créer une nouvelle classe de boîte de dialogue. Lorsque vous créez une classe de boîte de dialogue avec l’Assistant Ajouter une classe, il écrit les éléments suivants le. H et. Fichiers CPP que vous spécifiez :

Dans le. Fichier de H :

- Une déclaration de classe pour la classe de boîte de dialogue. La classe est dérivée de [CDialog](../mfc/reference/cdialog-class.md).

Dans le. Fichier CPP :

- Une table des messages pour la classe.

- Un constructeur standard pour la boîte de dialogue.

- Une substitution de la [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) fonction membre. Modifiez cette fonction. Il est utilisé pour les fonctionnalités d’échange et validation de données de boîte de dialogue, comme décrit ultérieurement dans [échange de données de boîtes de dialogue et la validation](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Voir aussi

[Création d’une classe de boîte de dialogue à l’aide des Assistants Code](../mfc/creating-a-dialog-class-with-code-wizards.md)<br/>
[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

