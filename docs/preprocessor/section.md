---
title: section, pragma
ms.date: 08/29/2019
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: 47ae2ff2503317e937e2b3a497357afbd5522a64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216599"
---
# <a name="section-pragma"></a>section, pragma

Crée une section dans un fichier .obj.

## <a name="syntax"></a>Syntaxe

> **#pragma section (** "*section-Name*" [ **,** *attributes* ] **)**

## <a name="remarks"></a>Notes

Les termes « *segment* » et « *section»* ont la même signification dans cet article.

Une fois qu'une section est définie, elle reste valide pour le reste de la compilation. Toutefois, vous devez utiliser [_ _ declspec (Allocate)](../cpp/allocate.md)ou rien n’est placé dans la section.

*section-Name* est un paramètre obligatoire qui devient le nom de la section. Ce nom ne doit pas être en conflit avec les noms de section standard. Pour obtenir la liste des noms que vous ne devez pas utiliser lors de la création d’une section, consultez [/section](../build/reference/section-specify-section-attributes.md) .

*attributs* est un paramètre facultatif constitué d’un ou de plusieurs attributs séparés par des virgules à assigner à la section. Les *attributs* possibles sont les suivants:

|Attribut|Description|
|-|-|
|**read**|Permet les opérations de lecture sur les données.|
|**write**|Permet les opérations d'écriture sur les données.|
|**execute**|Permet d'exécuter le code.|
|**shared**|Partage la section entre tous les processus qui chargent l'image.|
|**nopage**|Marque la section comme non paginable. Utile pour les pilotes de périphériques Win32.|
|**nocache**|Marque la section comme ne pouvant pas être mise en cache. Utile pour les pilotes de périphériques Win32.|
|**discard**|Marque la section comme étant Ignorable. Utile pour les pilotes de périphériques Win32.|
|**remove**|Marque la section comme ne résidant pas dans la mémoire. Pour les pilotes de périphériques virtuels (V*x*D) uniquement.|

Si vous ne spécifiez aucun attribut, la section contient des attributs **en lecture et en** **écriture** .

## <a name="example"></a>Exemples

Dans cet exemple, le premier pragma de section identifie la section et ses attributs. L’entier `j` n’est pas placé `mysec` dans, car il n’a `__declspec(allocate)`pas été déclaré à l’aide de. Au lieu `j` de cela, passe dans la section des données. L'entier `i` n'est pas placé dans `mysec` en raison de son attribut de classe de stockage `__declspec(allocate)`.

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
