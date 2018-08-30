---
title: Erreur irrécupérable NMAKE U1059 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b54919398c757bfe05f747ff57341f31decfc61
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200788"
---
# <a name="nmake-fatal-error-u1059"></a>Erreur irrécupérable NMAKE U1059

> Erreur de syntaxe : '}' manquant dans le fichier dépendant

Un chemin de recherche pour une dépendance a été incorrectement spécifié. Soit un espace existe dans le chemin d’accès ou l’accolade fermante (**}**) a été omis.

La syntaxe pour une spécification de répertoire pour une dépendance est

> **{** *répertoires* **} dépendant**

où *répertoires* spécifie un ou plusieurs chemins d’accès, chacun étant séparés par un point-virgule (**;**). Sans les espaces sont autorisés.

Si tout ou partie d’un chemin de recherche est remplacé par une macro, assurez-vous que sans espaces existent dans l’expansion macro.