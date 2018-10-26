---
title: no_namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_namespace
dev_langs:
- C++
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e84cfad5a11c0d691c56e6e7ddcca17ea87e3f02
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082917"
---
# <a name="nonamespace"></a>no_namespace
**Spécifique à C++**

Indique que le nom de l'espace de noms n'est pas généré par le compilateur.

## <a name="syntax"></a>Syntaxe

```
no_namespace
```

## <a name="remarks"></a>Notes

Le contenu de la bibliothèque de types dans le fichier d'en-tête `#import` est normalement défini dans un espace de noms. Le nom de l’espace de noms est spécifié dans le `library` instruction du fichier IDL d’origine. Si le **no_namespace** attribut est spécifié, alors que cet espace de noms n’est pas généré par le compilateur.

Si vous souhaitez utiliser un nom d’espace de noms différent, puis utiliser le [rename_namespace](../preprocessor/rename-namespace.md) d’attribut à la place.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)