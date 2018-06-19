---
title: Problèmes courants lors de la création d’une version Release | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting Visual C++
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8860783a2cf9fb88b28e24e0bc16eb16c0dd5d77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373164"
---
# <a name="common-problems-when-creating-a-release-build"></a>Problèmes courants lors de la création d’une version release
Pendant le développement, vous généralement générer et tester avec une version debug de votre projet. Si vous générez ensuite votre application pour une version release, vous pouvez obtenir une violation d’accès.  
  
 La liste ci-dessous répertorie les principales différences entre un debug et Release (non Debug). Autres différences existent, mais voici les principales différences sont de provoquer une Échec de l’application dans une version Release lorsqu’elle fonctionne dans une version debug.  
  
-   [Présentation du tas](#_core_heap_layout)  
  
-   [Compilation](#_core_compilation)  
  
-   [Prise en charge du pointeur](#_core_pointer_support)  
  
-   [Optimisations](#_core_optimizations)  
  
 Consultez le [/GZ (intercepter des erreurs de version Release dans la version Debug)](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md) option du compilateur pour plus d’informations sur l’interception version générer des erreurs dans les versions debug.  
  
##  <a name="_core_heap_layout"></a> Présentation du tas  
 Présentation du tas est à l’origine de 90 % environ des problèmes apparents quand une application fonctionne en version debug, mais pas la mise en production.  
  
 Lorsque vous générez votre projet pour le débogage, vous utilisez l’allocateur de mémoire de débogage. Cela signifie que toutes les allocations de mémoire ont des octets de protection placés autour d’elles. Ces octets de garde détectent un remplacement de mémoire. Étant donné que la mise en page de segment de mémoire est différent entre release et debug versions, un remplacement de mémoire ne peut pas créer d’incidents dans une version debug, mais peut avoir des effets catastrophiques dans une version Release.  
  
 Pour plus d’informations, consultez [vérifier les remplacements de mémoire](../../build/reference/checking-for-memory-overwrites.md) et [destiné à la version Debug pour vérifier l’écrasement de mémoire](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md).  
  
##  <a name="_core_compilation"></a> Compilation  
 Nombre de macros MFC et la plupart des modifications d’implémentation MFC quand vous générez pour la mise en production. En particulier, la macro ASSERT a la valeur nothing dans une version Release, aucun code trouvé dans les instructions Assert ne sera exécuté. Pour plus d’informations, consultez [examen des instructions ASSERT](../../build/reference/using-verify-instead-of-assert.md).  
  
 Certaines fonctions sont déclarées inline pour augmenter la vitesse de la version Release. Les optimisations sont généralement activées dans une version Release. Un allocateur de mémoire différent est également utilisé.  
  
##  <a name="_core_pointer_support"></a> Prise en charge du pointeur  
 L’absence d’informations de débogage supprime la marge intérieure de votre application. Dans une version Release, les pointeurs perdus ont plus de chances de pointant vers la mémoire non initialisée au lieu de pointer vers des informations de débogage.  
  
##  <a name="_core_optimizations"></a> Optimisations  
 Selon la nature de certains segments de code, le compilateur d’optimisation peut générer un code inattendu. Ceci est la moins probable des problèmes liés à la mise en production, mais il se produit à l’occasion. Pour une solution, consultez [optimisation du Code](../../build/reference/optimizing-your-code.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Versions Release](../../build/reference/release-builds.md)   
 [Résolution de problèmes liés à la version Release](../../build/reference/fixing-release-build-problems.md)