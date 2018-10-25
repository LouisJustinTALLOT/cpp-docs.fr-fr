---
title: raw_interfaces_only | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 789c9179b2ba48f5c3796f709931728bc756aaaa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075032"
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**Spécifique à C++**

Supprime la génération de fonctions de wrapper de la gestion des erreurs et [propriété](../cpp/property-cpp.md) déclarations qui utilisent ces fonctions wrapper.

## <a name="syntax"></a>Syntaxe

```
raw_interfaces_only
```

## <a name="remarks"></a>Notes

Le **raw_interfaces_only** attribut provoque également le préfixe par défaut utilisé pour nommer les fonctions non-propriété à supprimer. Normalement, le préfixe est **raw_**. Si cet attribut est spécifié, les noms de fonctions proviennent directement de la bibliothèque de types.

Cet attribut vous permet d'exposer uniquement le contenu de bas niveau de la bibliothèque de types.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)