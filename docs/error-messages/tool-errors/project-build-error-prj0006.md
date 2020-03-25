---
title: Erreur de génération de projet PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: 816355276a203adba1401841ce02eb94a18085b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192781"
---
# <a name="project-build-error-prj0006"></a>Erreur de génération de projet PRJ0006

Impossible d’ouvrir le fichier temporaire’fichier'. Assurez-vous que le fichier existe et que le répertoire n’est pas protégé en écriture.

Visual C++ n’a pas pu créer un fichier temporaire pendant le processus de génération. Les raisons peuvent être les suivantes :

- Aucun répertoire temporaire.

- Répertoire temporaire en lecture seule.

- Espace disque insuffisant.

- Le dossier $ (IntDir) est en lecture seule ou contient des fichiers temporaires qui sont en lecture seule.

Cette erreur se produit également après l’erreur projet PRJ0007 : impossible de créer le répertoire de sortie’répertoire'. L’erreur projet PRJ0007 signifie que le répertoire $ (IntDir) n’a pas pu être créé, ce qui implique que la création de fichiers temporaires échouera également.

Les fichiers temporaires sont créés chaque fois que vous spécifiez :

- Fichier réponse.

- Étape de génération personnalisée.

- Événement de Build.
