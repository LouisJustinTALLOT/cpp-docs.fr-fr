---
title: alloc_text | Microsoft Docs
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
ms.openlocfilehash: c90545bb2806b97ccdd47ae90f8ab41bf1b3422c
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42545753"
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

Le **alloc_text** pragma ne gère pas les fonctions membres C++ ni les fonctions surchargées. Il n’est applicable uniquement aux fonctions déclarées avec liaison C : autrement dit, les fonctions déclarées avec le **extern « C »** spécification de liaison. Si vous tentez d'utiliser ce pragma sur une fonction avec une liaison C++, une erreur de compilateur est générée.  
  
Depuis la fonction en utilisant adressage `__based` n’est pas compatible, en spécifiant les emplacements de section nécessite l’utilisation de la **alloc_text** pragma. Le nom spécifié par *textsection* doit être placée entre guillemets doubles.  
  
Le **alloc_text** pragma doit figurer après les déclarations d’une des fonctions spécifiées et avant les définitions de ces fonctions.  
  
Les fonctions référencées dans un **alloc_text** pragma doit être défini dans le même module que le pragma. Si ce n'est pas le cas et qu'une fonction non définie est compilée ultérieurement dans une section de texte différente, l'erreur peut être interceptée ou non. En règle générale, le programme fonctionnera correctement, mais la fonction ne sera pas allouée dans les sections prévues.  
  
Autres limitations sur **alloc_text** sont les suivantes :  
  
- Il ne peut pas être utilisé au sein d'une fonction.  
  
- Il doit être utilisé après que la fonction a été déclarée, mais avant que la fonction soit définie.  
  
## <a name="see-also"></a>Voir aussi 

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)