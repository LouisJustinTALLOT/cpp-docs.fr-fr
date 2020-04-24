---
title: Appels avec un nombre variable d’arguments
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- arguments [C++], variable number of
- VARARGS.H
- ellipsis (...), variable number of arguments
- STDARGS.H
- function calls, arguments
- '... ellipsis'
- function calls, variable number of arguments
ms.assetid: 8808fb26-4822-42f5-aba3-ac64b54e151b
ms.openlocfilehash: 22a2a363379163073ca722511d0baa0690110310
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032107"
---
# <a name="calls-with-a-variable-number-of-arguments"></a>Appels avec un nombre variable d’arguments

Une liste de paramètres partielle peut être terminée par la notation de sélection, une virgule suivie de trois points (**, ...**), pour indiquer qu’il peut y avoir plusieurs arguments passés à la fonction, mais qu’il n’y a pas d’informations supplémentaires fournies sur eux. La vérification du type n’est pas exécutée sur de tels arguments. Au moins un paramètre doit précéder la notation de sélection et celle-ci doit être le dernier jeton de la liste de paramètres. Sans cette notation de sélection, le comportement d'une fonction est indéfini s'il reçoit des paramètres en plus de ceux déclarés dans la liste de paramètres.

Pour appeler une fonction avec un nombre variable d'arguments, spécifiez simplement un nombre d'arguments dans l'appel de fonction. La fonction `printf` est un exemple de fonction de la bibliothèque Runtime C. L'appel de fonction doit inclure un argument pour chaque nom de type déclaré dans la liste de paramètres ou la liste de types d'argument.

Tous les arguments spécifiés dans l'appel de fonction sont placés sur la pile à moins que la convention d'appel `__fastcall` soit spécifiée. Le nombre de paramètres déclarés pour la fonction détermine le nombre d'arguments pris de la pile et assignés aux paramètres. Vous êtes chargé de récupérer tous les arguments supplémentaires de la pile et de déterminer le nombre d'arguments présents. Le fichier STDARG.H contient des macros de style ANSI pour accéder aux arguments de fonctions acceptant un nombre variable d'arguments. En outre, les macros de style XENIX dans VARARGS.H sont encore prises en charge.

Cette déclaration d’exemple est destinée à une fonction qui demande un nombre variable d’arguments :

```
int average( int first, ...);
```

## <a name="see-also"></a>Voir aussi

[Appels de fonction](../c-language/function-calls.md)
