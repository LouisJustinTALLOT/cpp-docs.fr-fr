---
title: volatile (C++) | Microsoft Docs
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
ms.openlocfilehash: 82ea6211a51bbe45fa1613dd7bb682f363783367
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461921"
---
# <a name="volatile-c"></a>volatile (C++)
Qualificateur de type que vous pouvez utiliser pour déclarer qu'un objet peut être modifié dans le programme par le matériel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
volatile declarator ;  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) commutateur de compilateur pour modifier la façon dont le compilateur interprète ce mot clé.  
  
 Visual Studio interprète le **volatile** mot clé différemment en fonction de l’architecture cible. Pour ARM, si aucun **/volatile** option du compilateur est spécifiée, le compilateur agit comme si **/volatile:iso** ont été spécifiés. Pour les architectures autres qu’ARM, si aucun **/volatile** option du compilateur est spécifiée, le compilateur exécute comme si **/volatile:ms** ont été spécifiées ; par conséquent, pour les architectures autres que ARM nous fortement Il est recommandé que vous spécifiez **/volatile:iso**et utiliser des primitives de synchronisation explicites et les intrinsèques du compilateur lorsque vous êtes confronté à la mémoire est partagé entre plusieurs threads.  
  
 Vous pouvez utiliser la **volatile** qualificateur pour fournir l’accès aux emplacements de mémoire qui sont utilisées par les processus asynchrones tels que des gestionnaires d’interruptions.  
  
 Lorsque **volatile** est utilisé sur une variable qui a également la [__restrict](../cpp/extension-restrict.md) mot clé, **volatile** est prioritaire.  
  
 Si un **struct** membre est marqué comme **volatile**, puis **volatile** est propagée vers la structure toute entière. Si une structure n’a pas une longueur pouvant être copiée sur l’architecture actuelle en utilisant une instruction, **volatile** peut être complètement perdu sur cette structure.  
  
 Le **volatile** mot clé ne peut avoir aucune incidence sur un champ si une des conditions suivantes est remplie :  
  
-   La longueur du champ volatile dépasse la taille maximale pouvant être copiée sur l'architecture actuelle en utilisant une instruction.  
  
-   La longueur du conteneur plus externe **struct**, ou si elle est membre d’un éventuellement imbriqué **struct**— dépasse la taille maximale pouvant être copiée sur l’architecture actuelle en utilisant une instruction.  
  
 Bien que le processeur ne réorganise pas les accès mémoire non mis en cache, les variables non mis en cache doivent être marqués comme **volatile** afin de garantir que le compilateur ne réorganise pas la mémoire y accède.  
  
 Objets qui sont déclarés comme **volatile** ne sont pas utilisés dans certaines optimisations, car leurs valeurs peuvent être modifiées à tout moment.  Le système lit toujours la valeur actuelle d'un objet volatile lorsque la demande en est faite, même si une instruction précédente a demandé une valeur du même objet.  De même, la valeur de l'objet est écrite immédiatement sur l'assignation.  
  
## <a name="iso-compliant"></a>Conformité ISO  
 Si vous êtes familiarisé avec le mot-clé volatil c# ou familiarisé avec le comportement de **volatile** dans les versions antérieures de Visual C++, n’oubliez pas que la norme C ++ 11 ISO **volatile** mot clé est différente et est prise en charge dans Visual Studio lorsque le [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) option du compilateur est spécifiée. (Pour ARM, elle est spécifiée par défaut). Le **volatile** mot clé dans le code Standard ISO C ++ 11 doit être utilisé uniquement pour l’accès matériel ; ne l’utilisez pas pour la communication entre threads. Pour la communication entre threads, utilisez des mécanismes tels que [std::atomic\<T >](../standard-library/atomic.md) à partir de la [bibliothèque Standard C++](../standard-library/cpp-standard-library-reference.md).  
  
## <a name="end-of-iso-compliant"></a>Fin de la conformité ISO  
  
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Lorsque le **/volatile:ms** option du compilateur est utilisée, par défaut lorsque les architectures autres qu’ARM sont ciblées, le compilateur génère du code supplémentaire pour conserver l’ordre des références aux objets volatiles par ailleurs ordre des références à d’autres objets globaux. En particulier :  
  
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