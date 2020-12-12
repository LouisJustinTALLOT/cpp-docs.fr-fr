---
description: 'En savoir plus sur : propriétés du débogueur Android'
title: Propriétés du débogueur Android (C++)
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 27068b56421860b1e77b6cacf7e2ef4fae147a24
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136524"
---
# <a name="android-debugger-properties"></a>Propriétés du débogueur Android

| Propriété | Description | Choices |
|--|--|--|
| Type de débogueur | Spécifie le type de code à déboguer. | **Natif uniquement**<br /><br />**Java uniquement** |
| Cible de débogage | Spécifie l’émulateur ou l’appareil à utiliser pour le débogage. Si aucun émulateur n’est en cours d’exécution, utilisez’Android Virtual Device (AVD) Manager’pour démarrer un appareil. |
| Package à lancer | Spécifie l’emplacement du *. apk* qui sera débogué. Cette option démarre le package (APK) lorsque l’application est déboguée. |
| Lancer une activité | L’activité Android à utiliser pour lancer l’application doit correspondre à celle utilisée dans le manifeste. Appuyez sur appliquer pour récupérer la liste de *AndroidManifest.xml* et la remplir dynamiquement. |
| Autres chemins de recherche des symboles | Chemin de recherche supplémentaire pour les symboles de débogage. |
| Chemins de recherche de sources Java supplémentaires | Chemins de recherche supplémentaires pour les fichiers sources Java. (S’applique seulement quand le type du débogueur est Java uniquement.) |
