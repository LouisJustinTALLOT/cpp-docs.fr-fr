---
title: Définition de la largeur d’une barre de défilement horizontale | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 51dad141-aa0b-46a3-a82c-46b80d603d94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74e9e24fdd3b46a8abe021b6c0ea3bbc2f860a2c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438871"
---
# <a name="setting-the-width-of-a-horizontal-scroll-bar"></a>Définition de la largeur d'une barre de défilement horizontale

Lorsque vous ajoutez une zone de liste avec une barre de défilement horizontale à une boîte de dialogue à l’aide des classes MFC, la barre de défilement s’affiche pas automatiquement dans votre application.

### <a name="to-make-the-scroll-bar-appear"></a>Pour afficher la barre de défilement

1. Définissez une largeur maximale pour l’élément le plus large en appelant [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) dans votre code.

   Sans cette valeur est définie, la barre de défilement pas apparaîtra, même lorsque les éléments dans la zone de liste sont plus larges que la zone.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

MFC

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)