---
title: Implémentation d’une boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 7866afd26c901181f2b4193a87daf5dca2b0c67f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226683"
---
# <a name="implementing-a-dialog-box"></a>Implémentation d’une boîte de dialogue

Il existe deux façons d’ajouter une boîte de dialogue à votre projet ATL : utilisez l’Assistant boîte de dialogue ATL ou ajoutez-le manuellement.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Ajout d’une boîte de dialogue à l’aide de l’Assistant boîte de dialogue ATL

Dans la [boîte de dialogue Ajouter une classe](../ide/add-class-dialog-box.md), sélectionnez l’objet de boîte de dialogue ATL pour ajouter une boîte de dialogue à votre projet ATL. Renseignez l’Assistant boîte de dialogue ATL de manière appropriée, puis cliquez sur **Terminer**. L’Assistant ajoute une classe dérivée de [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) à votre projet. Ouvrez **affichage des ressources** dans le menu **affichage** , localisez votre boîte de dialogue, puis double-cliquez dessus pour l’ouvrir dans l’éditeur de ressources.

> [!NOTE]
> Si votre boîte de dialogue est dérivée de `CAxDialogImpl` , elle peut héberger des contrôles ActiveX et Windows. Si vous ne souhaitez pas la surcharge liée à la prise en charge des contrôles ActiveX dans votre classe de boîte de dialogue, utilisez [CSimpleDialog](../atl/reference/csimpledialog-class.md) ou [CDialogImpl](../atl/reference/cdialogimpl-class.md) à la place.

Les gestionnaires de messages et d’événements peuvent être ajoutés à votre classe de boîte de dialogue à partir de Affichage de classes. Pour plus d’informations, consultez [Ajout d’un gestionnaire de messages ATL](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Ajout manuel d’une boîte de dialogue

L’implémentation d’une boîte de dialogue est semblable à l’implémentation d’une fenêtre. Vous dérivez une classe de [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md)ou [CSimpleDialog](../atl/reference/csimpledialog-class.md) et déclarez une [table des messages](../atl/message-maps-atl.md) pour gérer les messages. Toutefois, vous devez également spécifier un ID de ressource de modèle de boîte de dialogue dans votre classe dérivée. Votre classe doit avoir un membre de données appelé `IDD` pour contenir cette valeur.

> [!NOTE]
> Lorsque vous créez une boîte de dialogue à l’aide de l’Assistant boîte de dialogue ATL, l’Assistant ajoute automatiquement le `IDD` membre en tant que **`enum`** type.

`CDialogImpl`vous permet d’implémenter une boîte de dialogue modale ou non modale qui héberge des contrôles Windows. `CAxDialogImpl`vous permet d’implémenter une boîte de dialogue modale ou non modale qui héberge les contrôles ActiveX et Windows.

Pour créer une boîte de dialogue modale, créez une instance de votre `CDialogImpl` classe dérivée de (ou `CAxDialogImpl` dérivée de), puis appelez la méthode [DoModal](../atl/reference/cdialogimpl-class.md#domodal) . Pour fermer une boîte de dialogue modale, appelez la méthode [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) à partir d’un gestionnaire de messages. Pour créer une boîte de dialogue non modale, appelez la méthode [Create](../atl/reference/cdialogimpl-class.md#create) au lieu de `DoModal` . Pour détruire une boîte de dialogue non modale, appelez [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow).

Les événements de réception s’effectuent automatiquement dans [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Implémentez les gestionnaires de messages de la boîte de dialogue comme vous le feriez avec les gestionnaires d’une `CWindowImpl` classe dérivée de. S’il existe une valeur de retour spécifique au message, retournez-la en tant que `LRESULT` . Les valeurs retournées `LRESULT` sont mappées par ATL pour une gestion correcte par le gestionnaire de dialogue Windows. Pour plus d’informations, consultez le code source de [CDialogImplBaseT ::D ialogproc](../atl/reference/cdialogimpl-class.md#dialogproc) dans atlwin. h.

## <a name="example"></a>Exemple

La classe suivante implémente une boîte de dialogue :

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Voir aussi

[classes de fenêtre](../atl/atl-window-classes.md)
