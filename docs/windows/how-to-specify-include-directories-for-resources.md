---
title: 'Comment : spécifier répertoires Include pour les ressources | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directories [C++], specifying include paths for resources
- include files, specifying for resources
- resources [Visual Studio], including in projects
ms.assetid: d6a7c0f6-4810-4bb0-b4b7-7d2476a20ca2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e0b655713a378c859bb017f661022f86aa687ab6
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676430"
---
# <a name="how-to-specify-include-directories-for-resources"></a>Comment : spécifier des répertoires Include pour les ressources

### <a name="to-specify-include-directories-for-a-specific-rc-file"></a>Pour spécifier les répertoires Include d'un fichier .rc spécifique

1. Cliquez sur le fichier .rc dans l’Explorateur de solutions et sélectionnez **propriétés** dans le menu contextuel.

2. Dans le **Pages de propriétés** boîte de dialogue, cliquez sur le **ressources** nœud dans le volet gauche, puis spécifiez les répertoires dans include supplémentaires le **autres répertoires include** propriété.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le Guide du développeur .NET Framework. 

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Include des ressources, boîte de dialogue](../windows/resource-includes-dialog-box.md)  
[TN035 : utilisation de plusieurs fichiers de ressources et fichiers d’en-tête avec Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)  
[Fichiers de ressources](../windows/resource-files-visual-studio.md)  
[Éditeurs de ressources](../windows/resource-editors.md)