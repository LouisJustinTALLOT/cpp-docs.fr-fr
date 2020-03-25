---
title: Erreur de génération de projet PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 7d1c11ab7539f25d371c0bfbd2853b6155c9661c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192951"
---
# <a name="project-build-error-prj0008"></a>Erreur de génération de projet PRJ0008

Impossible de supprimer le fichier’fichier'.

**Assurez-vous que le fichier n’est pas ouvert par un autre processus et qu’il n’est pas protégé en écriture.**

Pendant une reconstruction ou un nettoyage, C++ Visual supprime tous les fichiers intermédiaires et de sortie connus pour la génération, ainsi que tous les fichiers qui répondent aux spécifications de caractères génériques dans la propriété **extensions à supprimer** en cas de nettoyage dans la [page de propriétés paramètres de configuration généraux](../../build/reference/general-property-page-project.md).

Cette erreur s’affiche si Visual C++ n’est pas en mesure de supprimer un fichier. Pour résoudre l’erreur, rendez le fichier et son répertoire accessible en écriture pour l’utilisateur qui effectue la génération.
