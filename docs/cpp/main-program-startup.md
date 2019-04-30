---
title: 'principal : Démarrage du programme'
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
ms.openlocfilehash: 358ae8ec88281bab741393b1196ee2a1e615e896
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345051"
---
# <a name="main-program-startup"></a>principal : Démarrage du programme

Une fonction spéciale nommée **principal** est le point de départ de l’exécution de tous les programmes C et C++. Si vous êtes écrire du code qui suit le modèle de programmation Unicode, vous pouvez utiliser `wmain`, qui est la version à caractères larges de **principal**.

Le **principal** fonction n’est pas prédéfinie par le compilateur. Elle doit être fournie dans le texte du programme.

La syntaxe de déclaration pour **principal** est

```cpp
int main();
```

ou, éventuellement,

```cpp
int main(int argc, char *argv[], char *envp[]);
```

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

La syntaxe de déclaration pour `wmain` est la suivante :

```cpp
int wmain( );
```

ou, éventuellement,

```cpp
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

Vous pouvez également utiliser `_tmain`, qui est définie dans tchar.h. `_tmain` correspond à **principal** , sauf si _UNICODE est défini. Dans ce cas, `_tmain` est résolu à `wmain`.

Vous pouvez également le **principal** et `wmain` fonctions peuvent être déclarées comme retournant **void** (aucune valeur de retour). Si vous déclarez **principal** ou `wmain` comme retournant **void**, vous ne peut pas retourner un code de sortie pour le processus parent ou le système d’exploitation en utilisant un [retourner](../cpp/return-statement-in-program-termination-cpp.md) instruction. Pour retourner un code de sortie lorsque **principal** ou `wmain` est déclaré comme **void**, vous devez utiliser le [quitter](../cpp/exit-function.md) (fonction).

**FIN de la section spécifique à Microsoft**

Les types pour `argc` et `argv` sont définis par le langage. Les noms `argc`, `argv` et `envp` sont traditionnels, mais ne sont pas requis par le compilateur. Pour plus d’informations et un exemple, consultez [définitions d’arguments](../cpp/argument-definitions.md).

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Utilisation de wmain au lieu de main](../cpp/using-wmain-instead-of-main.md)<br/>
[Restrictions relatives à la fonction main](../cpp/main-function-restrictions.md)<br/>
[Analyse des arguments de ligne de commande C++](../cpp/parsing-cpp-command-line-arguments.md)
