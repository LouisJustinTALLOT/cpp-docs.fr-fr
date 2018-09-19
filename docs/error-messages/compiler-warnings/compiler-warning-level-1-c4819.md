---
title: Compilateur avertissement (niveau 1) C4819 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4819
dev_langs:
- C++
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac468bc605c261b66f47fdf40efd1a01a5383d58
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074277"
---
# <a name="compiler-warning-level-1-c4819"></a>Avertissement du compilateur (niveau 1) C4819

Le fichier contient un caractère qui ne peut pas être représenté dans la page de codes actuelle (numéro). Enregistrez le fichier au format Unicode pour éviter toute perte de données.

L'erreur C4819 se produit quand un fichier source ANSI est compilé sur un système avec une page de codes qui ne peut pas représenter tous les caractères compris dans le fichier.

Pour résoudre l'erreur C4819, enregistrez le fichier au format Unicode. Dans Visual Studio, choisissez **fichier**, **Options d’enregistrement avancées**. Dans le **Options d’enregistrement avancées** boîte de dialogue, sélectionnez un encodage qui peut représenter tous les caractères dans le fichier, par exemple, UTF-8, puis choisissez **OK**.