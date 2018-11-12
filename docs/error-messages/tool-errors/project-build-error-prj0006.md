---
title: Erreur de génération de projet PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: d62c774411fda80a3e94044b3272567177328ff5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451557"
---
# <a name="project-build-error-prj0006"></a>Erreur de génération de projet PRJ0006

N’a pas pu ouvrir le fichier temporaire 'fichier'. Assurez-vous que le fichier existe et que le répertoire n’est pas protégé en écriture.

Visual C++ n’a pas pu créer un fichier temporaire pendant le processus de génération. Raisons sont :

- Aucun répertoire temporaire.

- Répertoire temporaire en lecture seule.

- Manque d’espace disque.

- Le dossier $ (IntDir) est en lecture seule ou contient des fichiers temporaires qui sont en lecture seule.

Cette erreur se produit également après erreur PRJ0007 : Impossible de créer répertoire sortie 'répertoire'. Erreur PRJ0007 signifie que le répertoire $ (IntDir) n’a pas pu être créé, ce qui implique la création de fichiers temporaires échouera également.

Fichiers temporaires sont créés chaque fois que vous spécifiez :

- Un fichier réponse.

- Une étape de génération personnalisée.

- Un événement de build.