---
title: Modificateurs spécifiques Microsoft | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 8490a50f30d366a53a9e3288417a8d83032c556d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420221"
---
# <a name="microsoft-specific-modifiers"></a>Modificateurs Microsoft spécifiques
Cette section décrit les extensions C++ spécifiques à Microsoft dans les domaines suivants :  
  
-   [Adressage](../cpp/based-addressing.md), la pratique de l’utilisation d’un pointeur comme base à partir de laquelle d’autres pointeurs peuvent être décalées  
  
-   [Conventions d’appel de fonction](../cpp/calling-conventions.md)  
  
-   Étendue des attributs de classe de stockage déclarés avec le [__declspec](../cpp/declspec.md) (mot clé)  
  
-   Le [__w64](../cpp/w64.md) (mot clé)  
  
 Un grand nombre des mots clés spécifiques à Microsoft peuvent être utilisés pour modifier des déclarateurs afin de former des types dérivés. Pour plus d’informations sur les déclarateurs, consultez [déclarateurs](http://msdn.microsoft.com/en-us/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838).  
  
### <a name="microsoft-specific-keywords"></a>Mots clés spécifiques à Microsoft  
  
|Mot clé|Signification|Utilisé pour former des types dérivés ?|  
|-------------|-------------|---------------------------------|  
|[__based](../cpp/based-grammar.md)|Le nom qui suit déclare un décalage de 32 bits par rapport à la base 32 bits contenue dans la déclaration.|Oui|  
|[__cdecl](../cpp/cdecl.md)|Le nom qui suit utilise les conventions de nommage et d’appel du langage C.|Oui|  
|[__declspec](../cpp/declspec.md)|Le nom qui suit spécifie un attribut de classe de stockage spécifique à Microsoft.|Non|  
|[__fastcall](../cpp/fastcall.md)|Le nom qui suit déclare une fonction qui utilise des registres, lorsqu’ils sont disponibles, à la place de la pile, pour transmettre des arguments.|Oui|  
|[__restrict](../cpp/extension-restrict.md)|Similaire à __declspec ([restreindre](../cpp/restrict.md)), mais pour une utilisation sur les variables.|Non|  
|[__stdcall](../cpp/stdcall.md)|Le nom qui suit spécifie une fonction qui respecte la convention d’appel standard.|Oui|  
|[__w64](../cpp/w64.md)|Marque un type de données comme étant plus grand sur un compilateur 64 bits.|Non|  
|[__unaligned](../cpp/unaligned.md)|Spécifie qu'un pointeur désignant un type ou d'autres données n'est pas aligné.|Non|  
|[__vectorcall](../cpp/vectorcall.md)|Le nom qui suit déclare une fonction qui utilise des registres, y compris les registres SSE lorsqu’ils sont disponibles, à la place de la pile, pour transmettre des arguments.|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)