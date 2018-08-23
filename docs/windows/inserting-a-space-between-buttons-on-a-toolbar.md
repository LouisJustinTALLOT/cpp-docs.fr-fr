---
title: Insertion d’un espace entre les boutons sur une barre d’outils | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Toolbar editor, spacing toolbar buttons
- toolbar buttons (in Toolbar editor), space between buttons
ms.assetid: 4925ea6b-5d3a-4949-a920-bf371a37e529
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d45fb3c7d0d61e1895ff03fff64ab75c828eda0e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599664"
---
# <a name="inserting-a-space-between-buttons-on-a-toolbar"></a>Insertion d'un espace entre des boutons sur une barre d'outils

En règle générale, pour insérer un espace entre les boutons, faites simplement glisser les autres dans la barre d’outils. Pour supprimer l’espace, faites-les glisser vers l’autre.

### <a name="to-insert-a-space-before-a-button-that-is-not-followed-by-a-space"></a>Pour insérer un espace avant un bouton qui n’est pas suivi d’un espace

1. Faites glisser le bouton à droite ou vers le bas jusqu'à ce qu’il chevauche le bouton suivant sur à mi-chemin.

### <a name="to-insert-a-space-before-a-button-which-is-followed-by-a-space-and-to-retain-that-trailing-space"></a>Insérer un espace avant un bouton qui est suivi par un espace et de conserver l’espace à droite

1. Faites glisser le bouton jusqu'à ce que le bord droit ou inférieur touche simplement le bouton suivant ou superpose à ce dernier.

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-close-up-that-following-space"></a>Pour insérer un espace avant un bouton qui est suivi par un espace et fermer espace suivant

1. Faites glisser le bouton à droite ou vers le bas jusqu'à ce qu’il chevauche le bouton suivant sur à mi-chemin.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[Création, déplacement et modification de boutons de barre d’outils](../windows/creating-moving-and-editing-toolbar-buttons.md)  
[Éditeur de barres d’outils](../windows/toolbar-editor.md)