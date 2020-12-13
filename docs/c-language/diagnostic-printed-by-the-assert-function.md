---
description: 'En savoir plus sur : diagnostic imprimé par la fonction Assert'
title: Diagnostic imprimé par la fonction d'assertion
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: cab4f6dfd2cab7d4b46486a103b39abb6ca17005
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186790"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostic imprimé par la fonction d'assertion

**ANSI 4.2** Diagnostic imprimé et comportement d'arrêt de la fonction **assert**

La fonction **assert** imprime un message de diagnostic et appelle la routine **abort** si l'expression est false (0). Le message de diagnostic se présente sous la forme

> **Assertion failed**: <em>expression</em>**, file** <em>filename</em>**, line** *linenumber*

où *filename* est le nom du fichier source et *linenumber* est le numéro de ligne de l’assertion qui a échoué dans le fichier source. Aucune action n’est effectuée si *expression* est true (différent de zéro).

## <a name="see-also"></a>Voir aussi

[Fonctions de la bibliothèque](../c-language/library-functions.md)
