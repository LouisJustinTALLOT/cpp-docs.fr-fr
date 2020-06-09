---
title: Fonctions membres couramment substituées
ms.date: 09/06/2019
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: 7d4fc9005ff368ef6a83252e8cf0b2005ecf2cef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619665"
---
# <a name="commonly-overridden-member-functions"></a>Fonctions membres couramment substituées

Le tableau suivant répertorie les fonctions membres les plus probables à substituer dans votre `CDialog` classe dérivée de.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Fonctions membres couramment substituées de la classe CDialog

|Fonction membre|Message auquel il répond|Objectif du remplacement|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|Initialisez les contrôles de la boîte de dialogue.|
|`OnOK`|**BN_CLICKED** pour le bouton **IDOK**|Répondre quand l’utilisateur clique sur le bouton OK.|
|`OnCancel`|**BN_CLICKED** pour le bouton **IDCANCEL**|Répondre quand l’utilisateur clique sur le bouton Annuler.|

`OnInitDialog`, `OnOK` et `OnCancel` sont des fonctions virtuelles. Pour les remplacer, vous déclarez une fonction de substitution dans votre classe de boîte de dialogue dérivée à l’aide de l ['Assistant classe MFC](reference/mfc-class-wizard.md).

`OnInitDialog`est appelé juste avant que la boîte de dialogue ne s’affiche. Vous devez appeler le gestionnaire par défaut `OnInitDialog` à partir de votre remplacement, généralement en tant que première action dans le gestionnaire. Par défaut, `OnInitDialog` retourne la **valeur true** pour indiquer que le focus doit être défini sur le premier contrôle de la boîte de dialogue.

`OnOK`est généralement substitué pour les boîtes de dialogue non modales, mais pas pour les boîtes de dialogue modales. Si vous substituez ce gestionnaire pour une boîte de dialogue modale, appelez la version de la classe de base à partir de votre remplacement, pour vous assurer que `EndDialog` est appelé, ou appelez `EndDialog` -vous.

`OnCancel`est généralement substitué pour les boîtes de dialogue non modales.

Pour plus d’informations sur ces fonctions membres, consultez la classe [CDialog](reference/cdialog-class.md) dans la *référence MFC* et la discussion sur l' [utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](dialog-boxes.md)<br/>
[Fonctions membres couramment ajoutées](commonly-added-member-functions.md)
