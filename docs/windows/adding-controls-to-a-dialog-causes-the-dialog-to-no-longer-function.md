---
title: Ajout de contrôles à une boîte de dialogue entraîne la boîte de dialogue ne fonctionne plus (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
ms.assetid: b2dd4574-ea59-4343-8d65-b387cead5da6
ms.openlocfilehash: d95c89c0a07e02ab0934a54ca1fe067961348766
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648290"
---
# <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function-c"></a>Ajout de contrôles à une boîte de dialogue entraîne la boîte de dialogue ne fonctionne plus (C++)

Après avoir ajouté un contrôle commun ou un contrôle RichEdit une boîte de dialogue, elle n’apparaît pas lorsque vous testez la boîte de dialogue ou de la boîte de dialogue n’apparaîtra pas.

### <a name="example-of-the-problem"></a>Exemple de ce problème

1. Créez un projet Win32, en modifiant les paramètres d’application pour créer une application Windows (pas une application console).

2. Dans [affichage des ressources](../windows/resource-view-window.md), double-cliquez sur le fichier .rc.

3. Sous l’option de la boîte de dialogue, double-cliquez sur le **sur** boîte.

4. Ajouter un **contrôle d’adresse IP** à la boîte de dialogue.

5. Enregistrer et **régénérer tout**.

6. Exécutez le programme.

7. Dans la boîte de dialogue **aide** menu, cliquez sur le **sur** commande ; aucune boîte de dialogue zone s’affiche.

### <a name="the-cause"></a>La cause

Actuellement, l’éditeur de boîtes de dialogue n’ajoute pas automatiquement code à votre projet lorsque vous faites glisser et déposez les contrôles communs ou RichEdit dans une boîte de dialogue. Ni Visual Studio fournit-il une erreur ou un avertissement lorsque ce problème se produit. Vous devez ajouter le code pour le contrôle manuellement.

||||
|-|-|-|
|Contrôle Slider|Contrôle d’arborescence|Date Time Picker|
|Contrôle Spin|Contrôle onglet|Calendrier mensuel|
|Contrôle de progression|Contrôle Animation|Contrôle d’adresse IP|
|Touche d’accès rapide|Contrôle RichEdit|Zone de liste déroulante étendue|
|Contrôle de liste|Contrôle Rich Edit 2.0|Contrôle personnalisé|

## <a name="the-fix-for-common-controls"></a>Le correctif pour les contrôles communs

Pour pouvoir utiliser les contrôles communs dans une boîte de dialogue, vous devez appeler [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) ou `AFXInitCommonControls` avant de créer la boîte de dialogue.

## <a name="the-fix-for-richedit-controls"></a>Le correctif pour les contrôles RichEdit

Vous devez appeler `LoadLibrary` des contrôles RichEdit. Pour plus d’informations, consultez [à l’aide du contrôle RichEdit 1.0 avec MFC](../windows/using-the-richedit-1-0-control-with-mfc.md), [sur les contrôles RichEdit](/windows/desktop/Controls/about-rich-edit-controls) dans le SDK Windows, et [vue d’ensemble du contrôle RichEdit](../mfc/overview-of-the-rich-edit-control.md).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Dépannage de l’Éditeur de boîtes de dialogue](../windows/troubleshooting-the-dialog-editor.md)<br/>
[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)