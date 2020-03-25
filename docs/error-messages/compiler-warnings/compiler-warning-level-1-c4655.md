---
title: Avertissement du compilateur (niveau 1) C4655
ms.date: 08/27/2018
f1_keywords:
- C4655
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
ms.openlocfilehash: d4c409c2d69099853a872142e05ef0fcda5a7655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199529"
---
# <a name="compiler-warning-level-1-c4655"></a>Avertissement du compilateur (niveau 1) C4655

> '*symbol*' : le type de variable est nouveau depuis la dernière génération, ou est défini différemment à un autre endroit

## <a name="remarks"></a>Notes

Vous avez modifié ou ajouté un nouveau type de données depuis la dernière génération réussie. Modifier & Continuer ne prend pas en charge les modifications sur les types de données existants.

Cet avertissement est suivi d’une [erreur irrécupérable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Pour plus d’informations, consultez [Modifications de code prises en charge](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Pour supprimer cet avertissement sans mettre fin à la session de débogage en cours

1. Replacez le type de données dans l’état où il se trouvait avant l’erreur.

2. Dans le menu **Déboguer** , choisissez **Appliquer les modifications du code**.

### <a name="to-remove-this-warning-without-changing-your-source-code"></a>Pour supprimer cette erreur sans modifier votre code source

1. Dans le menu **Déboguer** , choisissez **Arrêter le débogage**.

2. Dans le menu **Générer** , cliquez sur **Générer**.
