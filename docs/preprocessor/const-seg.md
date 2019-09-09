---
title: const_seg, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
ms.openlocfilehash: 845583889eb922ba97d145eefe6bca280a83817b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220433"
---
# <a name="const_seg-pragma"></a>const_seg, pragma

Spécifie la section (segment) où les variables [const](../cpp/const-cpp.md) sont stockées dans le fichier objet (. obj).

## <a name="syntax"></a>Syntaxe

> **#pragma const_seg (** ["*section-Name*" [ **,** "*section-Class*"]] **)** \
> **#pragma const_seg (** { **Push** | **pop** } [ **,** *identificateur* ] [ **,** "*section-Name*" [ **,** "*section-Class*"]] **)**

### <a name="parameters"></a>Paramètres

**souleve**\
Facultatif Place un enregistrement sur la pile interne du compilateur. Un **Push** peut avoir un *identificateur* et un *nom de section*.

**roulant**\
Facultatif Supprime un enregistrement du haut de la pile interne du compilateur. Une **liste déroulante** peut avoir un *identificateur* et un *nom de section*. Vous pouvez dépiler plusieurs enregistrements à l’aide d’une seule commande **pop** en utilisant l' *identificateur*. La *section-Name* devient le nom de la section Const active après le pop.

*identificateur*\
Facultatif En cas d’utilisation avec **Push**, assigne un nom à l’enregistrement sur la pile interne du compilateur. Lorsqu’elle est utilisée avec **pop**, la directive dépile les enregistrements de la pile interne jusqu’à ce que l' *identificateur* soit supprimé. Si l' *identificateur* est introuvable sur la pile interne, rien n’est dépilé.

«*section-Name*» \
Facultatif Nom d’une section. Lorsqu’elle est utilisée avec **pop**, la pile est dépilée et la *section-Name* devient le nom de la section Const active.

«*section-Class*» \
Facultatif Ignoré, mais inclus pour la compatibilité avec les versions C++ de Microsoft antérieures à la version 2,0.

## <a name="remarks"></a>Notes

Une *section* dans un fichier objet est un bloc de données nommé qui est chargé en mémoire en tant qu’unité. Une *section const* est une section qui contient des données constantes. Dans cet article, les termes *segment* et *section* ont la même signification.

La directive pragma **const_seg** indique au compilateur de placer tous les éléments de données constantes à partir de l’unité de traduction dans une section const nommée *section-Name*. La section par défaut du fichier objet pour les variables **const** est `.rdata`. Certaines variables **const** , telles que les scalaires, sont automatiquement incorporées dans le flux de code. Le code inline n’apparaît pas `.rdata`dans. Une directive pragma **const_seg** sans paramètre *section-Name* réinitialise le nom de la section pour les éléments de données **const** suivants `.rdata`sur.

Si vous définissez un objet qui nécessite une initialisation dynamique dans un `const_seg`, le résultat est un comportement indéfini.

Pour obtenir la liste des noms qui ne doivent pas être utilisés pour créer une section, consultez [/section](../build/reference/section-specify-section-attributes.md).

Vous pouvez également spécifier des sections pour les données initialisées ([data_seg](../preprocessor/data-seg.md)), les données non initialisées ([bss_seg](../preprocessor/bss-seg.md)) et les fonctions ([code_seg](../preprocessor/code-seg.md)).

Vous pouvez utiliser [DUMPBIN. EXE](../build/reference/dumpbin-command-line.md) pour afficher les fichiers objets. Les versions de DUMPBIN pour chaque architecture cible prise en charge sont incluses dans Visual Studio.

## <a name="example"></a>Exemple

```cpp
// pragma_directive_const_seg.cpp
// compile with: /EHsc
#include <iostream>

const int i = 7;               // inlined, not stored in .rdata
const char sz1[]= "test1";     // stored in .rdata

#pragma const_seg(".my_data1")
const char sz2[]= "test2";     // stored in .my_data1

#pragma const_seg(push, stack1, ".my_data2")
const char sz3[]= "test3";     // stored in .my_data2

#pragma const_seg(pop, stack1) // pop stack1 from stack
const char sz4[]= "test4";     // stored in .my_data1

int main() {
    using namespace std;
   // const data must be referenced to be put in .obj
   cout << sz1 << endl;
   cout << sz2 << endl;
   cout << sz3 << endl;
   cout << sz4 << endl;
}
```

```Output
test1
test2
test3
test4
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
