---
title: Erreur des outils Éditeur de liens LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: b397ef8e551f8cd6179392541e35183a5850454f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357750"
---
# <a name="linker-tools-error-lnk1561"></a>Erreur des outils Éditeur de liens LNK1561

le point d’entrée doit être défini

Le lieneur n’a pas trouvé de *point d’entrée,* la fonction initiale à appeler dans votre exécutable. Par défaut, le linker `main` `wmain` recherche une application ou `WinMain` `wWinMain` une fonction pour une `DllMain` application de console, un ou une fonction pour une application Windows, ou pour un DLL qui nécessite une initialisation. Vous pouvez spécifier une autre fonction en utilisant l’option de liaison [/ENTRY.](../../build/reference/entry-entry-point-symbol.md)

Cette erreur peut avoir plusieurs causes :

- Il se peut que vous n’ayez pas inclus le fichier qui définit votre point d’entrée dans la liste des fichiers à lier. Vérifiez que le fichier qui contient la fonction de point d’entrée est lié à votre application.
- Vous avez peut-être défini le point d’entrée à l’aide de la mauvaise signature de fonction; par exemple, vous avez peut-être mal orthographié ou utilisé le mauvais boîtier pour le nom de fonction, ou spécifié le type de retour ou les types de paramètres incorrectement.
- Vous n’avez peut-être pas spécifié l’option [/DLL](../../build/reference/dll-build-a-dll.md) lors de la construction d’un DLL.
- Vous avez peut-être mal précisé le nom de la fonction de point d’entrée lorsque vous avez utilisé l’option de liaison [/ENTRY.](../../build/reference/entry-entry-point-symbol.md)
- Si vous utilisez l’outil [LIB](../../build/reference/lib-reference.md) pour construire un DLL, vous avez peut-être spécifié un fichier .def. Si c’est le cas, retirez le fichier .def de la construction.

Lors de la construction d’une application, le linker recherche une fonction de point d’entrée pour appeler pour démarrer votre code. C’est la fonction qui s’appelle après le chargement de l’application et l’heure d’exécution est parasécé. Vous devez fournir une fonction de point d’entrée pour une application, ou votre application ne peut pas s’exécuter. Un point d’entrée est facultatif pour un DLL. Par défaut, le linker recherche une fonction de point d’entrée qui `int main(int, char**)`a l’un de plusieurs noms et signatures spécifiques, tels que . Vous pouvez spécifier un autre nom de fonction comme point d’entrée en utilisant l’option de liaison /ENTRY.

## <a name="example"></a>Exemple

L’échantillon suivant génère LNK1561 :

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
