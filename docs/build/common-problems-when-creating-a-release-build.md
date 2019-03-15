---
title: Problèmes courants lors de la création d’une version release
ms.date: 11/04/2016
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
ms.openlocfilehash: 7420fd5bbdeec30e9839206803952c02b8b56421
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825917"
---
# <a name="common-problems-when-creating-a-release-build"></a>Problèmes courants lors de la création d’une version release

Pendant le développement, vous généralement générer et tester avec une version debug de votre projet. Si vous générez ensuite votre application pour une version Release, vous pouvez obtenir une violation d’accès.

La liste ci-dessous montre les principales différences entre un débogage et une version Release (non Debug). Voici les autres différences, mais voici les principales différences qui entraînent une Échec de l’application dans une version Release lorsqu’il fonctionne dans une version debug.

- [Présentation du tas](#_core_heap_layout)

- [Compilation](#_core_compilation)

- [Prise en charge du pointeur](#_core_pointer_support)

- [optimisations](#_core_optimizations)

Consultez le [/GZ (intercepter les erreurs de la version Release dans la version Debug)](reference/gz-enable-stack-frame-run-time-error-checking.md) option du compilateur pour plus d’informations sur l’interception de mise en production des erreurs dans les versions debug de build.

##  <a name="_core_heap_layout"></a> Présentation du tas

Présentation du tas est à l’origine de 90 % environ des problèmes apparents quand une application fonctionne dans le débogage, mais pas la mise en production.

Lorsque vous générez votre projet pour le débogage, vous utilisez l’allocateur de mémoire de débogage. Cela signifie que toutes les allocations de mémoire ont des octets de protection placées autour d’elles. Ces octets de garde détectent un remplacement de mémoire. Étant donné que la présentation du tas est différente entre release et debug versions, un remplacement de mémoire ne peut pas créer d’incidents dans une version debug, mais peut avoir des effets catastrophiques dans une version Release.

Pour plus d’informations, consultez [vérifier pour le remplacement de la mémoire](checking-for-memory-overwrites.md) et [utiliser la version Debug pour vérifier pour le remplacement de la mémoire](using-the-debug-build-to-check-for-memory-overwrite.md).

##  <a name="_core_compilation"></a> Compilation

Un grand nombre des macros MFC et quantité de modifications d’implémentation MFC quand vous générez pour la mise en production. En particulier, la macro ASSERT a la valeur nothing dans une version Release, aucun code trouvé dans les instructions Assert ne sera exécuté. Pour plus d’informations, consultez [examen des instructions ASSERT](using-verify-instead-of-assert.md).

Certaines fonctions sont déclarées inline pour une vitesse accrue dans la version Release. Les optimisations sont généralement activées dans une version Release. Un allocateur de mémoire différent est également utilisé.

##  <a name="_core_pointer_support"></a> Prise en charge du pointeur

L’absence d’informations de débogage supprime la marge intérieure de votre application. Dans une version Release, les pointeurs perdus ont plus de chances de pointant vers la mémoire non initialisée au lieu de pointer vers des informations de débogage.

##  <a name="_core_optimizations"></a> optimisations

Selon la nature de certains segments de code, le compilateur d’optimisation peut générer un code inattendu. C’est la cause moins probable des problèmes liés à la mise en production, mais elle s’à l’occasion. Pour une solution, consultez [optimisation du Code](optimizing-your-code.md).

## <a name="see-also"></a>Voir aussi

[Versions Release](release-builds.md)<br/>
[Résolution de problèmes liés à la version Release](fixing-release-build-problems.md)
