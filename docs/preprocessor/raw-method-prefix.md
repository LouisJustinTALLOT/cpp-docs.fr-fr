---
description: 'En savoir plus sur : raw_method_prefix'
title: raw_method_prefix
ms.date: 08/29/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: 9e05f70814e48a4460287e96905b543f7d76dde6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201987"
---
# <a name="raw_method_prefix"></a>raw_method_prefix

**Section spécifique à C++**

Spécifie un préfixe différent pour éviter les collisions de noms.

## <a name="syntax"></a>Syntaxe

> raw_method_prefix de la *bibliothèque de types* **#import** **(** «*préfixe*» **)**

### <a name="parameters"></a>Paramètres

*Céder*\
Le préfixe à utiliser.

## <a name="remarks"></a>Notes

Les propriétés et les méthodes de bas niveau sont exposées par les fonctions membres nommées à l’aide d’un préfixe par défaut de **raw_**, afin d’éviter les conflits de noms avec les fonctions membres de gestion des erreurs de haut niveau.

> [!NOTE]
> Les effets de l’attribut **raw_method_prefix** sont inchangés par la présence de l’attribut [raw_interfaces_only](raw-interfaces-only.md) . La **raw_method_prefix** est toujours prioritaire sur la `raw_interfaces_only` spécification d’un préfixe. Si les deux attributs sont utilisés dans la même `#import` instruction, le préfixe spécifié par l’attribut **raw_method_prefix** est utilisé.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
