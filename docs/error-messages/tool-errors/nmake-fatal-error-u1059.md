---
title: Erreur irrécupérable NMAKE U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 3c148bf2feb7ba12686e00b29f5bf90cb9f2f2d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367289"
---
# <a name="nmake-fatal-error-u1059"></a>Erreur irrécupérable NMAKE U1059

> Erreur de syntaxe : '}' manquant dans le fichier dépendant

Un chemin de recherche pour une dépendance a été incorrectement spécifié. Soit un espace existe dans le chemin d’accès ou l’accolade fermante (**}**) a été omis.

La syntaxe pour une spécification de répertoire pour une dépendance est

> **{** *directories* **}dependent**

où *répertoires* spécifie un ou plusieurs chemins d’accès, chacun étant séparés par un point-virgule (**;**). Sans les espaces sont autorisés.

Si tout ou partie d’un chemin de recherche est remplacé par une macro, assurez-vous que sans espaces existent dans l’expansion macro.