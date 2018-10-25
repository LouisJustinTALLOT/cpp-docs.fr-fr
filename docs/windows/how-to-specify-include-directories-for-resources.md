---
title: 'Comment : spécifier répertoires Include pour les ressources (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
ms.assetid: d6a7c0f6-4810-4bb0-b4b7-7d2476a20ca2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: be030539a7b2d0585ea895f1428de822d3300d53
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052965"
---
# <a name="how-to-specify-include-directories-for-resources-c"></a>Comment : spécifier répertoires Include pour les ressources (C++)

### <a name="to-specify-include-directories-for-a-specific-rc-file"></a>Pour spécifier les répertoires Include d'un fichier .rc spécifique

1. Cliquez sur le fichier .rc dans l’Explorateur de solutions et sélectionnez **propriétés** dans le menu contextuel.

2. Dans le **Pages de propriétés** boîte de dialogue, cliquez sur le **ressources** nœud dans le volet gauche, puis spécifiez les répertoires dans include supplémentaires le **autres répertoires include** propriété.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le Guide du développeur .NET Framework.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Include des ressources, boîte de dialogue](../windows/resource-includes-dialog-box.md)<br/>
[TN035 : utilisation de plusieurs fichiers de ressources et fichiers d’en-tête avec Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)<br/>
[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)