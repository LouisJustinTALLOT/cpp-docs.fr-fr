---
description: 'En savoir plus sur : Comment : déboguer une version Release'
title: 'Comment : déboguer une version release'
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: bbe70a534a9d953ea1b739dba3a32296c7893930
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162701"
---
# <a name="how-to-debug-a-release-build"></a>Comment : déboguer une version release

Vous pouvez déboguer une version Release d’une application.

### <a name="to-debug-a-release-build"></a>Pour déboguer une version Release

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](working-with-project-properties.md).

1. Cliquez sur le nœud **C/C++** . Définissez le **format des informations de débogage** sur [Compatible C7 (/Z7)](reference/z7-zi-zi-debug-information-format.md) ou sur la **base de données du programme (/ZI)**.

1. Développez **éditeur de liens** , puis cliquez sur le nœud **général** . Définissez Activer l’édition de **liens incrémentielle** sur [non (/Incremental : no)](reference/incremental-link-incrementally.md).

1. Sélectionnez le nœud **débogage** . Définissez **générer les informations de débogage** sur [Oui (/Debug)](reference/debug-generate-debug-info.md).

1. Sélectionnez le nœud **optimisation** . Définissez les **références** à [/OPT : Ref](reference/opt-optimizations.md) et **activez le repli COMDAT** sur [/OPT : ICF](reference/opt-optimizations.md).

1. Vous pouvez désormais déboguer votre application de version Release. Pour identifier un problème, exécutez le code pas à pas (ou utilisez le débogage juste-à-temps) jusqu’à ce que vous trouviez l’endroit où se produit l’échec, puis déterminez les paramètres ou le code incorrects.

   Si une application fonctionne dans une version Debug, mais échoue dans une version Release, l’une des optimisations du compilateur peut exposer une erreur dans le code source. Pour isoler le problème, désactivez les optimisations sélectionnées pour chaque fichier de code source jusqu’à ce que vous trouviez le fichier et l’optimisation à l’origine du problème. (Pour accélérer le processus, vous pouvez diviser les fichiers en deux groupes, désactiver l’optimisation sur un groupe et, lorsque vous détectez un problème dans un groupe, continuer à diviser jusqu’à ce que vous isolez le fichier de problème.)

   Vous pouvez utiliser [/RTC](reference/rtc-run-time-error-checks.md) pour essayer d’exposer de tels bogues dans vos versions Debug.

   Pour plus d’informations, consultez [optimisation de votre code](optimizing-your-code.md).

## <a name="see-also"></a>Voir aussi

[Résolution des problèmes de version Release](fixing-release-build-problems.md)
