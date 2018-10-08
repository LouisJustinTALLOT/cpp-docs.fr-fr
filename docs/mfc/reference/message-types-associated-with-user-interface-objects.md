---
title: Les Types associés aux objets d’Interface utilisateur de messages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.uiobject.msgs
dev_langs:
- C++
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd89f19547eef8ade9d23a6176ea74cb49586857
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860288"
---
# <a name="message-types-associated-with-user-interface-objects"></a>Types de messages associés aux objets interface utilisateur

Le tableau suivant présente les types d’objets avec lesquelles vous travaillez et les types de messages qui s’y rapportent.

### <a name="user-interface-objects-and-associated-messages"></a>Objets d’Interface utilisateur et les Messages associés

|ID d’objet|Messages|
|---------------|--------------|
|Nom de la classe, qui représente la fenêtre conteneur|Les messages Windows appropriés pour une [CWnd](../../mfc/reference/cwnd-class.md)-classe dérivée : une boîte de dialogue, la fenêtre, la fenêtre enfant, la fenêtre enfant MDI ou fenêtre frame au premier plan.|
|Identificateur de menu ou d’accélérateur|-Message de commande (exécute la fonction de programme).<br />-Message UPDATE_COMMAND_UI (met dynamiquement à jour l’élément de menu).|
|Identificateur de contrôle|Messages de notification de contrôle pour le type de contrôle sélectionné.|

## <a name="see-also"></a>Voir aussi

[Mappage des messages à des fonctions](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Une fonction virtuelle de substitution](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigating-the-class-structure-visual-cpp.md)
