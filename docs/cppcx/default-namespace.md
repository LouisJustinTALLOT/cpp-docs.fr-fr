---
description: 'En savoir plus sur : espace de noms par défaut'
title: espace de noms par défaut
ms.date: 12/30/2016
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
ms.openlocfilehash: 46fa1e6162d0d9ffe25a47bfec88d8461f366828
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273317"
---
# <a name="default-namespace"></a>espace de noms par défaut

L' `default` espace de noms portée les types intégrés qui sont pris en charge par C++/CX.

## <a name="syntax"></a>Syntaxe

```
namespace default;
```

### <a name="members"></a>Membres

Tous les types intégrés héritent des membres suivants.

| Nom | Description |
|--|--|
| [default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md) | Détermine si l'objet spécifié est égal à l'objet actuel. |
| [default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md) | Retourne le code de hachage de cette instance. |
| [default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md) | Retourne une chaîne qui représente le type actuel. |
| [default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md) | Retourne une chaîne qui représente le type actuel. |

### <a name="built-in-types"></a>Types intégrés

|Nom|Description|
|----------|-----------------|
|`char16`|Valeur non numérique 16 bits qui représente un point de code Unicode (UTF-16).|
|`float32`|Nombre à virgule flottante IEEE 754 32 bits.|
|`float64`|Nombre à virgule flottante IEEE 754 64 bits.|
|`int16`|Entier signé 16 bits.|
|`int32`|Entier signé 32 bits.|
|`int64`|Entier signé 64 bits.|
|`int8`|Valeur numérique signée 8 bits.|
|`uint16`|Entier non signé 16 bits.|
|`uint32`|Entier non signé 32 bits.|
|`uint64`|Entier 64 bits non signé.|
|`uint8`|Valeur numérique non signée 8 bits.|

### <a name="requirements"></a>Spécifications

**En-tête** : vccorlib.h

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
