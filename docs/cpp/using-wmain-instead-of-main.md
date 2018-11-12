---
title: Utilisation de wmain au lieu de main
ms.date: 11/04/2016
f1_keywords:
- wmain
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
ms.openlocfilehash: 8cdc986d1582d2b26f137e3147ce78bc83e9daca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677758"
---
# <a name="using-wmain-instead-of-main"></a>Utilisation de wmain au lieu de main

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

Dans le modèle de programmation Unicode, vous pouvez définir une version à caractères larges de la `main` (fonction). Utilisez **wmain** au lieu de `main` si vous souhaitez écrire du code portable conforme à la spécification Unicode.

Vous déclarez des paramètres formels à **wmain** à l’aide d’un format identique à `main`. Vous pouvez ensuite passer des arguments à caractère élargi et éventuellement un pointeur d’environnement à caractère élargi au programme. Le *argv* et *envp* paramètres **wmain** sont de type `wchar_t*`.

Si votre programme utilise une `main` (fonction), l’environnement de caractère multioctets est créé par le système d’exploitation au démarrage du programme. Une copie de caractères larges de l’environnement est créée uniquement si nécessaire (par exemple, par un appel à la [_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md) ou [_wputenv](../c-runtime-library/reference/putenv-wputenv.md) fonctions). Au premier appel à `_wputenv`, ou à `_wgetenv` si un environnement MBCS existe déjà, un environnement de chaîne à caractères larges correspondant est créé, puis désigné par la variable globale `_wenviron`, qui est une version à caractères larges de la variable globale `_environ`. À ce moment-là, deux copies de l'environnement (MBCS et Unicode) existent simultanément et sont conservées par le système d'exploitation pendant toute la vie du programme.

De même, si votre programme utilise une **wmain** (fonction), un environnement MBCS (ASCII) est créé sur le premier appel à `_putenv` ou `getenv`et est pointée par le `_environ` (variable globale).

Pour plus d’informations sur l’environnement MBCS, consultez [un octet et des jeux de caractères multioctets](../c-runtime-library/single-byte-and-multibyte-character-sets.md) dans le *Run-Time Library Reference.*

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[main : démarrage du programme](../cpp/main-program-startup.md)