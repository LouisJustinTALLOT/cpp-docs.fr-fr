---
title: 'main : démarrage du programme'
ms.date: 11/04/2016
f1_keywords:
- vc.main.startup
- _tmain
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
ms.openlocfilehash: 29e1b77c2e36c66e4e6fc4ec30a73af4d57654a0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857435"
---
# <a name="main-program-startup"></a>main : démarrage du programme

Une fonction spéciale nommée **main** est le point de départ de l’exécution de tous C++ les programmes et C. Si vous écrivez du code conforme au modèle de programmation Unicode, vous pouvez utiliser `wmain`, qui est la version à caractères larges de **main**.

La fonction **main** n’est pas prédéfinie par le compilateur. Elle doit être fournie dans le texte du programme.

La syntaxe de déclaration pour **main** est

```cpp
int main();
```

ou, éventuellement,

```cpp
int main(int argc, char *argv[], char *envp[]);
```

**Section spécifique de Microsoft**

La syntaxe de déclaration pour `wmain` est la suivante :

```cpp
int wmain( );
```

ou, éventuellement,

```cpp
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

Vous pouvez également utiliser `_tmain`, qui est défini dans Tchar. h. `_tmain` est résolu en **main** , sauf si _UNICODE est défini. Dans ce cas, `_tmain` est résolu à `wmain`.

Les fonctions **main** et `wmain` peuvent également être déclarées comme renvoyant **void** (aucune valeur de retour). Si vous déclarez **main** ou `wmain` comme renvoyant **void**, vous ne pouvez pas retourner de code de sortie au processus parent ou au système d’exploitation à l’aide d’une instruction [Return](../cpp/return-statement-in-program-termination-cpp.md) . Pour retourner un code de sortie lorsque **main** ou `wmain` est déclaré comme **void**, vous devez utiliser la fonction [Exit](../cpp/exit-function.md) .

**Fin de la section spécifique de Microsoft**

Les types pour `argc` et `argv` sont définis par le langage. Les noms `argc`, `argv` et `envp` sont traditionnels, mais ne sont pas requis par le compilateur. Pour plus d’informations et pour obtenir un exemple, consultez [définitions d’arguments](../cpp/argument-definitions.md).

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Utilisation de wmain au lieu de main](../cpp/using-wmain-instead-of-main.md)<br/>
[Restrictions relatives à la fonction main](../cpp/main-function-restrictions.md)<br/>
[Analyse des arguments de ligne de commande C++](../cpp/parsing-cpp-command-line-arguments.md)
