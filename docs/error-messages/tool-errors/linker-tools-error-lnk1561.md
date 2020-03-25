---
title: Erreur des outils Éditeur de liens LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: 706cf6c90dc187b6c343edc82cebb93bb8660452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194848"
---
# <a name="linker-tools-error-lnk1561"></a>Erreur des outils Éditeur de liens LNK1561

le point d’entrée doit être défini

L’éditeur de liens n’a pas trouvé de *point d’entrée*, la fonction initiale à appeler dans votre fichier exécutable. Par défaut, l’éditeur de liens recherche une fonction `main` ou `wmain` pour une application console, une fonction `WinMain` ou `wWinMain` pour une application Windows, ou `DllMain` pour une DLL qui requiert une initialisation. Vous pouvez spécifier une autre fonction à l’aide de l’option de l’éditeur de liens [/entry](../../build/reference/entry-entry-point-symbol.md) .

Cette erreur peut avoir plusieurs causes :
- Vous n’avez peut-être pas inclus le fichier qui définit votre point d’entrée dans la liste des fichiers à lier. Vérifiez que le fichier qui contient la fonction de point d’entrée est lié à votre application.
- Vous avez peut-être défini le point d’entrée à l’aide d’une signature de fonction incorrecte. par exemple, vous avez peut-être mal orthographié ou utilisé une casse incorrecte pour le nom de la fonction, ou spécifié le type de retour ou les types de paramètres de manière incorrecte.
- Vous n’avez peut-être pas spécifié l’option [/dll](../../build/reference/dll-build-a-dll.md) lors de la génération d’une dll.
- Vous avez peut-être spécifié de manière incorrecte le nom de la fonction de point d’entrée lorsque vous avez utilisé l’option de l’éditeur de liens [/entry](../../build/reference/entry-entry-point-symbol.md) .
- Si vous utilisez l’outil [lib](../../build/reference/lib-reference.md) pour générer une dll, vous avez peut-être spécifié un fichier. def. Dans ce cas, supprimez le fichier. def de la Build.

Lors de la génération d’une application, l’éditeur de liens recherche une fonction de point d’entrée à appeler pour démarrer votre code. Il s’agit de la fonction appelée après le chargement de l’application et de l’initialisation du Runtime. Vous devez fournir une fonction de point d’entrée pour une application, ou votre application ne peut pas s’exécuter. Un point d’entrée est facultatif pour une DLL. Par défaut, l’éditeur de liens recherche une fonction de point d’entrée qui a l’un des noms et signatures spécifiques, par exemple `int main(int, char**)`. Vous pouvez spécifier un autre nom de fonction comme point d’entrée à l’aide de l’option/ENTRY de l’éditeur de liens.

## <a name="example"></a>Exemple

L’exemple suivant génère l’LNK1561 :

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
