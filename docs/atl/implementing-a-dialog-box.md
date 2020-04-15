---
title: Mise en œuvre d’une boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 435926b0a0affde03580ceb2b479cb08a17d0454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319476"
---
# <a name="implementing-a-dialog-box"></a>Mise en œuvre d’une boîte de dialogue

Il y a deux façons d’ajouter une boîte de dialogue à votre projet ATL : utiliser le assistant de dialogue ATL ou l’ajouter manuellement.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Ajout d’une boîte de dialogue avec le assistant de dialogue ATL

Dans la [boîte de dialogue Add Class](../ide/add-class-dialog-box.md), sélectionnez l’objet ATL Dialog pour ajouter une boîte de dialogue à votre projet ATL. Remplissez le assistant de dialogue ATL le cas échéant et cliquez sur **Finition**. L’assistant ajoute une classe dérivée de [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) à votre projet. Ouvrez **la vue des ressources** à partir du menu **View,** localisez votre dialogue et cliquez deux fois pour l’ouvrir dans l’éditeur de ressources.

> [!NOTE]
> Si votre boîte de `CAxDialogImpl`dialogue est dérivée, elle peut héberger les commandes ActiveX et Windows. Si vous ne voulez pas les frais généraux de la prise en charge de contrôle ActiveX dans votre classe de boîte de dialogue, utilisez [CSimpleDialog](../atl/reference/csimpledialog-class.md) ou [CDialogImpl](../atl/reference/cdialogimpl-class.md) à la place.

Les gestionnaires de messages et d’événements peuvent être ajoutés à votre classe de dialogue à partir de Class View. Pour plus d’informations, voir [Ajouter un message ATL Handler](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Ajout d’une boîte de dialogue manuellement

La mise en œuvre d’une boîte de dialogue est similaire à la mise en œuvre d’une fenêtre. Vous dérivez une classe de [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md), ou [CSimpleDialog](../atl/reference/csimpledialog-class.md) et déclarez une [carte de message](../atl/message-maps-atl.md) pour gérer les messages. Toutefois, vous devez également spécifier un modèle de dialogue id de ressource dans votre classe dérivée. Votre classe doit avoir `IDD` un membre de données appelé pour détenir cette valeur.

> [!NOTE]
> Lorsque vous créez une boîte de dialogue à l’aide `IDD` de l’ASSISTANT de dialogue ATL, l’assistant ajoute automatiquement le membre comme un type **enum.**

`CDialogImpl`vous permet d’implémenter une boîte de dialogue modale ou sans mode qui héberge les commandes Windows. `CAxDialogImpl`vous permet d’implémenter une boîte de dialogue modale ou sans mode qui héberge à la fois les contrôles ActiveX et Windows.

Pour créer une boîte de dialogue modal, créez un exemple de votre `CDialogImpl`classe dérivée (ou `CAxDialogImpl`dérivée), puis appelez la méthode [DoModal.](../atl/reference/cdialogimpl-class.md#domodal) Pour fermer une boîte de dialogue modal, appelez la méthode [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) à partir d’un gestionnaire de message. Pour créer une boîte de dialogue sans mode, appelez la méthode [Créer](../atl/reference/cdialogimpl-class.md#create) au lieu de `DoModal`. Pour détruire une boîte de dialogue sans mode, appelez [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow).

Les événements de naufrage se font automatiquement dans [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Implémentez les gestionnaires de messages de la boîte `CWindowImpl`de dialogue comme vous le feriez pour les gestionnaires d’une classe dérivée. S’il y a une valeur de `LRESULT`retour spécifique au message, retournez-la comme un . Les `LRESULT` valeurs retournées sont cartographiées par ATL pour une bonne manipulation par le gestionnaire de dialogue Windows. Pour plus de détails, voir le code source pour [CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) in atlwin.h.

## <a name="example"></a>Exemple

La classe suivante met en œuvre une boîte de dialogue :

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Voir aussi

[classes de fenêtre](../atl/atl-window-classes.md)
