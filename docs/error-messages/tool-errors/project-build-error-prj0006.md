---
title: Erreur de génération PRJ0006 de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0006
dev_langs:
- C++
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 264b2f90a2d778b1545117ce5c3b1272626ebad6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073250"
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