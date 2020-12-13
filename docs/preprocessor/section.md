---
description: 'En savoir plus sur : pragma de section'
title: section, pragma
ms.date: 08/29/2019
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: f4a719c60fd5bdf4f8e8841aab88f82c30b92a95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342281"
---
# <a name="section-pragma"></a>section, pragma

Crée une section dans un fichier .obj.

## <a name="syntax"></a>Syntaxe

> **#pragma section (** "*section-Name*" [ **,** *attributes* ] **)**

## <a name="remarks"></a>Notes

Les termes « *segment* » et « *section »* ont la même signification dans cet article.

Une fois qu'une section est définie, elle reste valide pour le reste de la compilation. Toutefois, vous devez utiliser [__declspec (Allocate)](../cpp/allocate.md)ou rien n’est placé dans la section.

*section-Name* est un paramètre obligatoire qui devient le nom de la section. Ce nom ne doit pas être en conflit avec les noms de section standard. Pour obtenir la liste des noms que vous ne devez pas utiliser lors de la création d’une section, consultez [/section](../build/reference/section-specify-section-attributes.md) .

*attributs* est un paramètre facultatif constitué d’un ou de plusieurs attributs séparés par des virgules à assigner à la section. Les *attributs* possibles sont les suivants :

|Attribut|Description|
|-|-|
|**en lecture**|Permet les opérations de lecture sur les données.|
|**Ecrire**|Permet les opérations d'écriture sur les données.|
|**execute**|Permet d'exécuter le code.|
|**partagé**|Partage la section entre tous les processus qui chargent l'image.|
|**nopage**|Marque la section comme non paginable. Utile pour les pilotes de périphériques Win32.|
|**NoCache**|Marque la section comme ne pouvant pas être mise en cache. Utile pour les pilotes de périphériques Win32.|
|**refuser**|Marque la section comme étant Ignorable. Utile pour les pilotes de périphériques Win32.|
|**remove**|Marque la section comme ne résidant pas dans la mémoire. Pour les pilotes de périphériques virtuels (V *x* D) uniquement.|

Si vous ne spécifiez aucun attribut, la section contient des attributs **en lecture et en** **écriture** .

## <a name="example"></a>Exemple

Dans cet exemple, le premier pragma de section identifie la section et ses attributs. L’entier `j` n’est pas placé dans `mysec` , car il n’a pas été déclaré à l’aide de `__declspec(allocate)` . Au lieu de cela, `j` passe dans la section des données. L'entier `i` n'est pas placé dans `mysec` en raison de son attribut de classe de stockage `__declspec(allocate)`.

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
