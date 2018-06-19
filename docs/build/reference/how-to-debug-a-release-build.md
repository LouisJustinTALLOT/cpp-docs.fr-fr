---
title: 'Comment : déboguer une version Release | Documents Microsoft'
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
ms.openlocfilehash: 7e733375f01d4b2b8ec7090f7f70ad1ec5280cd9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374477"
---
# <a name="how-to-debug-a-release-build"></a>Comment : déboguer une version release
Vous pouvez déboguer une version Release d’une application.  
  
### <a name="to-debug-a-release-build"></a>Pour déboguer une version Release  
  
1.  Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **C/C++** nœud. Définissez **Format des informations de débogage** à [compatible C7 (/ Z7)](../../build/reference/z7-zi-zi-debug-information-format.md) ou **la base de données de programme (/ Zi)**.  
  
3.  Développez **l’éditeur de liens** et cliquez sur le **général** nœud. Définissez **activation des liens incrémentiels** à [non (/ INCREMENTAL : NO)](../../build/reference/incremental-link-incrementally.md).  
  
4.  Sélectionnez le **débogage** nœud. Définissez **générer des infos de débogage** à [Oui (/Debug)](../../build/reference/debug-generate-debug-info.md).  
  
5.  Sélectionnez le **optimisation** nœud. Définissez **références** à [/OPT : REF](../../build/reference/opt-optimizations.md) et **activer le repli COMDAT** à [/OPT : ICF](../../build/reference/opt-optimizations.md).  
  
6.  Vous pouvez maintenant déboguer votre application de version release. Pour rechercher un problème, parcourez le code (ou le débogage juste-à-temps d’utilisation) jusqu'à ce que vous trouviez où la défaillance se produit, puis déterminer le code ou les paramètres incorrects.  
  
     Si une application fonctionne dans une version debug, mais échoue dans une version Release, une des optimisations du compilateur peut présenter une erreur dans le code source. Pour isoler le problème, désactivez les optimisations sélectionnées pour chaque fichier de code source jusqu'à ce que vous trouviez le fichier et l’optimisation qui provoque le problème. (Pour accélérer le processus, vous pouvez diviser les fichiers en deux groupes, désactiver l’optimisation sur un groupe et lorsque vous identifiez un problème dans un groupe, continuer à le diviser jusqu'à ce que vous ayez le fichier posant problème.)  
  
     Vous pouvez utiliser [/RTC.](../../build/reference/rtc-run-time-error-checks.md) pour tenter d’exposer des bogues dans vos versions debug.  
  
     Pour plus d’informations, consultez [optimisation du Code](../../build/reference/optimizing-your-code.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution de problèmes liés à la version Release](../../build/reference/fixing-release-build-problems.md)