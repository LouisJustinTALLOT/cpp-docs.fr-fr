---
title: Symboles Win32 prédéfinis | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols [C++], Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 18edb56c03541f61607817d14fdbadb067a3630d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422777"
---
# <a name="win32-predefined-symbols"></a>Symboles Win32 prédéfinis

Ces symboles sont définis dans les fichiers d’en-tête Win32 et ils prennent en charge les actions et fonctions d’application Windows standard. Ces symboles sont principalement utilisés avec les éléments d’interface utilisateur courants. Lorsque vous travaillez avec des contrôles dans les éditeurs de ressources, ces symboles s’affichent dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) associées aux contrôles courants. Par exemple, si votre barre d’outils doit afficher l’icône d’application, l’icône sera associée au symbole IDI_SMALL dans le **fenêtre des propriétés**.

|||
|-|-|
|IDABORT|Contrôle : Bouton d’abandon de boîte de dialogue|
|IDC_STATIC|Contrôle : Texte statique dans une boîte de dialogue|
|IDCANCEL|Contrôle : Bouton Annuler de boîte de dialogue|
|IDD_ABOUTBOX|Boîte de dialogue : Produit à propos de la boîte de dialogue|
|IDI_PROJECTNAME|Icône : Icône du projet actuel|
|IDI_SMALL|Icône : Petite icône de projet actuel|
|IDIGNORE|Contrôle : Utilisé avec le bouton Ignorer dans les boîtes de dialogue|
|IDM_ABOUT|Élément de menu : Utilisé avec aide... Sur...|
|IDM_EXIT|Élément de menu : Utilisé avec fichier... Sortie...|
|IDNO|Contrôle : ne boîte de dialogue aucun bouton|
|IDOK|Contrôle : Bouton OK de boîte de dialogue|
|IDRETRY|Contrôle : Bouton de nouvelle tentative de boîte de dialogue|
|IDS_APP_TITLE|Chaîne : Nom actuel de l’application|
|IDYES|Contrôle : Bouton de la boîte de dialogue Oui|

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)<br/>
[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)