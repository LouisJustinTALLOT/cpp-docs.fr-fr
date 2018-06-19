---
title: alloc_text | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
dev_langs:
- C++
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1e07b630254d7691321443a74973e06ed50ae2d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912769"
---
# <a name="alloctext"></a>alloc_text
Nomme la section de code où les définitions de fonctions spécifiées doivent résider. Le pragma doit intervenir entre un déclarateur de fonction et la définition de fonction pour les fonctions nommées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma alloc_text( "  
textsection  
", function1, ... )  
```  
  
## <a name="remarks"></a>Notes  
 Le **alloc_text** pragma ne gère pas les fonctions membres C++ ni les fonctions surchargées. Il s’applique uniquement aux fonctions déclarées avec liaison C : autrement dit, les fonctions déclarées avec le **extern « C »** spécification de liaison. Si vous tentez d'utiliser ce pragma sur une fonction avec une liaison C++, une erreur de compilateur est générée.  
  
 Depuis la fonction adressage avec `__based` n’est pas compatible, en spécifiant les emplacements de section nécessite l’utilisation de la **alloc_text** pragma. Le nom spécifié par *textsection* doit être placée entre guillemets doubles.  
  
 Le **alloc_text** pragma doit figurer après les déclarations d’une des fonctions spécifiées et avant les définitions de ces fonctions.  
  
 Les fonctions référencées dans un **alloc_text** pragma doit être défini dans le même module que le pragma. Si ce n'est pas le cas et qu'une fonction non définie est compilée ultérieurement dans une section de texte différente, l'erreur peut être interceptée ou non. En règle générale, le programme fonctionnera correctement, mais la fonction ne sera pas allouée dans les sections prévues.  
  
 Autres limitations sur **alloc_text** sont les suivantes :  
  
-   Il ne peut pas être utilisé au sein d'une fonction.  
  
-   Il doit être utilisé après que la fonction a été déclarée, mais avant que la fonction soit définie.  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)