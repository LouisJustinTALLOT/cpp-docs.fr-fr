---
title: Implémentation d’une boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b656af864f8a0dd7c5a69866976b4c1e624b87b9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764291"
---
# <a name="implementing-a-dialog-box"></a>Implémentation d’une boîte de dialogue

Il existe deux façons d’ajouter une boîte de dialogue à votre projet ATL : utiliser l’Assistant dialogue ATL ou ajouter manuellement.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Ajout d’une boîte de dialogue avec l’Assistant dialogue ATL

Dans le [boîte de dialogue Ajouter une classe](../ide/add-class-dialog-box.md), sélectionnez l’objet de la boîte de dialogue ATL pour ajouter une boîte de dialogue à votre projet ATL. Complétez l’Assistant dialogue ATL comme il convient et cliquez sur **Terminer**. L’Assistant ajoute une classe dérivée de [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) à votre projet. Ouvrez l’affichage des ressources à partir de la **vue** menu, recherchez votre boîte de dialogue et double-cliquez dessus pour l’ouvrir dans l’éditeur de ressources.

> [!NOTE]
>  Si votre boîte de dialogue est dérivée de `CAxDialogImpl`, il peut héberger les deux ActiveX et contrôles Windows. Si vous ne souhaitez pas la surcharge liée à la prise en charge du contrôle ActiveX dans votre classe de boîte de dialogue, utilisez [CSimpleDialog](../atl/reference/csimpledialog-class.md) ou [CDialogImpl](../atl/reference/cdialogimpl-class.md) à la place.

Message et gestionnaires d’événements peuvent être ajoutés à votre classe de boîte de dialogue à partir de l’affichage de classes. Pour plus d’informations, consultez [Ajout d’un gestionnaire de messages ATL](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Ajout manuel d’une boîte de dialogue

Implémentation d’une boîte de dialogue est similaire à l’implémentation d’une fenêtre. Vous dérivez une classe à partir de le [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md), ou [CSimpleDialog](../atl/reference/csimpledialog-class.md) et déclarer un [table des messages](../atl/message-maps-atl.md) à traiter les messages. Toutefois, vous devez également spécifier un ID de ressource de modèle de boîte de dialogue dans votre classe dérivée. Votre classe doit avoir un membre de données appelé `IDD` doit contenir cette valeur.

> [!NOTE]
>  Lorsque vous créez une boîte de dialogue à l’aide de l’Assistant dialogue ATL, l’Assistant ajoute automatiquement le `IDD` membre comme un **enum** type.

`CDialogImpl` vous permet d’implémenter une modale ou une boîte de dialogue non modale qui héberge des contrôles de Windows. `CAxDialogImpl` vous permet d’implémenter une modale ou une boîte de dialogue non modale qui héberge des contrôles ActiveX et Windows.

Pour créer une boîte de dialogue modale, créez une instance de votre `CDialogImpl`-dérivées (ou `CAxDialogImpl`-dérivées) classe, puis appelez le [DoModal](../atl/reference/cdialogimpl-class.md#domodal) (méthode). Pour fermer la boîte de dialogue modale, appelez le [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) méthode à partir d’un gestionnaire de messages. Pour créer une boîte de dialogue non modale, appelez le [créer](../atl/reference/cdialogimpl-class.md#create) méthode au lieu de `DoModal`. Pour détruire une boîte de dialogue non modale, appelez [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow).

Réception d’événements est effectuée automatiquement dans [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Implémenter des gestionnaires de messages de la boîte de dialogue comme vous le feriez pour les gestionnaires dans un `CWindowImpl`-classe dérivée. S’il existe une valeur de retour spécifiques au message, retourner comme un `LRESULT`. Retourné `LRESULT` les valeurs sont mappées par ATL pour gérer correctement par le Gestionnaire de boîte de dialogue Windows. Pour plus d’informations, consultez le code source pour [CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) dans atlwin.h.

## <a name="example"></a>Exemple

La classe suivante implémente une boîte de dialogue :

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Voir aussi

[Classes de fenêtre](../atl/atl-window-classes.md)

