---
title: Erreur irrécupérable NMAKE U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 33be3312e1f0aaa7f1e8aad64b44ea9aefd25346
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182836"
---
# <a name="nmake-fatal-error-u1059"></a>Erreur irrécupérable NMAKE U1059

> erreur de syntaxe : '} 'manquant dans le dépendant

Un chemin de recherche pour un dépendant n’a pas été spécifié correctement. Soit un espace existe dans le chemin d’accès, soit l’accolade fermante ( **}** ) a été omise.

La syntaxe d’une spécification de répertoire pour un dépendant est

> **{** *Directories* **} dépendant**

où *répertoires* spécifie un ou plusieurs chemins d’accès, séparés par un point-virgule ( **;** ). Aucun espace n’est autorisé.

Si une partie ou la totalité d’un chemin de recherche est remplacée par une macro, assurez-vous qu’il n’existe aucun espace dans l’expansion macro.
