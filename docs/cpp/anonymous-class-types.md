---
title: Types de classe anonymes | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2f2b3f46a463eed0d330f7e22975197f76c900b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="anonymous-class-types"></a>Types de classe anonymes
Les classes peuvent être anonymes, autrement dit, ils peuvent être déclarées sans un *identificateur*. Cela est utile lorsque vous remplacez un nom de classe par un nom de `typedef`, comme dans l'exemple suivant :  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
> [!NOTE]
>  L'utilisation de classes anonymes indiquée dans l'exemple précédent est utile pour conserver la compatibilité avec un code C existant. Dans du code C, l'utilisation de `typedef` conjointement aux structures anonymes est généralisée.  
  
 Les classes anonymes sont également utiles lorsque vous souhaitez qu'une référence à un membre de classe apparaisse comme si elle n'était pas été contenue dans une classe distincte, comme dans l'exemple suivant :  
  
```  
struct PTValue  
{  
    POINT ptLoc;  
    union  
    {  
        int  iValue;  
        long lValue;  
    };  
};  
  
PTValue ptv;  
```  
  
 Dans le code précédent, `iValue` accessibles à l’aide de l’opérateur de sélection de membre d’objet (**.**) comme suit :  
  
```  
int i = ptv.iValue;  
```  
  
 Les classes anonymes sont soumises à certaines restrictions. (Pour plus d’informations sur les unions anonymes, consultez [Unions](../cpp/unions.md).) Classes anonymes :  
  
-   Ne peut pas avoir de constructeur ou de destructeur.  
  
-   Ne peut pas être passé en tant qu'argument aux fonctions (à moins que la vérification de type soit invalidée en utilisant des points de suspension).  
  
-   Ne peut pas être retourné comme valeurs de retour à partir des fonctions.  
  
## <a name="anonymous-structs"></a>Structs anonymes  
  
### <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Une extension Microsoft C vous permet de déclarer une variable de structure dans une autre structure sans lui donner un nom. Ces structures imbriquées sont appelées des structures anonymes. C++ n'autorise pas les structures anonymes.  
  
 Vous pouvez accéder aux membres d'une structure anonyme comme s'ils étaient des membres de la structure conteneur.  
  
```  
// anonymous_structures.c  
#include <stdio.h>  
  
struct phone  
{  
    int  areacode;  
    long number;  
};  
  
struct person  
{  
    char   name[30];  
    char   gender;  
    int    age;  
    int    weight;  
    struct phone;    // Anonymous structure; no name needed  
} Jim;  
  
int main()  
{  
    Jim.number = 1234567;  
    printf_s("%d\n", Jim.number);     
}  
//Output: 1234567  
```  
  
**FIN de la section spécifique à Microsoft**  
  
