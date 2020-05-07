---
title: Diagnostic imprimé par la fonction d'assertion
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: 666ba22d642b772fe8ad336f57ab1bdd82bd2e18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234221"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostic imprimé par la fonction d'assertion

**ANSI 4.2** Diagnostic imprimé et comportement d'arrêt de la fonction **assert**

La fonction **assert** imprime un message de diagnostic et appelle la routine **abort** si l'expression est false (0). Le message de diagnostic se présente sous la forme

> **Assertion failed**: <em>expression</em>**, file** <em>filename</em>**, line** *linenumber*

où *filename* est le nom du fichier source et *linenumber* est le numéro de ligne de l’assertion qui a échoué dans le fichier source. Aucune action n’est effectuée si *expression* est true (différent de zéro).

## <a name="see-also"></a>Voir aussi

[Fonctions de la bibliothèque](../c-language/library-functions.md)
