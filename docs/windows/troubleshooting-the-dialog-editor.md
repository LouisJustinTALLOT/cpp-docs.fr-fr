---
title: Résolution des problèmes de l’éditeur de boîtes de dialogue (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 21882868-5ac4-4a41-a4a6-eaaa059402ea
ms.openlocfilehash: fe0fe704b5c17d0db4e3419f29d21f0e60bc4211
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484953"
---
# <a name="troubleshooting-the-dialog-editor-c"></a>Résolution des problèmes de l’éditeur de boîtes de dialogue (C++)

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

Voici quelques problèmes dont vous devez connaître lorsque vous travaillez dans le C++ **boîte de dialogue** éditeur :

## <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>Ajout de contrôles à une boîte de dialogue, la boîte de dialogue ne fonctionne plus

Après avoir ajouté un contrôle commun ou un contrôle RichEdit une boîte de dialogue, elle ne s’affiche lorsque vous testez la boîte de dialogue ou de la boîte de dialogue ne s’affiche.

### <a name="example-of-the-problem"></a>Exemple de ce problème

1. Créez un projet Win32, en modifiant les paramètres d’application pour créer une application Windows (pas une application console).

1. Dans [affichage des ressources](../windows/resource-view-window.md), double-cliquez sur le fichier .rc.

1. Sous l’option de la boîte de dialogue, double-cliquez sur le **sur** boîte.

1. Ajouter un **contrôle d’adresse IP** à la boîte de dialogue.

1. Enregistrer et **régénérer tout**.

1. Exécutez le programme.

1. Dans la boîte de dialogue **aide** menu, cliquez sur le **sur** commande ; aucune boîte de dialogue zone s’affiche.

### <a name="the-cause"></a>La cause

Actuellement, le **boîte de dialogue** éditeur n’ajoute pas automatiquement code à votre projet lorsque vous faites glisser et déposez les contrôles communs ou RichEdit dans une boîte de dialogue. Ni Visual Studio fournit-il une erreur ou un avertissement lorsque ce problème se produit. Pour résoudre le problème, ajoutez manuellement le code pour le contrôle.

||||
|-|-|-|
|Contrôle Slider|Contrôle d’arborescence|Date Time Picker|
|Contrôle Spin|Contrôle onglet|Calendrier mensuel|
|Contrôle de progression|Contrôle Animation|Contrôle d’adresse IP|
|Touche d’accès rapide|Contrôle RichEdit|Zone de liste déroulante étendue|
|Contrôle de liste|Contrôle Rich Edit 2.0|Contrôle personnalisé|

### <a name="fix-for-common-controls"></a>Correctif pour les contrôles communs

Pour utiliser les contrôles communs dans une boîte de dialogue, vous devez appeler [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) ou `AFXInitCommonControls` avant de créer la boîte de dialogue.

### <a name="fix-for-richedit-controls"></a>Correctif pour les contrôles RichEdit

Vous devez appeler `LoadLibrary` des contrôles RichEdit. Pour plus d’informations, consultez [sur les contrôles RichEdit](/windows/desktop/Controls/about-rich-edit-controls) dans le SDK Windows et [vue d’ensemble du contrôle RichEdit](../mfc/overview-of-the-rich-edit-control.md).

### <a name="requirements"></a>Spécifications

Win32

## <a name="using-the-richedit-10-control-with-mfc"></a>Utilisation du contrôle RichEdit 1.0 avec MFC

Pour utiliser un contrôle RichEdit, vous devez d’abord appeler [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) pour charger le contrôle RichEdit 2.0 (RICHED20. DLL), ou appelez [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) pour charger l’ancien contrôle RichEdit 1.0 (Riched32). (DLL).

Vous pouvez utiliser actuel [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) classe avec l’ancien contrôle RichEdit 1.0, mais `CRichEditCtrl` est conçu uniquement pour prendre en charge le contrôle RichEdit 2.0. RichEdit 1.0 et RichEdit 2.0 étant similaires, la plupart des méthodes fonctionnera. Notez, toutefois, il existe des différences entre les contrôles 1.0 et 2.0, et certaines méthodes peuvent fonctionner de manière incorrecte ou ne fonctionne pas du tout.

### <a name="requirements"></a>Spécifications

MFC

## <a name="see-also"></a>Voir aussi

[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)