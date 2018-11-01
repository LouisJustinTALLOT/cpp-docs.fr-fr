---
title: Erreur de génération de projet PRJ0009
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: 963b7c861f9e8ee7105ebdc23afff08c4be46465
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438094"
---
# <a name="project-build-error-prj0009"></a>Erreur de génération de projet PRJ0009

Build journal n’a pas pu être ouvert en écriture.

**Assurez-vous que le fichier n’est pas ouvert par un autre processus et qu’il n’est pas protégé en écriture.**

Après avoir défini le **journal de génération** propriété **Oui** et effectuer une génération ou une régénération, Visual C++ n’a pas pu ouvrir le journal de génération en mode exclusif.

Inspecter le **journal de génération** définition en ouvrant le **Options** boîte de dialogue (sur le **outils** menu, cliquez sur **Options** commande), puis en sélectionnant **VC ++ Build** dans le **projets** dossier. Le fichier de build est appelé BuildLog.htm et est écrit dans le répertoire intermédiaire $(IntDir).

Raisons possibles de cette erreur :

- Vous exécutez deux processus de Visual C++ et essaie de générer la même configuration du même projet dans les deux simultanément.

- Le fichier journal de génération est ouvert dans un processus qui verrouille le fichier.

- L’utilisateur ne dispose pas d’autorisation pour créer un fichier.

- L’utilisateur actuel n’a pas d’accès en écriture au fichier BuildLog.htm.