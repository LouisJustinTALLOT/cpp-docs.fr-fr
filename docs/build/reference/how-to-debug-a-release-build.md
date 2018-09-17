---
title: 'Comment : déboguer une version Release | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2dcafe151edf907521c2db49b4ffacca38593e9b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723903"
---
# <a name="how-to-debug-a-release-build"></a>Comment : déboguer une version release

Vous pouvez déboguer une version Release d’une application.

### <a name="to-debug-a-release-build"></a>Pour déboguer une version Release

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le **C/C++** nœud. Définissez **Format des informations de débogage** à [compatible C7 (/ Z7)](../../build/reference/z7-zi-zi-debug-information-format.md) ou **la base de données de programme (/Zi)**.

1. Développez **l’éditeur de liens** et cliquez sur le **général** nœud. Définissez **activation des liens incrémentiels** à [non (/ INCREMENTAL : NO)](../../build/reference/incremental-link-incrementally.md).

1. Sélectionnez le **débogage** nœud. Définissez **Generate Debug Info** à [Oui (/Debug)](../../build/reference/debug-generate-debug-info.md).

1. Sélectionnez le **optimisation** nœud. Définissez **références** à [/OPT : REF](../../build/reference/opt-optimizations.md) et **activation du repli COMDAT** à [/OPT : ICF](../../build/reference/opt-optimizations.md).

1. Vous pouvez maintenant déboguer votre application de la build mise en production. Pour rechercher un problème, parcourez le code (ou le débogage juste-à-temps d’utilisation) jusqu'à ce que vous trouviez où la défaillance se produit et déterminer le code ou les paramètres incorrects.

   Si une application fonctionne dans une version debug, mais échoue dans une version Release, une des optimisations du compilateur peut présenter une erreur dans le code source. Pour isoler le problème, désactivez les optimisations sélectionnées pour chaque fichier de code source jusqu'à ce que vous trouviez le fichier et l’optimisation qui provoque le problème. (Pour accélérer le processus, vous pouvez diviser les fichiers en deux groupes, désactiver l’optimisation sur un groupe et lorsque vous rencontrez un problème dans un groupe, continuer à diviser jusqu'à ce que vous isoler le fichier posant problème.)

   Vous pouvez utiliser [/RTC](../../build/reference/rtc-run-time-error-checks.md) pour tenter d’exposer des bogues dans vos versions debug.

   Pour plus d’informations, consultez [optimisation du Code](../../build/reference/optimizing-your-code.md).

## <a name="see-also"></a>Voir aussi

[Résolution de problèmes liés à la version Release](../../build/reference/fixing-release-build-problems.md)