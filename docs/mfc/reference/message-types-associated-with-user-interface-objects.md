---
description: 'En savoir plus sur : types de messages associés à des objets User-Interface'
title: Types de messages associés aux objets interface utilisateur
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.uiobject.msgs
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
ms.openlocfilehash: 78ddb9e5290d17f92714d6b50a57ac097bbf104c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219276"
---
# <a name="message-types-associated-with-user-interface-objects"></a>Types de messages associés aux objets interface utilisateur

Le tableau suivant indique les types d’objets avec lesquels vous travaillez, ainsi que les types de messages qui leur sont associés.

### <a name="user-interface-objects-and-associated-messages"></a>Objets de l’interface utilisateur et messages associés

|ID de l'objet|Messages|
|---------------|--------------|
|Nom de la classe, représentant la fenêtre conteneur|Messages Windows appropriés à une classe dérivée de [CWnd](../../mfc/reference/cwnd-class.md): une boîte de dialogue, une fenêtre, une fenêtre enfant, une fenêtre enfant MDI ou une fenêtre frame de premier plan.|
|Identificateur de menu ou d’accélérateur|-Message de commande (exécute la fonction de programme).<br />-UPDATE_COMMAND_UI message (met à jour dynamiquement l’élément de menu).|
|Identificateur de contrôle|Contrôle les messages de notification pour le type de contrôle sélectionné.|

## <a name="see-also"></a>Voir aussi

[Mappage de messages à des fonctions](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigate-code-cpp.md)
