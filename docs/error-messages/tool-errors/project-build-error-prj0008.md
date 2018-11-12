---
title: Erreur de génération de projet PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 696b77e9906b231a680027a3faaf23e53d8fb6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525903"
---
# <a name="project-build-error-prj0008"></a>Erreur de génération de projet PRJ0008

N’a pas pu supprimer le fichier 'fichier'.

**Assurez-vous que le fichier n’est pas ouvert par un autre processus et qu’il n’est pas protégé en écriture.**

Lors d’une reconstruction ou de nettoyage, Visual C++ supprime tous les fichiers intermédiaires et de sortie connus de la génération, ainsi que tous les fichiers qui répondent aux spécifications de caractères génériques dans le **Extensions à supprimer lors du nettoyage** propriété dans le [général Page de propriétés de paramètres de configuration](../../ide/general-property-page-project.md).

Vous verrez cette erreur si Visual C++ n’est pas en mesure de supprimer un fichier. Pour résoudre l’erreur, veillez au fichier et son répertoire accessible en écriture pour l’utilisateur qui effectue la build.