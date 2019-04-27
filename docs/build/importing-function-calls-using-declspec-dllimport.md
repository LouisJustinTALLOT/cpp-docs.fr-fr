---
title: Importation d'appels de fonctions à l'aide de __declspec(dllimport)
ms.date: 11/04/2016
f1_keywords:
- __declspec
- dllimport
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 8635cf5d389f72972f471a4fd53ed56c3497bfe9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188793"
---
# <a name="importing-function-calls-using-declspecdllimport"></a>Importation d'appels de fonctions à l'aide de __declspec(dllimport)

L’exemple de code suivant montre comment utiliser **_declspec (dllimport)** pour importer des appels de fonction à partir d’une DLL dans une application. Supposons que `func1` est une fonction qui réside dans une DLL séparée du fichier .exe qui contient le **principal** (fonction).

Sans **__declspec (dllimport)**, étant donné ce code :

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

et l’éditeur de liens convertit l’appel en quelque chose comme ceci :

```
call 0x4000000         ; The address of 'func1'.
```

Si `func1` existe dans une autre DLL, l’éditeur de liens ne peut pas résoudre ce directement, car il n’a aucun moyen de déterminer l’adresse de `func1` est. Dans les environnements de 16 bits, l’éditeur de liens ajoute cette adresse de code à une liste dans le fichier .exe que le chargeur pourrait corriger au moment de l’exécution avec l’adresse correcte. Dans les environnements 32 bits et 64 bits, l’éditeur de liens génère un thunk dont il connaît l’adresse. Dans un environnement 32 bits le thunk ressemble à :

```
0x40000000:    jmp DWORD PTR __imp_func1
```

Ici `imp_func1` est l’adresse pour le `func1` emplacement dans la table d’adresses importation du fichier .exe. Toutes les adresses sont ainsi connues de l’éditeur de liens. Le chargeur doit seulement mettre à jour la table des adresses d’importation du fichier .exe au moment du chargement pour que tout fonctionne correctement.

Par conséquent, l’utilisation **__declspec (dllimport)** est préférable, car l’éditeur de liens ne génère pas un thunk si elle n’est pas obligatoire. Thunks augmentent le code (sur les systèmes RISC, il peut représenter plusieurs instructions) et peut dégrader les performances du cache. Si vous indiquez au compilateur de que la fonction se trouve dans une DLL, il peut générer un appel indirect pour vous.

Par conséquent, ce code :

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

génère cette instruction :

```
call DWORD PTR __imp_func1
```

Il y a aucune conversion de code et non `jmp` obtenir des instructions, par conséquent, le code est plus petit et plus rapide.

En revanche, pour les appels de fonction à l’intérieur d’une DLL, vous ne souhaitez pas obligé d’utiliser un appel indirect. Vous savez déjà une adresse de fonction. Étant donné que le temps et espace sont requis pour charger et stocker l’adresse de la fonction avant un appel indirect, un appel direct est toujours plus rapide et plus petits. Vous souhaitez uniquement utiliser **__declspec (dllimport)** lors de l’appel des fonctions DLL depuis l’extérieur de la DLL proprement dite. N’utilisez pas **__declspec (dllimport)** sur les fonctions à l’intérieur d’une DLL lors de la génération de cette DLL.

## <a name="see-also"></a>Voir aussi

[Importation dans une application](importing-into-an-application.md)
