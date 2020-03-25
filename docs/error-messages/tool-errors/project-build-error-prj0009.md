---
title: Erreur de génération de projet PRJ0009
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: d02325504b04a13cd15dee0bd70891bf5a63b62e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192959"
---
# <a name="project-build-error-prj0009"></a>Erreur de génération de projet PRJ0009

Le journal de génération n’a pas pu être ouvert en écriture.

**Assurez-vous que le fichier n’est pas ouvert par un autre processus et qu’il n’est pas protégé en écriture.**

Après avoir défini la propriété de **journalisation** de la génération sur **Oui** et effectué une C++ génération ou une régénération, Visual n’a pas pu ouvrir le journal de génération en mode exclusif.

Inspectez le paramètre de **journalisation de génération** en ouvrant la boîte de dialogue **options** (dans le menu **Outils** , cliquez sur commande **options** ), puis sélectionnez **Build VC + +** dans le dossier **projets** . Le fichier de build est appelé BuildLog. htm et est écrit dans le répertoire intermédiaire $ (IntDir).

Raisons possibles pour cette erreur :

- Vous exécutez deux processus de Visual C++ et essayez de générer la même configuration du même projet dans simultanément.

- Le fichier journal de génération est ouvert dans un processus qui verrouille le fichier.

- L’utilisateur n’a pas l’autorisation de créer un fichier.

- L’utilisateur actuel ne dispose pas d’un accès en écriture au fichier BuildLog. htm.
