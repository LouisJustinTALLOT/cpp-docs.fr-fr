---
title: Importation d'appels de fonctions à l'aide de __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 1743cbba8c3046ef844f16be8e78d43c61f62606
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442519"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Importation d'appels de fonctions à l'aide de __declspec(dllimport)

L’exemple de code suivant montre comment utiliser **_declspec (dllimport)** pour importer des appels de fonction à partir d’une dll dans une application. Supposons que `func1` est une fonction qui réside dans une DLL distincte du fichier. exe qui contient la fonction **main** .

Sans **__declspec (dllimport)** , à partir de ce code :

```
int main(void)
{
   func1();
}
```

le compilateur génère du code qui ressemble à ceci :

```
call func1
```

et l’éditeur de liens traduit l’appel de la façon suivante :

```
call 0x4000000         ; The address of 'func1'.
```

Si `func1` existe dans une autre DLL, l’éditeur de liens ne peut pas résoudre cela directement, car il n’a aucun moyen de connaître l’adresse du `func1`. Dans les environnements 16 bits, l’éditeur de liens ajoute cette adresse de code à une liste dans le fichier. exe que le chargeur corrige au moment de l’exécution avec l’adresse correcte. Dans les environnements 32 bits et 64 bits, l’éditeur de liens génère un thunk dont il connaît l’adresse. Dans un environnement 32 bits, le thunk ressemble à ce qui suit :

```
0x40000000:    jmp DWORD PTR __imp_func1
```

Ici `imp_func1` est l’adresse de l’emplacement de `func1` dans la table d’adresses d’importation du fichier. exe. Toutes les adresses sont donc connues de l’éditeur de liens. Le chargeur doit uniquement mettre à jour la table d’adresses d’importation du fichier. exe au moment du chargement pour que tout fonctionne correctement.

Par conséquent, l’utilisation de **__declspec (dllimport)** est meilleure car l’éditeur de liens ne génère pas de thunk s’il n’est pas requis. Les thunks rendent le code plus volumineux (sur les systèmes RISC, il peut y avoir plusieurs instructions) et peuvent dégrader les performances de votre cache. Si vous indiquez au compilateur que la fonction se trouve dans une DLL, elle peut générer un appel indirect pour vous.

Voici maintenant ce code :

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

génère l’instruction suivante :

```
call DWORD PTR __imp_func1
```

Il n’existe pas de thunk et aucune instruction `jmp`, le code est donc plus petit et plus rapide.

En revanche, pour les appels de fonction à l’intérieur d’une DLL, vous ne souhaitez pas avoir à utiliser un appel indirect. Vous connaissez déjà l’adresse d’une fonction. Étant donné que le temps et l’espace sont nécessaires pour charger et stocker l’adresse de la fonction avant un appel indirect, un appel direct est toujours plus rapide et plus petit. Vous souhaitez uniquement utiliser **__declspec (dllimport)** lors de l’appel de fonctions dll à partir de l’extérieur de la dll elle-même. N’utilisez pas **__declspec (dllimport)** sur les fonctions à l’intérieur d’une dll lors de la génération de cette dll.

## <a name="see-also"></a>Voir aussi

[Importation dans une application](importing-into-an-application.md)
