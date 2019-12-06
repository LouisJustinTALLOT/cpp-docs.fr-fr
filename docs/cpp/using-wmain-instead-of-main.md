---
title: Utilisation de wmain au lieu de main
ms.date: 11/04/2016
f1_keywords:
- wmain
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
ms.openlocfilehash: f47d7219a54b197ec59f109cf08879774b48e6f7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857214"
---
# <a name="using-wmain-instead-of-main"></a>Utilisation de wmain au lieu de main

**Section spécifique de Microsoft**

Dans le modèle de programmation Unicode, vous pouvez définir une version à caractères larges de la fonction `main`. Utilisez **wmain** au lieu de `main` si vous souhaitez écrire du code portable conforme à la spécification Unicode.

Vous déclarez des paramètres formels à **wmain** à l’aide d’un format similaire à `main`. Vous pouvez ensuite passer des arguments à caractère élargi et éventuellement un pointeur d’environnement à caractère élargi au programme. Les paramètres *argv* et *envp* de **wmain** sont de type `wchar_t*`.

Si votre programme utilise une fonction de `main`, l’environnement de caractères multioctets est créé par le système d’exploitation au démarrage du programme. Une copie à caractères larges de l’environnement est créée uniquement lorsque cela est nécessaire (par exemple, par un appel aux fonctions [_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md) ou [_wputenv](../c-runtime-library/reference/putenv-wputenv.md) ). Au premier appel à `_wputenv`, ou à `_wgetenv` si un environnement MBCS existe déjà, un environnement de chaîne à caractères larges correspondant est créé, puis désigné par la variable globale `_wenviron`, qui est une version à caractères larges de la variable globale `_environ`. À ce moment-là, deux copies de l'environnement (MBCS et Unicode) existent simultanément et sont conservées par le système d'exploitation pendant toute la vie du programme.

De même, si votre programme utilise une fonction **wmain** , un environnement MBCS (ASCII) est créé lors du premier appel à `_putenv` ou `getenv`, et est désigné par la variable globale `_environ`.

Pour plus d’informations sur l’environnement MBCS, consultez Jeux de caractères codés sur [un octet et multioctets](../c-runtime-library/single-byte-and-multibyte-character-sets.md) dans la référence de la *bibliothèque Runtime.*

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[main : démarrage du programme](../cpp/main-program-startup.md)