---
title: no_auto_exclude | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_auto_exclude
dev_langs:
- C++
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0673a7216bc00fb13cb0c99e0f9b74accabe33b0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074964"
---
# <a name="noautoexclude"></a>no_auto_exclude
**Spécifique à C++**

Désactive l'exclusion automatique.

## <a name="syntax"></a>Syntaxe

```
no_auto_exclude
```

## <a name="remarks"></a>Notes

Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. `#import` tente d'éviter les erreurs de définitions multiples en excluant automatiquement ces éléments. Dans ce cas, [Avertissement du compilateur (niveau 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) sera émis pour chaque élément à exclure. Vous pouvez désactiver cette exclusion automatique à l'aide de cet attribut.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)