---
title: Erreur irrécupérable NMAKE U1095 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1095
dev_langs:
- C++
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 964ec1d029e56a5d9d78659ad919c71a4e44506d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039879"
---
# <a name="nmake-fatal-error-u1095"></a>Erreur irrécupérable NMAKE U1095

ligne de commande développée « ligne de commande' trop long

Après une expansion macro, la ligne de commande donnée a dépassé la limite de longueur de lignes de commande du système d’exploitation.

MS-DOS autorise jusqu'à 128 caractères sur une ligne de commande.

Si la commande est d’un programme qui peut accepter une entrée de ligne de commande à partir d’un fichier, modifiez la commande et fournissez l’entrée à partir d’un fichier sur disque ou un fichier inline. Par exemple, lien et LIB acceptent une entrée à partir d’un fichier réponse.