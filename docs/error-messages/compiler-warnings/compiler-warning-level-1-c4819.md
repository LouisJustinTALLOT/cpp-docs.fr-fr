---
title: Avertissement du compilateur (niveau 1) C4819
ms.date: 11/04/2016
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: c0ca29a304fbd05cb0c6b7d1b06414304c70fb2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596610"
---
# <a name="compiler-warning-level-1-c4819"></a>Avertissement du compilateur (niveau 1) C4819

Le fichier contient un caractère qui ne peut pas être représenté dans la page de codes actuelle (numéro). Enregistrez le fichier au format Unicode pour éviter toute perte de données.

L'erreur C4819 se produit quand un fichier source ANSI est compilé sur un système avec une page de codes qui ne peut pas représenter tous les caractères compris dans le fichier.

Pour résoudre l'erreur C4819, enregistrez le fichier au format Unicode. Dans Visual Studio, choisissez **fichier**, **Options d’enregistrement avancées**. Dans le **Options d’enregistrement avancées** boîte de dialogue, sélectionnez un encodage qui peut représenter tous les caractères dans le fichier, par exemple, UTF-8, puis choisissez **OK**.