---
title: Importation d’appels de fonctions à l’aide de __declspec(dllimport)
description: Comment et pourquoi utiliser __declspec (dllimport) lors de l’appel de fonctions et de données de DLL.
ms.date: 05/03/2020
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 515fbdb2824c1eaf41e822adeae1a16d3072eec4
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765719"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Importation d’appels de fonction à l’aide de`__declspec(dllimport)`

L’annotation des appels à l' **`__declspec(dllimport)`** aide de la peut les rendre plus rapides. **`__declspec(dllimport)`** est toujours requis pour accéder aux données DLL exportées.

## <a name="import-a-function-from-a-dll"></a>Importer une fonction à partir d’une DLL

L’exemple de code suivant montre comment utiliser **`__declspec(dllimport)`** pour importer des appels de fonction à partir d’une dll dans une application. Supposons `func1` que est une fonction qui se trouve dans une dll distincte du fichier exécutable qui contient la fonction **main** .

Sans **`__declspec(dllimport)`**, étant donné ce code :

```C
int main(void)
{
   func1();
}
```

le compilateur génère du code qui ressemble à ceci :

```asm
call func1
```

et l’éditeur de liens traduit l’appel de la façon suivante :

```asm
call 0x4000000         ; The address of 'func1'.
```

Si `func1` existe dans une autre dll, l’éditeur de liens ne peut pas résoudre cette adresse directement, car il n’a aucun moyen `func1` de savoir quelle est l’adresse. Dans les environnements 32 bits et 64 bits, l’éditeur de liens génère un thunk à une adresse connue. Dans un environnement 32 bits, le thunk ressemble à ce qui suit :

```asm
0x40000000:    jmp DWORD PTR __imp_func1
```

Voici `__imp_func1` l’adresse de l' `func1` emplacement dans la table d’adresses d’importation du fichier exécutable. Toutes ces adresses sont connues de l’éditeur de liens. Le chargeur doit uniquement mettre à jour la table d’adresses d’importation du fichier exécutable au moment du chargement pour que tout fonctionne correctement.

C’est la raison **`__declspec(dllimport)`** pour laquelle l’utilisation de est meilleure : car l’éditeur de liens ne génère pas de thunk s’il n’est pas requis. Les thunks rendent le code plus volumineux (sur les systèmes RISC, il peut y avoir plusieurs instructions) et peuvent dégrader les performances de votre cache. Si vous indiquez au compilateur que la fonction se trouve dans une DLL, elle peut générer un appel indirect pour vous.

Voici maintenant ce code :

```C
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

génère l’instruction suivante :

```asm
call DWORD PTR __imp_func1
```

Il n’existe pas de thunk `jmp` et aucune instruction. le code est donc plus petit et plus rapide. Vous pouvez également avoir le même effet sans **`__declspec(dllimport)`** utiliser l’optimisation de l’ensemble du programme. Pour plus d’informations, consultez l’article [/GL (Optimisation de l’ensemble du programme)](reference/gl-whole-program-optimization.md).

Pour les appels de fonction dans une DLL, vous ne souhaitez pas avoir à utiliser un appel indirect. L’éditeur de liens connaît déjà l’adresse de la fonction. Le chargement et l’enregistrement de l’adresse de la fonction avant un appel indirect prennent du temps et de l’espace supplémentaires. Un appel direct est toujours plus rapide et plus petit. Vous ne souhaitez utiliser **`__declspec(dllimport)`** que lors de l’appel de fonctions dll à partir de l’extérieur de la dll elle-même. N’utilisez **`__declspec(dllimport)`** pas sur des fonctions à l’intérieur d’une dll lors de la génération de cette dll.

## <a name="see-also"></a>Voir aussi

[Importation dans une application](importing-into-an-application.md)
