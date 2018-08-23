---
title: Modificateurs spécifiques Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 08/16/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3dfc57e1d6af11628b37823f2452ee2b65f8a7f
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42572184"
---
# <a name="microsoft-specific-modifiers"></a>Modificateurs Microsoft spécifiques
Cette section décrit les extensions C++ spécifiques à Microsoft dans les domaines suivants :  
  
-   [Adressage basé sur](based-addressing.md), la pratique consistant à l’aide d’un pointeur comme base à partir de laquelle d’autres pointeurs peuvent être décalées  
  
-   [Conventions d’appel de fonction](calling-conventions.md)  
  
-   Attributs étendus de stockage-classe déclarés avec le [__declspec](declspec.md) mot clé  
  
-   Le [__w64](w64.md) mot clé  

### <a name="microsoft-specific-keywords"></a>Mots clés spécifiques à Microsoft  

Un grand nombre des mots clés spécifiques à Microsoft peuvent être utilisés pour modifier des déclarateurs afin de former des types dérivés. Pour plus d’informations sur les déclarateurs, consultez [déclarateurs](overview-of-declarators.md).  

|Mot clé|Signification|Utilisé pour former des types dérivés ?|   
|-------------|-------------|---------------------------------|
|[__based](based-grammar.md)|Le nom qui suit déclare un décalage de 32 bits par rapport à la base 32 bits contenue dans la déclaration.|Oui|   
|[__cdecl](cdecl.md)|Le nom qui suit utilise les conventions de nommage et d’appel du langage C.|Oui|      
|[__declspec](declspec.md)|Le nom qui suit spécifie un attribut de classe de stockage spécifique à Microsoft.|Non|    
|[__fastcall](fastcall.md)|Le nom qui suit déclare une fonction qui utilise des registres, lorsqu’ils sont disponibles, à la place de la pile, pour transmettre des arguments.|Oui|   
|[__restrict](extension-restrict.md)|Similaire à __declspec ([restreindre](restrict.md)), mais pour une utilisation sur les variables.|Non|      
|[__stdcall](stdcall.md)|Le nom qui suit spécifie une fonction qui respecte la convention d’appel standard.|Oui|     
|[__w64](w64.md)|Marque un type de données comme étant plus grand sur un compilateur 64 bits.|Non|    
|[__unaligned](unaligned.md)|Spécifie qu'un pointeur désignant un type ou d'autres données n'est pas aligné.|Non|      
|[__vectorcall](vectorcall.md)|Le nom qui suit déclare une fonction qui utilise des registres, y compris les registres SSE lorsqu’ils sont disponibles, à la place de la pile, pour transmettre des arguments.|Oui|      
    
## <a name="see-also"></a>Voir aussi     
 [Informations de référence sur le langage C++](cpp-language-reference.md)