---
title: Propriétés Android Debugger (C)
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 23fd871f030593607cf374870b96e09d8bc2da7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374198"
---
# <a name="android-debugger-properties"></a>Propriétés du débogueur Android

| Propriété | Description | Choices |
|--|--|--|
| Type de débogueur | Spécifie le type de code à déboguer. | **Autochtone seulement**<br /><br />**Java uniquement** |
| Cible de débogage | Spécifie l’émulateur ou l’appareil à utiliser pour le débogage. Si aucun émulateur n’est en cours d’exécution, utilisez alors 'Android Virtual Device (AVD) Manager' pour démarrer un appareil. |
| Package à lancer | Spécifie l’emplacement du *.apk* qui sera déboisé. Cette option démarre le paquet (APK) lorsque l’application est débogée. |
| Lancer une activité | L’activité Android à utiliser pour lancer l’application doit correspondre à celle utilisée dans le manifeste. Appuyez sur Appliquer pour récupérer la liste de *AndroidManifest.xml* et le peupler dynamiquement. |
| Autres chemins de recherche des symboles | Chemin de recherche supplémentaire pour les symboles de débogage. |
| Chemins de recherche de sources Java supplémentaires | Chemins de recherche supplémentaires pour les fichiers sources Java. (S’applique seulement quand le type du débogueur est Java uniquement.) |
