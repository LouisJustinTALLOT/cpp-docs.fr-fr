---
title: const_seg
ms.date: 09/17/2018
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
ms.openlocfilehash: c58f154f5e1ab6906b45d59f454a7dc2b5c0bfbe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366587"
---
# <a name="constseg"></a>const_seg
Spécifie le segment où [const](../cpp/const-cpp.md) variables sont stockées dans le fichier .obj.

## <a name="syntax"></a>Syntaxe

```
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>Paramètres

**push**<br/>
(Facultatif) Place un enregistrement sur la pile interne du compilateur. Un **push** peut avoir un *identificateur* et *segment-name*.

**pop**<br/>
(Facultatif) Supprime un enregistrement à partir du haut de la pile interne du compilateur.

*identifier*<br/>
(Facultatif) Lorsqu’il est utilisé avec **push**, assigne un nom à l’enregistrement sur la pile interne du compilateur. Lorsqu’il est utilisé avec **pop**, dépile les enregistrements de la pile interne jusqu'à ce que *identificateur* est supprimé ; si *identificateur* est introuvable sur la pile interne, rien n’est dépilé.

À l’aide de *identificateur* permet à plusieurs enregistrements à dépiler avec une seule **pop** commande.

"*segment-name*"<br/>
(Facultatif) Le nom d’un segment. Lorsqu’il est utilisé avec **pop**, la pile est dépilée et *segment-name* devient le nom de segment actif.

"*segment-class*"<br/>
(Facultatif) Inclus pour la compatibilité avec C++ antérieures à la version 2.0. Elle est ignorée.

## <a name="remarks"></a>Notes

La signification des termes du contrat *segment* et *section* sont interchangeables dans cette rubrique.

Les fichiers OBJ peuvent être affichés avec le [dumpbin](../build/reference/dumpbin-command-line.md) application. Dans le fichier .obj, le segment par défaut pour les variables `const` est .rdata. Certaines variables `const`, telles que les scalaires, sont automatiquement incluses en ligne dans le flux de code. Le code inline n'apparaîtra pas dans .rdata.

La définition d'un objet qui requiert une initialisation dynamique dans un `const_seg` entraîne un comportement non défini.

`#pragma const_seg` sans paramètre réinitialise le segment sur .rdata.

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

## <a name="comments"></a>Commentaires

Consultez [/SECTION](../build/reference/section-specify-section-attributes.md) pour obtenir la liste des noms que vous ne devez pas utiliser lors de la création d’une section.

Vous pouvez également spécifier des sections pour les données initialisées ([data_seg](../preprocessor/data-seg.md)), données non initialisées ([bss_seg](../preprocessor/bss-seg.md)) et les fonctions ([code_seg](../preprocessor/code-seg.md)).

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)