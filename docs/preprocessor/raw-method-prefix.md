---
title: raw_method_prefix
ms.date: 08/29/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: b1bc536507716e5c117718ec825bf7fe76c84b61
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216144"
---
# <a name="raw_method_prefix"></a>raw_method_prefix

**C++Plus**

Spécifie un préfixe différent pour éviter les collisions de noms.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **raw_method_prefix (** «*préfixe*» **)**

### <a name="parameters"></a>Paramètres

*Céder*\
Le préfixe à utiliser.

## <a name="remarks"></a>Notes

Les propriétés et les méthodes de bas niveau sont exposées par les fonctions membres nommées à l’aide d’un préfixe par défaut **raw_** , afin d’éviter les conflits de noms avec les fonctions membres de gestion des erreurs de haut niveau.

> [!NOTE]
> Les effets de l’attribut **raw_method_prefix** sont inchangés par la présence de l’attribut [raw_interfaces_only](raw-interfaces-only.md) . Le **raw_method_prefix** a toujours la priorité `raw_interfaces_only` sur la spécification d’un préfixe. Si les deux attributs sont utilisés dans la `#import` même instruction, le préfixe spécifié par l’attribut **raw_method_prefix** est utilisé.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
