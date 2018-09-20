---
title: 'Comment : modifier la langue ou la Condition d’une ressource lors de la copie (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.changing
dev_langs:
- C++
helpviewer_keywords:
- Language property [C++]
ms.assetid: 8f622ab0-bac2-468f-ae70-78911afc4759
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6239acd275d94eb2a59fe59882095d5106d3fc1e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405734"
---
# <a name="how-to-change-the-language-or-condition-of-a-resource-while-copying-c"></a>Comment : modifier la langue ou la Condition d’une ressource lors de la copie (C++)

Durant la copie d'une ressource, vous pouvez changer sa propriété language ou sa propriété condition, ou les deux.

- La langue de la ressource identifie simplement la langue correspondant à la ressource. Ceci est utilisé par [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) pour aider à identifier la ressource pour laquelle vous avez besoin. (Toutefois, les ressources peuvent présenter des différences spécifiques à chaque langue et qui ne sont pas liées à du texte, par exemple, des accélérateurs qui fonctionnent seulement sur un clavier japonais, ou une image bitmap appropriée uniquement pour les builds localisées en chinois, etc.)

- La condition d'une ressource est un symbole défini qui identifie une condition dans laquelle cette copie particulière de la ressource doit être utilisée.

La langue et la condition d'une ressource sont affichées entre parenthèses après le nom de la ressource dans la fenêtre Espace de travail. Dans cet exemple, la ressource nommée IDD_AboutBox utilise le finnois comme langue, et sa condition est XX33.

```cpp
IDD_AboutBox (Finnish - XX33)  
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Pour copier une ressource existante et modifier sa langue ou sa condition

1. Dans le fichier .rc ou dans le [affichage des ressources](../windows/resource-view-window.md) fenêtre, avec le bouton droit de la ressource que vous souhaitez copier.

2. Choisissez **insérer une copie** dans le menu contextuel.

3. Dans le **insérer une copie de ressources** boîte de dialogue :

   - Pour le **langage** zone de liste, sélectionnez la langue.

   - Dans le **Condition** , tapez la condition.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Guide pratique pour copier des ressources](../windows/how-to-copy-resources.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)