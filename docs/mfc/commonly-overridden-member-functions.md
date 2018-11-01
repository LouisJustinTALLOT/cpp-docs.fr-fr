---
title: Fonctions membres couramment substituées
ms.date: 11/04/2016
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: 163da1ee6e98e974af0fd1a6b27e1b2df85e9ce0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439578"
---
# <a name="commonly-overridden-member-functions"></a>Fonctions membres couramment substituées

Le tableau suivant répertorie la plus vraisemblable de fonctions membres à remplacer dans votre `CDialog`-classe dérivée.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Les fonctions membres de la classe CDialog couramment substituées

|Fonction membre|Il répond à des messages|Objet du remplacement|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|Initialiser les contrôles de la boîte de dialogue.|
|`OnOK`|**BN_CLICKED** bouton **IDOK**|Répondre quand l’utilisateur clique sur le bouton OK.|
|`OnCancel`|**BN_CLICKED** bouton **IDCANCEL**|Répondre quand l’utilisateur clique sur le bouton Annuler.|

`OnInitDialog`, `OnOK`, et `OnCancel` sont des fonctions virtuelles. Pour les remplacer, vous déclarez une fonction de substitution dans votre classe de boîte de dialogue dérivée à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

`OnInitDialog` est appelé juste avant que la boîte de dialogue s’affiche. Vous devez appeler la valeur par défaut `OnInitDialog` gestionnaire à partir de votre remplacement, généralement en tant que la première action dans le gestionnaire. Par défaut, `OnInitDialog` retourne **TRUE** pour indiquer que le focus doit être défini pour le premier contrôle dans la boîte de dialogue.

`OnOK` est généralement substituée pour les boîtes de dialogue non modale, mais non modale. Si vous remplacez ce gestionnaire pour une boîte de dialogue modale, appelez la version de la classe de base à partir de votre remplacement, pour vous assurer que `EndDialog` est appelée, ou appeler `EndDialog` vous-même.

`OnCancel` est généralement substituée pour les boîtes de dialogue non modale.

Pour plus d’informations sur ces fonctions membres, consultez la classe [CDialog](../mfc/reference/cdialog-class.md) dans le *référence MFC* et la discussion sur [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Fonctions membres couramment ajoutées](../mfc/commonly-added-member-functions.md)
