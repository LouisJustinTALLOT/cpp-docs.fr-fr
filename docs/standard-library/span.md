---
title: '&lt;répartis&gt;'
ms.date: 05/28/2020
f1_keywords:
- <span>
helpviewer_keywords:
- span header
ms.openlocfilehash: 27f27acfa84a3ccc42586593747e4657146cbe39
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813533"
---
# <a name="ltspangt"></a>&lt;répartis&gt;

Un `span` est une vue sur une séquence contiguë d’objets. Il fournit un accès rapide et sécurisé aux limites. Contrairement `vector` `array` à ou, il n’est pas « propriétaire » des éléments auxquels il fournit l’accès.

Pour plus d’informations, consultez [classe span](span-class.md) . Voici un exemple de la façon dont une étendue peut être utilisée :

```cpp
#include <span>
#include <iostream>

void Show(std::span<int> someValues)
{
    // show values in reverse
    for (auto rIt = someValues.rbegin(); rIt != someValues.rend(); ++rIt)
    {
        std::cout << *rIt;
    }

    // show a subspan
    for (auto& i : someValues.subspan(1, 2))
    {
        std::cout << i;
    }
}

int main()
{
    int numbers[]{ 0,1,2,3,4 };
    Show(numbers); // note conversion from array to span
}
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<span>

**Espace de noms :** std

**Option du compilateur :** /std : c + + latest

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|||
|-|:-|
|[répartis](span-class.md)| Fournit une vue sur une séquence contiguë d’objets. |

### <a name="operators"></a>Opérateurs

|||
|-|:-|
|[opérateur =](span-class.md#op_eq)| Affectation d’étendue |
|[and\[\]](span-class.md#op_at)| Accès aux éléments |

### <a name="functions"></a>Fonctions

|||
|-|:-|
| [as_bytes](span-functions.md#as_bytes)| Obtient les octets en lecture seule sous-jacents de l’étendue. |
| [as_writable_bytes](span-functions.md#as_writable_bytes) | Obtient les octets sous-jacents de l’étendue. |

### <a name="constants"></a>Constantes

|||
|-|:-|
| **dynamic_extent** | Indique que la taille de l’étendue est déterminée au moment de l’exécution plutôt qu’au moment de la compilation. Lorsque le nombre d’éléments dans l’étendue est connu au moment de la compilation, il est spécifié en tant que `Extent` paramètre de modèle. Si le nombre n’est pas connu jusqu’à l’exécution, spécifiez à la `dynamic_extent` place. |

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
