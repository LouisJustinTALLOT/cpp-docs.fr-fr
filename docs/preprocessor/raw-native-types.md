---
title: raw_native_types
ms.date: 11/04/2016
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: 32b77905ef7025334e5101e76864da9a15c50cf6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180477"
---
# <a name="rawnativetypes"></a>raw_native_types
**Spécifique à C++**

Désactive l'utilisation des classes de prise en charge COM dans les fonctions wrapper de haut niveau et force l'utilisation de types de données de bas niveau à la place.

## <a name="syntax"></a>Syntaxe

```
raw_native_types
```

## <a name="remarks"></a>Notes

Par défaut, les méthodes de gestion des erreurs de haut niveau utilisent les classes de prise en charge COM [_bstr_t](../cpp/bstr-t-class.md) et [_variant_t](../cpp/variant-t-class.md) à la place de la `BSTR` et `VARIANT` pointeurs d’interface COM bruts et les types de données. Ces classes encapsulent les détails de l'allocation et de la libération du stockage de mémoire pour ces types de données, et simplifient considérablement le casting de type et les opérations de conversion.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)