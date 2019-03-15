---
title: 'Procédure : Déboguer une version Release'
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: 6d93fac4e980085c322acb55e6f8758e6cea0a00
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826170"
---
# <a name="how-to-debug-a-release-build"></a>Procédure : Déboguer une version Release

Vous pouvez déboguer une version Release d’une application.

### <a name="to-debug-a-release-build"></a>Pour déboguer une version Release

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](working-with-project-properties.md).

1. Cliquez sur le **C/C++** nœud. Définissez **Format des informations de débogage** à [compatible C7 (/ Z7)](reference/z7-zi-zi-debug-information-format.md) ou **la base de données de programme (/Zi)**.

1. Développez **l’éditeur de liens** et cliquez sur le **général** nœud. Définissez **activation des liens incrémentiels** à [non (/ INCREMENTAL : NO)](reference/incremental-link-incrementally.md).

1. Sélectionnez le **débogage** nœud. Définissez **Generate Debug Info** à [Oui (/Debug)](reference/debug-generate-debug-info.md).

1. Sélectionnez le **optimisation** nœud. Définissez **références** à [/OPT : REF](reference/opt-optimizations.md) et **activation du repli COMDAT** à [/OPT : ICF](reference/opt-optimizations.md).

1. Vous pouvez maintenant déboguer votre application de la build mise en production. Pour rechercher un problème, parcourez le code (ou le débogage juste-à-temps d’utilisation) jusqu'à ce que vous trouviez où la défaillance se produit et déterminer le code ou les paramètres incorrects.

   Si une application fonctionne dans une version debug, mais échoue dans une version Release, une des optimisations du compilateur peut présenter une erreur dans le code source. Pour isoler le problème, désactivez les optimisations sélectionnées pour chaque fichier de code source jusqu'à ce que vous trouviez le fichier et l’optimisation qui provoque le problème. (Pour accélérer le processus, vous pouvez diviser les fichiers en deux groupes, désactiver l’optimisation sur un groupe et lorsque vous rencontrez un problème dans un groupe, continuer à diviser jusqu'à ce que vous isoler le fichier posant problème.)

   Vous pouvez utiliser [/RTC](reference/rtc-run-time-error-checks.md) pour tenter d’exposer des bogues dans vos versions debug.

   Pour plus d’informations, consultez [optimisation du Code](optimizing-your-code.md).

## <a name="see-also"></a>Voir aussi

[Résolution de problèmes liés à la version Release](fixing-release-build-problems.md)
