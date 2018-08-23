---
title: ID de symbole prédéfinis | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, predefined IDs
- predefined symbol IDs
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee34744a110b31eba125e4b6cbef48207081f5d7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578638"
---
# <a name="predefined-symbol-ids"></a>ID de symbole prédéfinis

Quand vous commencez un nouveau projet, selon le type de projet, certains ID de symbole sont prédéfinis pour que vous puissiez les utiliser. Ces ID de symbole prennent en charge des bibliothèques et types de projet divers, par exemple MFC. Ils représentent les tâches usuelles généralement incluses dans une application, ou les actions des éléments matériels, par exemple une souris ou une imprimante.

Ces ID de symbole prennent de l'importance quand vous utilisez des ressources. Ils sont disponibles quand vous modifiez les tables d'accélérateurs. Certains d'entre eux sont déjà associés à des touches virtuelles. Ils sont également disponibles via le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez assigner des ID de symbole prédéfinis à de nouvelles ressources, ou leur assigner des touches d'accès rapide. La fonctionnalité associée à l'ID de symbole est automatiquement associée à la combinaison de touches concernée.

Ces bibliothèques comportent des symboles prédéfinis qui s'affichent dans le cadre du projet :

- [Symboles MFC prédéfinis](../windows/mfc-predefined-symbols.md)

- [Symboles ATL prédéfinis](../windows/atl-predefined-symbols.md)

- [Symboles Win32 prédéfinis](../windows/win32-predefined-symbols.md)

   > [!NOTE]
   > Les symboles prédéfinis sont toujours en lecture seule.

## <a name="requirements"></a>Configuration requise

Win32, MFC ou ATL

## <a name="see-also"></a>Voir aussi

[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)