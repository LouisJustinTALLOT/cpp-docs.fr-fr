---
title: Ajout de contrôles à une boîte de dialogue entraîne la boîte de dialogue ne fonctionne plus après | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], troubleshooting
- common controls, troubleshooting
- troubleshooting controls
- dialog boxes, troubleshooting
- dialog box controls, troubleshooting
- InitCommonControls
ms.assetid: b2dd4574-ea59-4343-8d65-b387cead5da6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b10c24955e74d08ab570b5b694628f42bb394268
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858992"
---
# <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>La boîte de dialogue ne fonctionne plus après l'ajout de contrôles
Après avoir ajouté un contrôle commun ou un contrôle d’édition enrichi pour une boîte de dialogue, il n’apparaît pas lorsque vous testez la boîte de dialogue ou la boîte de dialogue n’apparaît pas.  
  
 **Exemple de ce problème**  
  
1.  Créez un projet Win32, en modifiant les paramètres d’application afin de créer une application Windows (pas une application console).  
  
2.  Dans [affichage des ressources](../windows/resource-view-window.md), double-cliquez sur le fichier .rc.  
  
3.  Sous l’option de la boîte de dialogue, double-cliquez sur le **sur** boîte.  
  
4.  Ajouter un **contrôle de l’adresse IP** à la boîte de dialogue.  
  
5.  Enregistrer et **tout reconstruire**.  
  
6.  Exécutez le programme.  
  
7.  Dans la boîte de dialogue **aide** menu, cliquez sur le **sur** commande ; aucune boîte de dialogue zone s’affiche.  
  
 **La cause**  
  
 Actuellement, l’éditeur de ne pas ajoute automatiquement le code à votre projet lorsque vous faites glisser et déposez les contrôles communs ou RichEdit dans une boîte de dialogue. Ni Visual Studio fournit une erreur ou un avertissement lorsque ce problème se produit. Vous devez ajouter le code pour le contrôle manuellement.  
  
||||  
|-|-|-|  
|Contrôle Slider|Contrôle d’arborescence|Date Time Picker|  
|Contrôle toupie|Contrôle onglet|Calendrier mensuel|  
|Contrôle de progression|Contrôle Animation|Contrôle de l’adresse IP|  
|Touche d’accès rapide|Contrôle RichEdit|Zone de liste déroulante étendue|  
|Contrôle de liste|Contrôle Rich Edit 2.0|Contrôle personnalisé|  
  
## <a name="the-fix-for-common-controls"></a>Le correctif pour les contrôles communs  
 Pour pouvoir utiliser les contrôles communs dans une boîte de dialogue, vous devez appeler [InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697) ou **AFXInitCommonControls** avant de créer la boîte de dialogue.  
  
## <a name="the-fix-for-richedit-controls"></a>Le correctif pour les contrôles RichEdit  
 Vous devez appeler **LoadLibrary** des contrôles RichEdit. Pour plus d’informations, consultez [à l’aide du contrôle RichEdit 1.0 avec MFC](../windows/using-the-richedit-1-0-control-with-mfc.md), [sur les contrôles RichEdit](http://msdn.microsoft.com/library/windows/desktop/bb787873) dans les [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)], et [vue d’ensemble du contrôle RichEdit](../mfc/overview-of-the-rich-edit-control.md).  
  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage de l’éditeur de boîte de dialogue](../windows/troubleshooting-the-dialog-editor.md)   
 [Éditeur de boîtes de dialogue](../windows/dialog-editor.md)

