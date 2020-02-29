---
title: Propriétés du débogueur AndroidC++()
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 8ff6e539828d697e103c820d05565969f6afb910
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177527"
---
# <a name="android-debugger-properties"></a>Propriétés du débogueur Android

Propriété | Description | Choices
--- | ---| ---
Type de débogueur | Spécifie le type de code à déboguer. | **Natif uniquement**<br>**Java uniquement**<br>
Cible de débogage | Spécifie l’émulateur ou l’appareil à utiliser pour le débogage. Si aucun émulateur n’est en cours d’exécution, utilisez’Android Virtual Device (AVD) Manager’pour démarrer un appareil.
Package à lancer | Spécifie l’emplacement du fichier *.apk* à déboguer. Cette option démarre le package (APK) lorsque l’application est déboguée.
Lancer une activité | L’activité Android à utiliser pour lancer l’application doit correspondre à celle utilisée dans le manifeste. Appuyez sur Appliquer pour récupérer la liste du fichier *AndroidManifest.xml* et la remplir dynamiquement.
Autres chemins de recherche des symboles | Chemin de recherche supplémentaire pour les symboles de débogage.
Chemins de recherche de sources Java supplémentaires | Chemins de recherche supplémentaires pour les fichiers sources Java. (S’applique seulement quand le type du débogueur est Java uniquement.)
