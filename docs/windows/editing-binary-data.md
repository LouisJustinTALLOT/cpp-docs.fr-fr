---
title: Modification des données binaires | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- binary data
ms.assetid: 0fd429de-baf1-4871-b5e4-42bf868a3261
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96a4370d56e2f5d9758e97010965668bd08306c3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593003"
---
# <a name="editing-binary-data"></a>Édition de données binaires

### <a name="to-edit-a-resource-in-the-binary-editor"></a>Pour modifier une ressource dans l’éditeur binaire

1. Sélectionnez l’octet que vous souhaitez modifier.

   Le **onglet** touche déplace le focus entre les sections hexadécimale et ASCII de la **binaire** éditeur. Vous pouvez utiliser la **PG.préc** et **PG.suiv** clés pour vous déplacer dans l’écran d’une ressource à la fois.

2. Tapez la nouvelle valeur.

   La valeur change immédiatement dans à la fois les sections hexadécimale et ASCII et le focus passe à la valeur suivante dans la ligne.

   > [!NOTE]
   > Le **binaire** éditeur accepte les modifications automatiquement lorsque vous fermez l’éditeur.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Binary Editor](binary-editor.md)