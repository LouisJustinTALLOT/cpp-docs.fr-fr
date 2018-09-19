---
title: Diagnostic affiché par la fonction assert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac5473a2dd592bbd9af2f65044d3d7d97515dc37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103384"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostic imprimé par la fonction d'assertion

**ANSI 4.2** Diagnostic imprimé et comportement d'arrêt de la fonction **assert**

La fonction **assert** imprime un message de diagnostic et appelle la routine **abort** si l'expression est false (0). Le message de diagnostic se présente sous la forme

> **Assertion failed**: <em>expression</em>**, file** <em>filename</em>**, line** *linenumber*

où *filename* est le nom du fichier source et *linenumber* est le numéro de ligne de l’assertion qui a échoué dans le fichier source. Aucune action n’est effectuée si *expression* est true (différent de zéro).

## <a name="see-also"></a>Voir aussi

[Fonctions des bibliothèques](../c-language/library-functions.md)