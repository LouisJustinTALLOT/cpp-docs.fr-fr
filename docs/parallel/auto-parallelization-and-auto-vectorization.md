---
title: Parallélisation et vectorisation automatiques | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1ff172fde385b4e814508aaf2b567ac15874069
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720389"
---
# <a name="auto-parallelization-and-auto-vectorization"></a>Parallélisation et vectorisation automatiques
Le paralléliseur automatique et le vectoriseur automatique sont conçus pour fournir des gains de performance automatiques pour les boucles de votre code.  
  
## <a name="auto-parallelizer"></a>Paralléliseur automatique  

Le [/Qpar](../build/reference/qpar-auto-parallelizer.md) permet de commutateur de compilateur *parallélisation automatique* de boucles dans votre code. Quand vous spécifiez cet indicateur sans modifier votre code existant, le compilateur évalue le code pour trouver des boucles susceptibles de tirer un bénéfice de la parallélisation. Comme il peut trouver des boucles qui n'effectuent pas un gros travail et qui ne tireront donc pas de bénéfice de la parallélisation, et comme chaque parallélisation non nécessaire peut provoquer la génération d'un pool de threads, de la synchronisation supplémentaire ou d'autres traitements tendant à ralentir les performances au lieu de les améliorer, le compilateur a une approche prudente dans la sélection des boucles qu'il parallélise. Par exemple, considérez l'exemple suivant dans lequel la limite supérieure de la boucle n'est pas connue au moment de la compilation :  
  
```cpp  
void loop_test(int u) {  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
Comme `u` peut être une valeur peu élevée, le compilateur ne va pas paralléliser automatiquement cette boucle. Vous pouvez cependant souhaiter qu'elle soit parallélisée, car vous savez que `u` aura toujours une valeur élevée. Pour activer la parallélisation automatique, spécifiez [#pragma hint_parallel](../preprocessor/loop.md), où `n` est le nombre de threads pour paralléliser sur. Dans l'exemple suivant, le compilateur tentera de paralléliser la boucle entre 8 threads.  
  
```cpp  
void loop_test(int u) {  
#pragma loop(hint_parallel(8))  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
Comme avec toutes les [directives pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), la syntaxe alternative `__pragma(loop(hint_parallel(n)))` est également pris en charge.  
  
Il existe quelques boucles que le compilateur ne peut pas paralléliser même si vous voulez qu'il le fasse. Voici un exemple :  
  
```cpp  
#pragma loop(hint_parallel(8))  
for (int i=0; i<upper_bound(); ++i)  
    A[i] = B[i] * C[i];  
```  
  
La fonction `upper_bound()` peut changer chaque fois qu'elle est appelée. Comme la limite supérieure ne peut pas être connue, le compilateur peut émettre un message de diagnostic expliquant pourquoi il ne peut pas paralléliser cette boucle. L'exemple suivant montre une boucle qui peut être parallélisée, une boucle qui ne peut pas être parallélisée, la syntaxe du compilateur à utiliser à l'invite de commandes et la sortie du compilateur pour chaque option de ligne de commande :  
  
```cpp  
int A[1000];  
void test() {  
#pragma loop(hint_parallel(0))  
    for (int i=0; i<1000; ++i) {  
        A[i] = A[i] + 1;  
    }  
  
    for (int i=1000; i<2000; ++i) {  
        A[i] = A[i] + 1;  
    }  
}  
```  
  
La compilation à l'aide de cette commande :  
  
`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:1`  
  
 génère cette sortie :  
  
```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
```
  
La compilation à l'aide de cette commande :  
  
`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:2`  
  
génère cette sortie :  
  
```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
d:\myproject\mytest.cpp(4) : loop not parallelized due to reason '1008'
```
  
Notez la différence des sorties entre les deux différents [/qpar-report (niveau de rapport du PARALLÉLISEUR automatique)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md) options. `/Qpar-report:1` génère des messages du paralléliseur seulement pour les boucles qui sont parallélisées. `/Qpar-report:2` génère des messages du paralléliseur pour les parallélisations qui sont effectuées et pour celles qui ne le sont pas.  
  
Pour plus d’informations sur les codes motifs et les messages, consultez [Messages du Vectoriseur et du PARALLÉLISEUR](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
## <a name="auto-vectorizer"></a>Vectoriseur automatique  
 
Le vectoriseur automatique analyse les boucles de votre code, et utilise les registres vectoriels et les instructions vectorielles sur l'ordinateur cible pour les exécuter si c'est possible. Ceci peut améliorer les performances de votre code. Le compilateur cible les instructions SSE2, AVX et AVX2 dans les processeurs Intel ou AMD, ou les instructions NEON sur les processeurs ARM, conformément à la [/arch](../build/reference/arch-minimum-cpu-architecture.md) basculer.  
  
Le vectoriseur automatique peut générer des instructions différentes de celles spécifiées par le commutateur `/arch`. Ces instructions sont surveillées par une vérification à l'exécution, destinée à s'assurer que ce code s'exécute correctement. Par exemple, quand vous compilez `/arch:SSE2`, des instructions SSE4.2 peuvent être générées. Une vérification à l'exécution contrôle que SSE4.2 est disponible sur le processeur cible et passe à une version non-SSE4.2 de la boucle si le processeur ne prend pas en charge ces instructions.  
  
Par défaut, le vectoriseur automatique est activé. Si vous souhaitez comparer les performances de votre code avec vectorisation, vous pouvez utiliser [Loop (no_vector) #pragma](../preprocessor/loop.md) pour désactiver la vectorisation d’une boucle donnée.  
  
```cpp
#pragma loop(no_vector)  
for (int i = 0; i < 1000; ++i)  
   A[i] = B[i] + C[i];  
```  
  
Comme avec toutes les [directives pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), la syntaxe alternative `__pragma(loop(no_vector))` est également pris en charge.  
  
Comme avec le PARALLÉLISEUR automatique, vous pouvez spécifier le [/Qvec-report (niveau de rapport du Vectoriseur automatique)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md) une option de ligne de commande pour signaler les seulement les boucles vectorisées —`/Qvec-report:1`— ou les deux avec succès et les boucles non vectorisées —`/Qvec-report:2`).  
  
Pour plus d’informations sur les codes motifs et les messages, consultez [Messages du Vectoriseur et du PARALLÉLISEUR](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
Pour obtenir un exemple montrant comment le vectoriseur fonctionne en pratique, consultez [Project Austin Part 2 of 6 : Page Curling](http://blogs.msdn.com/b/vcblog/archive/2012/09/27/10348494.aspx)  
  
## <a name="see-also"></a>Voir aussi  
 
[Boucle](../preprocessor/loop.md)   
[Programmation parallèle en Code natif](http://go.microsoft.com/fwlink/p/?linkid=263662)   
[/ Qpar (PARALLÉLISEUR automatique)](../build/reference/qpar-auto-parallelizer.md)   
[/ Qpar-report (rapport du PARALLÉLISEUR automatique niveau)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
[/ Qvec-report (Vectoriseur niveau de rapport)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)   
[Messages du vectoriseur et du paralléliseur](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)