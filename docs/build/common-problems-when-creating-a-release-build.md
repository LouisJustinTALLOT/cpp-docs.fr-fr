---
description: 'En savoir plus sur : problèmes courants lors de la création d’une version Release'
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
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: 7470b87a33b9dc0cb6f7e85b9cfa7b7c1216a936
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163091"
---
# <a name="common-problems-when-creating-a-release-build"></a>Problèmes courants lors de la création d’une version release

Pendant le développement, vous créez et testez généralement avec une version Debug de votre projet. Si vous générez ensuite votre application pour une version Release, vous risquez d’obtenir une violation d’accès.

La liste ci-dessous montre les principales différences entre une version Debug et une version Release (qui n’est pas déboguée). Il existe d’autres différences, mais voici les principales différences qui provoqueraient l’échec d’une application dans une version Release lorsqu’elle fonctionne dans une version Debug.

- [Disposition du tas](#_core_heap_layout)

- [Compilation](#_core_compilation)

- [Prise en charge du pointeur](#_core_pointer_support)

- [Optimisations](#_core_optimizations)

Pour plus d’informations sur la façon d’intercepter les erreurs de build de version dans les versions de débogage, consultez l’option de compilateur [/gz (Catch Release-Build Errors in Debug Build)](reference/gz-enable-stack-frame-run-time-error-checking.md) .

## <a name="heap-layout"></a><a name="_core_heap_layout"></a> Disposition du tas

La disposition du tas sera la cause d’environ 90% des problèmes apparentés lorsqu’une application fonctionne dans Debug, mais pas dans la version Release.

Quand vous générez votre projet pour le débogage, vous utilisez l’allocateur de mémoire de débogage. Cela signifie que toutes les allocations de mémoire sont placées autour des octets de garde. Ces octets de protection détectent un remplacement de mémoire. Étant donné que la disposition du tas diffère entre les versions release et Debug, un remplacement de mémoire peut ne pas créer de problèmes dans une version Debug, mais peut avoir des effets catastrophiques dans une version Release.

Pour plus d’informations, consultez [vérifier le remplacement de mémoire](checking-for-memory-overwrites.md) et [Utilisez la version Debug pour vérifier le remplacement de mémoire](using-the-debug-build-to-check-for-memory-overwrite.md).

## <a name="compilation"></a><a name="_core_compilation"></a> Élaboration

La plupart des macros MFC et la majeure partie de l’implémentation de MFC changent lorsque vous générez pour la version finale. En particulier, la macro Assert prend la valeur Nothing dans une version Release, donc aucun code trouvé dans assertions ne sera exécuté. Pour plus d’informations, consultez [examiner les instructions Assert](using-verify-instead-of-assert.md).

Certaines fonctions sont Inline pour une vitesse accrue dans la version Release. Les optimisations sont généralement activées dans une version Release. Un allocateur de mémoire différent est également utilisé.

## <a name="pointer-support"></a><a name="_core_pointer_support"></a> Prise en charge du pointeur

L’absence d’informations de débogage supprime le remplissage de votre application. Dans une version Release, les pointeurs isolés ont une plus grande chance de pointer vers une mémoire non initialisée au lieu de pointer vers les informations de débogage.

## <a name="optimizations"></a><a name="_core_optimizations"></a> Optimisations

Selon la nature de certains segments de code, le compilateur d’optimisation peut générer du code inattendu. Il s’agit de la cause la moins probable des problèmes de génération de version, mais cela se produit à l’occasion. Pour obtenir une solution, consultez [optimisation de votre code](optimizing-your-code.md).

## <a name="see-also"></a>Voir aussi

[Versions Release](release-builds.md)<br/>
[Résolution des problèmes de version Release](fixing-release-build-problems.md)
