---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4656'
title: Avertissement du compilateur (niveau 1) C4656
ms.date: 11/04/2016
f1_keywords:
- C4656
helpviewer_keywords:
- C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
ms.openlocfilehash: d902a7f7629f8bcbadab4ead240c06ebbf1aa33c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318808"
---
# <a name="compiler-warning-level-1-c4656"></a>Avertissement du compilateur (niveau 1) C4656

'Symbol' : le type de données est nouveau ou a été modifié depuis la dernière génération, ou est défini différemment à un autre endroit

Vous avez ajouté ou modifié un type de données, ce qui le rend nouveau pour votre code source depuis la dernière génération réussie. Modifier & Continuer ne prend pas en charge les modifications sur les types de données existants.

Cet avertissement sera toujours suivi d’une [Erreur irrécupérable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Pour plus d’informations, consultez [Modifications de code prises en charge](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Pour supprimer cet avertissement sans mettre fin à la session de débogage en cours

1. Replacez le type de données dans l’état où il se trouvait avant l’erreur.

1. Dans le menu **Déboguer** , choisissez **Appliquer les modifications du code**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Pour supprimer cette erreur sans modifier votre code source

1. Dans le menu **Déboguer** , choisissez **Arrêter le débogage**.

1. Dans le menu **Générer** , cliquez sur **Générer**.
