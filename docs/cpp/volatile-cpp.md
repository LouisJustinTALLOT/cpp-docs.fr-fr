---
title: volatile (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- volatile_cpp
dev_langs:
- C++
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 295654586a3fe251526a4764d54f80f3a70c7014
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423952"
---
# <a name="volatile-c"></a>volatile (C++)
Qualificateur de type que vous pouvez utiliser pour déclarer qu'un objet peut être modifié dans le programme par le matériel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
volatile declarator ;  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) commutateur de compilateur pour modifier la façon dont le compilateur interprète ce mot clé.  
  
 Visual Studio interprète le mot clé `volatile` différemment selon l'architecture cible. Pour ARM, si aucun **/volatile** option du compilateur est spécifiée, le compilateur agit comme si **/volatile:iso** ont été spécifiés. Pour les architectures autres qu’ARM, si aucun **/volatile** option du compilateur est spécifiée, le compilateur effectue comme si **/volatile:ms** ont été spécifiées ; par conséquent, pour les architectures autres que ARM, nous vous Il est recommandé que vous spécifiez **/volatile:iso**et utiliser des primitives de synchronisation explicites et les intrinsèques du compilateur lorsque vous travaillez avec une mémoire qui est partagée entre plusieurs threads.  
  
 Vous pouvez utiliser le qualificateur `volatile` pour fournir un accès aux emplacements de mémoire utilisés par des processus asynchrones tels que les gestionnaires d'interruptions.  
  
 Lorsque `volatile` est utilisé sur une variable qui a également la [__restrict](../cpp/extension-restrict.md) (mot clé), `volatile` est prioritaire.  
  
 Si un membre `struct` est marqué comme `volatile`, `volatile` est propagé à l'ensemble de la structure. Si la longueur d'une structure ne peut pas être copiée sur l'architecture actuelle en utilisant une instruction, `volatile` peut être complètement perdu sur cette structure.  
  
 Le mot clé `volatile` peut ne pas avoir d'effet sur un champ si l'une des conditions suivantes est vraie :  
  
-   La longueur du champ volatile dépasse la taille maximale pouvant être copiée sur l'architecture actuelle en utilisant une instruction.  
  
-   La longueur du `struct` conteneur le plus externe, ou s'il s'agit d'un membre d'un `struct` éventuellement imbriqué, dépasse la taille maximale pouvant être copiée sur l'architecture actuelle en utilisant une instruction.  
  
 Bien que le processeur ne réorganise pas les accès à la mémoire ne pouvant pas être mise en cache, les variables qui ne peuvent pas être mises en cache doivent être marquées comme `volatile` pour garantir que le compilateur ne réorganise pas les accès à la mémoire.  
  
 Les objets déclarés comme `volatile` ne sont pas utilisés dans certaines optimisations, car leurs valeurs peuvent changer à tout moment.  Le système lit toujours la valeur actuelle d'un objet volatile lorsque la demande en est faite, même si une instruction précédente a demandé une valeur du même objet.  De même, la valeur de l'objet est écrite immédiatement sur l'assignation.  
  
## <a name="iso-compliant"></a>Conformité ISO  
 Si vous êtes familiarisé avec le langage c# mot clé volatile ou familiarisé avec le comportement de `volatile` dans les versions antérieures de Visual C++, gardez à l’esprit que la norme C ++ 11 ISO `volatile` (mot clé) est différent et est pris en charge dans Visual Studio lorsque le [/ volatile : iso](../build/reference/volatile-volatile-keyword-interpretation.md) option du compilateur est spécifiée. (Pour ARM, elle est spécifiée par défaut). Le mot clé `volatile` dans le code de norme ISO C++11 doit être utilisé uniquement pour l'accès matériel ; ne l'utilisez pas pour la communication entre les threads. Pour la communication entre les threads, utilisez des mécanismes tels que [std::atomic\<T >](../standard-library/atomic.md) à partir de la [bibliothèque Standard C++](../standard-library/cpp-standard-library-reference.md).  
  
## <a name="end-of-iso-compliant"></a>Fin de la conformité ISO  
  
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Lorsque le **/volatile:ms** option du compilateur est utilisée, par défaut lorsque les architectures autres que ARM sont ciblées, le compilateur génère un code supplémentaire pour conserver l’ordre des références aux objets volatiles, en plus de conserver ordre des références à d’autres objets globaux. En particulier :  
  
-   L’écriture dans un objet volatile (également appelée "écriture volatile") a une sémantique Release, c’est-à-dire, une référence à un objet global ou statique qui se produit avant qu’une écriture dans un objet volatile de la séquence d’instructions ne se produise avant cette écriture volatile dans le fichier binaire compilé.  
  
-   La lecture d'un objet volatile (également appelée "lecture volatile") a une sémantique Acquire, c'est-à-dire, une référence à un objet global ou statique qui se produit après qu'une lecture de la mémoire volatile dans la séquence d'instructions se produit après cette lecture volatile dans le fichier binaire compilé.  
  
 Cela permet aux objets volatiles d’être utilisés pour les verrous et les libérations de mémoire dans les applications multithread.  
  
> [!NOTE]
>  Lorsqu’il repose sur la garantie améliorée fournie quand le **/volatile:ms** option du compilateur est utilisée, le code n’est pas portable.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés](../cpp/keywords-cpp.md)   
 [const](../cpp/const-cpp.md)   
 [const et volatile, pointeurs](../cpp/const-and-volatile-pointers.md)