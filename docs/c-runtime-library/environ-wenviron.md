---
title: _environ, _wenviron
ms.date: 11/04/2016
f1_keywords:
- environ
- wenviron
- _wenviron
- _environ
helpviewer_keywords:
- environ function
- _environ function
- _wenviron function
- process environment
- wenviron function
ms.assetid: 7e639962-6536-47cd-8095-0cbe44a56e03
ms.openlocfilehash: 56f6f1d06d834ccab68daf859fac065cf215582c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748921"
---
# <a name="environ-wenviron"></a>_environ, _wenviron

La variable `_environ` est un pointeur vers un tableau de pointeurs qui désignent les chaînes de caractères multioctets qui constituent l'environnement de processus. Cette variable globale a été déconseillée au profit des versions fonctionnelles plus sécurisées [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md) et [putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md), qui doivent être utilisées à la place de la variable globale. `_environ` est déclaré dans Stdlib.h.

> [!IMPORTANT]
>  Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```
extern char **_environ;
```

## <a name="remarks"></a>Remarques

Dans un programme qui utilise la fonction `main`, `_environ` est initialisé au démarrage du programme en fonction des paramètres tirés de l'environnement de système d'exploitation. L'environnement se compose d'une ou plusieurs entrées de la forme

`ENVVARNAME` `=string`

`getenv_s` et `putenv_s` utilisent la variable `_environ` pour accéder à la table d'environnement et la modifier. Quand `_putenv` est appelé pour ajouter ou supprimer des paramètres d'environnement, la table d'environnement change de taille. Son emplacement dans la mémoire peut aussi changer, selon les besoins en mémoire du programme. La valeur de `_environ` est automatiquement ajustée en conséquence.

La variable `_wenviron`, déclarée dans Stdlib.h sous la forme :

```
extern wchar_t **_wenviron;
```

est une version à caractères larges de `_environ`. Dans un programme qui utilise la fonction `wmain`, `_wenviron` est initialisé au démarrage du programme en fonction des paramètres tirés de l'environnement de système d'exploitation.

Dans un programme qui utilise `main`, la valeur initiale de `_wenviron` est **NULL** car l’environnement se compose de chaînes de caractères multioctets. Au premier appel à `_wgetenv` ou `_wputenv`, un environnement à chaînes de caractères larges correspondant est créé et est désigné par `_wenviron`.

De la même manière, dans un programme qui utilise `wmain`, la valeur initiale de `_environ` est **NULL** car l’environnement se compose de chaînes de caractères larges. Au premier appel à `_getenv` ou `_putenv`, un environnement à chaînes de caractères multioctets correspondant est créé et est désigné par `_environ`.

Quand deux copies de l'environnement (MBCS et Unicode) existent simultanément dans un programme, le système Runtime doit gérer les deux copies, ce qui entraîne des temps d'exécution plus lents. Par exemple, quand vous appelez `_putenv`, un appel à `_wputenv` est aussi exécuté automatiquement, de sorte que les deux chaînes d'environnement correspondent.

> [!CAUTION]
>  Dans de rares cas, quand le système Runtime gère à la fois une version Unicode et une version multioctet de l'environnement, ces deux versions d'environnement peuvent ne pas correspondre exactement. En effet, même si une chaîne de caractères multioctets unique est mappée à une chaîne Unicode unique, le mappage d'une chaîne Unicode unique à une chaîne de caractères multioctets n'est pas nécessairement unique. Par conséquent, deux chaînes Unicode distinctes peuvent être mappées à une même chaîne multioctet.

Interroger `_environ` dans un contexte Unicode n'a pas de sens quand [/MD](../build/reference/md-mt-ld-use-run-time-library.md) ou une liaison `/MDd` est utilisé. Pour la DLL CRT, le type (large ou multioctet) du programme est inconnu. Seul le type multioctet est créé, car il s'agit du scénario le plus probable.

Le pseudo-code suivant illustre comment cela peut se produire.

```
int i, j;
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:
                                      // putenv ("env_var_z=string1")
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:
                                      // putenv("env_var_z=string2")
```

Dans la notation utilisée pour cet exemple, les chaînes de caractères ne sont pas des littéraux de chaîne C ; il s'agit plutôt d'espaces réservés qui représentent des littéraux de chaîne d'environnement Unicode dans l'appel `_wputenv` et des chaînes d'environnement multioctet dans l'appel `putenv`. Les espaces réservés de caractères « `x` » et « `y` » dans les deux chaînes d'environnement Unicode distinctes ne sont pas mappées de façon unique à des caractères de l'environnement MBCS actif. Au lieu de cela, toutes deux sont mappées à un certain caractère MBCS « `z` » qui est le résultat par défaut de la tentative de conversion des chaînes.

Ainsi, dans l'environnement multioctet, la valeur de « `env_var_z` » après le premier appel implicite à `putenv` est « `string1` », mais cette valeur est remplacée au deuxième appel implicite à `putenv`, quand « `env_var_z` » a la valeur « `string2` ». L'environnement Unicode (dans `_wenviron`) et l'environnement multioctet (dans `_environ`) sont donc différents à la suite de cette série d'appels.

## <a name="see-also"></a>Voir aussi

[Variables globales](../c-runtime-library/global-variables.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)
