---
title: const_seg | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 984dc392b6ffa51d662d3ab56b1c0dc0dbc92233
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839153"
---
# <a name="constseg"></a>const_seg
Spécifie le segment où [const](../cpp/const-cpp.md) variables sont stockées dans le fichier .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Notes  
 La signification des termes du contrat *segment* et *section* sont interchangeables dans cette rubrique.  
  
 Fichiers OBJ peuvent être affichés avec le [dumpbin](../build/reference/dumpbin-command-line.md) application. Dans le fichier .obj, le segment par défaut pour les variables `const` est .rdata. Certaines variables `const`, telles que les scalaires, sont automatiquement incluses en ligne dans le flux de code. Le code inline n'apparaîtra pas dans .rdata.  
  
 La définition d'un objet qui requiert une initialisation dynamique dans un `const_seg` entraîne un comportement non défini.  
  
 `#pragma const_seg` sans paramètre réinitialise le segment sur .rdata.  
  
 `push`(facultatif)  
 Place un enregistrement sur la pile interne du compilateur. Un `push` peut avoir un `identifier` et un `segment-name`.  
  
 `pop`(facultatif)  
 Supprime un enregistrement du haut de la pile interne du compilateur.  
  
 `identifier`(facultatif)  
 En cas d'utilisation avec `push`, assigne un nom à l'enregistrement sur la pile interne du compilateur. En cas d'utilisation avec `pop`, dépile les enregistrements de la pile interne jusqu'à ce que `identifier` soit supprimé ; si `identifier` est introuvable sur la pile interne, rien n'est dépilé.  
  
 Utiliser `identifier` permet à plusieurs enregistrements d'être dépilés à l'aide d'une seule commande `pop`.  
  
 "`segment-name`" (facultatif)  
 Nom d'un segment. Lorsqu'il est utilisé avec `pop`, la pile est dépilée et `segment-name` devient le nom du segment actif.  
  
 "`segment-class`" (facultatif)  
 Incluse pour la compatibilité avec les versions de C++ antérieures à la version 2.0. Elle est ignorée.  
  
## <a name="example"></a>Exemple  
  
```  
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
 Consultez [/SECTION](../build/reference/section-specify-section-attributes.md) pour une liste de noms, vous ne devez pas utiliser lors de la création d’une section.  
  
 Vous pouvez également spécifier des sections pour les données initialisées ([data_seg](../preprocessor/data-seg.md)), données non initialisées ([bss_seg](../preprocessor/bss-seg.md)) et les fonctions ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)