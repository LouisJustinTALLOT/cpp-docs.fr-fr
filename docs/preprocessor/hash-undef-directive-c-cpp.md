---
title: '#undef, Directive (C/C++) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#undef'
dev_langs:
- C++
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16b8c937ad62ddc6738c626543dab2d4e5453bc5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839778"
---
# <a name="undef-directive-cc"></a>#undef, directive (C/C++)
Supprime (élimine) un nom créé précédemment avec `#define`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#undef   
identifier  
  
```  
  
## <a name="remarks"></a>Notes  
 Le `#undef` directive supprime la définition actuelle de *identificateur*. Par conséquent, les occurrences suivantes de *identificateur* sont ignorés par le préprocesseur. Pour supprimer une définition de macro à l’aide de `#undef`, attribuez uniquement la macro *identificateur* ; ne donnent pas une liste de paramètres.  
  
 Vous pouvez également appliquer la directive `#undef` à un identificateur qui n'a aucune définition précédente. Cela garantit que l'identificateur n'est pas défini. Le remplacement de macro n'est pas effectué dans des instructions `#undef`.  
  
 La directive `#undef` est généralement combinée avec une directive `#define` pour créer une zone dans un programme source dans lequel un identificateur a une signification spéciale. Par exemple, une fonction spécifique du programme source peut utiliser des constantes manifestes pour définir les valeurs spécifiques à l'environnement qui n'affectent pas le reste du programme. La directive `#undef` fonctionne également avec la directive `#if` pour contrôler la compilation conditionnelle du programme source. Consultez [le #if, #elif, #else et #endif Directives](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) pour plus d’informations.  
  
 Dans l'exemple suivant, la directive `#undef` supprime des définitions d'une constante symbolique et d'une macro. Notez que seul l'identificateur de la macro est donné.  
  
```  
#define WIDTH 80  
#define ADD( X, Y ) ((X) + (Y))  
.  
.  
.  
#undef WIDTH  
#undef ADD  
```  
  
 **Section spécifique à Microsoft**  
  
 Les macros peuvent être supprimées de la ligne de commande avec l'option /U, suivie des noms de macros à supprimer. L’effet de cette commande est équivalente à une séquence de `#undef` *-nom de la macro* instructions au début du fichier.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Directives de préprocesseur](../preprocessor/preprocessor-directives.md)