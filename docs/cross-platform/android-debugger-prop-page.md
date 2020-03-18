---
title: Propriétés du débogueur AndroidC++()
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 3ac896b384181e4e2b436368f39a343d35fe321a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446894"
---
# <a name="android-debugger-properties"></a>Propriétés du débogueur Android

| Propriété | Description | Choices |
|--|--|--|
| Type de débogueur | Spécifie le type de code à déboguer. | **Natif uniquement**<br /><br />**Java uniquement** |
| Cible de débogage | Spécifie l’émulateur ou l’appareil à utiliser pour le débogage. Si aucun émulateur n’est en cours d’exécution, utilisez’Android Virtual Device (AVD) Manager’pour démarrer un appareil. |
| Package à lancer | Spécifie l’emplacement du fichier *.apk* à déboguer. Cette option démarre le package (APK) lorsque l’application est déboguée. |
| Lancer une activité | L’activité Android à utiliser pour lancer l’application doit correspondre à celle utilisée dans le manifeste. Appuyez sur Appliquer pour récupérer la liste du fichier *AndroidManifest.xml* et la remplir dynamiquement. |
| Autres chemins de recherche des symboles | Chemin de recherche supplémentaire pour les symboles de débogage. |
| Chemins de recherche de sources Java supplémentaires | Chemins de recherche supplémentaires pour les fichiers sources Java. (S’applique seulement quand le type du débogueur est Java uniquement.) |
