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
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: 9bd1cafe40417872d42f2e9e1427e5f2eccad7a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328867"
---
# <a name="common-problems-when-creating-a-release-build"></a>Problèmes courants lors de la création d’une version release

Pendant le développement, vous construireez et testerez habituellement avec une construction de débbug de votre projet. Si vous construisez ensuite votre demande de version, vous pouvez obtenir une violation d’accès.

La liste ci-dessous montre les principales différences entre un débbug et une version (nondebug) construire. Il ya d’autres différences, mais suivants sont les principales différences qui causerait une application à l’échec dans une version de construction quand il fonctionne dans une construction de débogé.

- [Mise en page du tas](#_core_heap_layout)

- [Compilation](#_core_compilation)

- [Soutien pointeur](#_core_pointer_support)

- [Optimisations](#_core_optimizations)

Voir l’option [compilateur /GZ (Catch Release-Build Errors in Debug Build)](reference/gz-enable-stack-frame-run-time-error-checking.md) pour obtenir des informations sur la façon de capter les erreurs de construction de version dans les constructions de déboges.

## <a name="heap-layout"></a><a name="_core_heap_layout"></a>Mise en page du tas

La disposition du tas sera la cause d’environ quatre-vingt-dix pour cent des problèmes apparents quand une application fonctionne dans le débbug, mais pas la libération.

Lorsque vous construisez votre projet de débog, vous utilisez l’alloueur de mémoire de débogé. Cela signifie que toutes les allocations de mémoire ont des octets de garde placés autour d’eux. Ces octets de garde détectent un surmortrite de mémoire. Parce que la disposition du tas est différente entre les versions de libération et de débog, un surmortrite de mémoire pourrait ne pas créer de problèmes dans une construction de débbug, mais peut avoir des effets catastrophiques dans une version.

Pour plus d’informations, voir [Check for Memory Overwrite](checking-for-memory-overwrites.md) et [Utilisez la construction Debug pour vérifier pour le sursoil de la mémoire](using-the-debug-build-to-check-for-memory-overwrite.md).

## <a name="compilation"></a><a name="_core_compilation"></a>Compilation

Bon nombre des macros MFC et une grande partie des modifications de mise en œuvre de MFC lorsque vous construisez pour la libération. En particulier, la macro ASSERT n’évalue à rien dans une version, de sorte qu’aucun code trouvé dans ASSERTs ne sera exécuté. Pour plus d’informations, voir [Examinez les déclarations ASSERT](using-verify-instead-of-assert.md).

Certaines fonctions sont inlined pour la vitesse accrue dans la construction de version. Les optimisations sont généralement activées dans une version. Un alloueur de mémoire différent est également utilisé.

## <a name="pointer-support"></a><a name="_core_pointer_support"></a>Soutien pointeur

Le manque d’informations de débogage supprime le rembourrage de votre application. Dans une version de construction, pointeurs errants ont une plus grande chance de pointer vers la mémoire uninitialisée au lieu de pointer vers l’information de déboiffée.

## <a name="optimizations"></a><a name="_core_optimizations"></a>Optimisations

Selon la nature de certains segments de code, le compilateur d’optimisation peut générer du code inattendu. C’est la cause la moins probable de problèmes de construction de libération, mais il ne se pose à l’occasion. Pour une solution, voir [Optimiser votre code](optimizing-your-code.md).

## <a name="see-also"></a>Voir aussi

[Versions Release](release-builds.md)<br/>
[Résolution de problèmes liés à la version release](fixing-release-build-problems.md)
