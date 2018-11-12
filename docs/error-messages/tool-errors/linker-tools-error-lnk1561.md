---
title: Erreur des outils Éditeur de liens LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: ad216c7b7a09b8dd5d2ca2b86bc3a386fa18a552
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552813"
---
# <a name="linker-tools-error-lnk1561"></a>Erreur des outils Éditeur de liens LNK1561

point d’entrée doit être défini.

L’éditeur de liens n’a pas trouvé un *point d’entrée*, la fonction initiale à appeler dans votre fichier exécutable. Par défaut, l’éditeur de liens recherche un `main` ou `wmain` (fonction) pour une application console, un `WinMain` ou `wWinMain` (fonction) pour une application Windows, ou `DllMain` pour une DLL qui requiert une initialisation. Vous pouvez spécifier une autre fonction en utilisant le [/Entry](../../build/reference/entry-entry-point-symbol.md) option de l’éditeur de liens.

Cette erreur peut avoir plusieurs causes :
- Vous n’avez ne peut-être pas inclus le fichier qui définit votre point d’entrée dans la liste des fichiers à lier. Vérifiez que le fichier qui contient la fonction de point d’entrée est lié à votre application.
- Il pouvez que vous avez défini le point d’entrée à l’aide de la signature de fonction incorrect ; par exemple, vous pourrez mal orthographié ou utilisé une casse incorrecte pour le nom de fonction ou spécifié de manière incorrecte le type de retour ou les types de paramètre.
- Vous n’avez ne peut-être pas spécifié le [/DLL](../../build/reference/dll-build-a-dll.md) option lors de la création d’une DLL.
- Vous avez peut-être spécifié le nom de la fonction de point d’entrée incorrectement lorsque vous avez utilisé le [/Entry](../../build/reference/entry-entry-point-symbol.md) option de l’éditeur de liens.
- Si vous utilisez le [LIB](../../build/reference/lib-reference.md) outil pour générer une DLL, vous avez peut-être spécifié un fichier .def. Dans ce cas, supprimez le fichier .def de la génération.

Lorsque vous créez une application, l’éditeur de liens recherche pour une fonction de point d’entrée à appeler pour démarrer votre code. Il s’agit de la fonction est appelée une fois que l’application est chargée et le runtime est initialisé. Vous devez fournir une fonction de point d’entrée pour une application ou votre application ne peut pas s’exécuter. Un point d’entrée est facultatif pour une DLL. Par défaut, l’éditeur de liens recherche pour une fonction de point d’entrée qui a plusieurs noms spécifiques et les signatures, telle que `int main(int, char**)`. Vous pouvez spécifier un autre nom de la fonction en tant que l’entrée de point à l’aide de l’option de l’éditeur de liens/Entry.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur LNK1561 :

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```