---
title: section
ms.date: 11/04/2016
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: cd8eee564fa17b21d5421a3471fd676af921f444
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462138"
---
# <a name="section"></a>section

Crée une section dans un fichier .obj.

## <a name="syntax"></a>Syntaxe

```
#pragma section( "section-name" [, attributes] )
```

## <a name="remarks"></a>Notes

La signification des termes du contrat *segment* et *section* sont interchangeables dans cette rubrique.

Une fois qu'une section est définie, elle reste valide pour le reste de la compilation. Toutefois, vous devez utiliser [__declspec (Allocate)](../cpp/allocate.md) ou rien ne sera placé dans la section.

*nom de la section* est un paramètre obligatoire qui sera le nom de la section. Ce nom ne doit pas être en conflit avec les noms de section standard. Consultez [/SECTION](../build/reference/section-specify-section-attributes.md) pour obtenir la liste des noms que vous ne devez pas utiliser lors de la création d’une section.

*attributs* est un paramètre optionnel consistant en un ou plusieurs attributs séparés par des virgules que vous souhaitez affecter à la section. Possible *attributs* sont :

|Attribut|Description|
|-|-|
|**read**|Permet les opérations de lecture sur les données.|
|**write**|Permet les opérations d'écriture sur les données.|
|**execute**|Permet d'exécuter le code.|
|**Partagé**|Partage la section entre tous les processus qui chargent l'image.|
|**nopage**|Marque la section comme non paginable ; utile pour les pilotes de périphériques Win32.|
|**nocache**|Marque la section comme ne pouvant pas être mise en cache ; utile pour les pilotes de périphériques Win32.|
|**Ignorer**|Marque la section comme ne pouvant pas être supprimée ; utile pour les pilotes de périphériques Win32.|
|**remove**|Marque la section comme non résidante en ; pilotes de périphériques virtuels (V*x*D) uniquement.|

Si vous ne spécifiez aucun attribut, la section aura des attributs en lecture et en écriture.

## <a name="example"></a>Exemple

Dans l'exemple suivant, la première instruction identifie la section et ses attributs. L'entier `j` n'est pas placé dans `mysec` car il n'a pas été déclaré avec `__declspec(allocate)` ; `j` est placé dans la section de données. L'entier `i` n'est pas placé dans `mysec` en raison de son attribut de classe de stockage `__declspec(allocate)`.

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)