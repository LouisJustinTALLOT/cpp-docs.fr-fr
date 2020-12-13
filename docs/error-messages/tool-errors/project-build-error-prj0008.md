---
description: 'En savoir plus sur : erreur de génération de projet PRJ0008'
title: Erreur de génération de projet PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 2ae4952dfd3e5c5f53a3f549536598402ce1fd48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343910"
---
# <a name="project-build-error-prj0008"></a>Erreur de génération de projet PRJ0008

Impossible de supprimer le fichier’fichier'.

**Assurez-vous que le fichier n’est pas ouvert par un autre processus et qu’il n’est pas protégé en écriture.**

Pendant une reconstruction ou un nettoyage, Visual C++ supprime tous les fichiers de sortie et de sortie connus pour la génération, ainsi que tous les fichiers qui répondent aux spécifications de caractères génériques dans la propriété **extensions à supprimer lors du nettoyage** de la [page de propriétés paramètres de configuration généraux](../../build/reference/general-property-page-project.md).

Cette erreur s’affiche si Visual C++ n’est pas en mesure de supprimer un fichier. Pour résoudre l’erreur, rendez le fichier et son répertoire accessible en écriture pour l’utilisateur qui effectue la génération.
