---
title: Symboles ATL prédéfinis | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 965eb339295b86c223b5081dede8e33dd282b95d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386598"
---
# <a name="atl-predefined-symbols"></a>Symboles ATL prédéfinis

Ces symboles sont définis dans les fichiers d’en-tête ATL, mais ils prennent en charge les actions et fonctions d’application Windows standard. Ces symboles sont utilisés principalement avec les boîtes de dialogue. Lorsque vous travaillez avec les boîtes de dialogue et des contrôles dans le [éditeur de boîte de dialogue](../windows/dialog-editor.md), ces symboles s’affichent dans le **propriétés** fenêtre associée aux contrôles communs. Par exemple, si votre boîte de dialogue a un **Annuler** bouton, que la commande sera associée au symbole IDCANCEL dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

|||
|-|-|
|IDABORT|Contrôle : Bouton d’abandon de boîte de dialogue|
|IDC_STATIC|Contrôle : Contrôle statique|
|IDCANCEL|Contrôle : Bouton Annuler de boîte de dialogue|
|IDIGNORE|Contrôle : Bouton Ignorer de boîte de dialogue|
|IDNO|Contrôle : ne boîte de dialogue aucun bouton|
|IDOK|Contrôle : Bouton OK de boîte de dialogue|
|IDR_ACCELERATOR1|Ressource : Table d’accélérateurs|
|IDRETRY|Contrôle : Bouton de nouvelle tentative de boîte de dialogue|
|IDS_PROJNAME|Chaîne : Nom actuel de l’application|
|IDYES|Contrôle : Bouton de la boîte de dialogue Oui|

## <a name="requirements"></a>Configuration requise

ATL

## <a name="see-also"></a>Voir aussi

[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)<br/>
[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)