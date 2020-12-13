---
description: 'En savoir plus sur : erreur de génération de projet projet PRJ0006'
title: Erreur de génération de projet PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: a78646c843a6c6df3b4e2847076670492a9efb6b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343923"
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
