---
description: 'En savoir plus sur : erreur de génération de projet projet PRJ0009'
title: Erreur de génération de projet PRJ0009
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: 28a7a9ce1a4fa5f1b5b95ba208739b7172f0ac6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343884"
---
# <a name="project-build-error-prj0009"></a>Erreur de génération de projet PRJ0009

Le journal de génération n’a pas pu être ouvert en écriture.

**Assurez-vous que le fichier n’est pas ouvert par un autre processus et qu’il n’est pas protégé en écriture.**

Après avoir défini la propriété de **journalisation** de la génération sur **Oui** et effectué une génération ou une régénération, Visual C++ n’a pas pu ouvrir le journal de génération en mode exclusif.

Inspectez le paramètre de **journalisation de génération** en ouvrant la boîte de dialogue **options** (dans le menu **Outils** , cliquez sur commande **options** ), puis sélectionnez **Build VC + +** dans le dossier **projets** . Le fichier de build est appelé BuildLog.htm et est écrit dans le répertoire intermédiaire $ (IntDir).

Raisons possibles pour cette erreur :

- Vous exécutez deux processus de Visual C++ et vous essayez de générer la même configuration du même projet dans simultanément.

- Le fichier journal de génération est ouvert dans un processus qui verrouille le fichier.

- L’utilisateur n’a pas l’autorisation de créer un fichier.

- L’utilisateur actuel ne dispose pas d’un accès en écriture au fichier BuildLog.htm.
