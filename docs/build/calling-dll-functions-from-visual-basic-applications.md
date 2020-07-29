---
title: Appel de fonctions de la DLL à partir d'applications Visual Basic
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
ms.openlocfilehash: 8d792dac45d69a0857bda551d1f3c03fc3d03d1c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229881"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Appel de fonctions de la DLL à partir d'applications Visual Basic

Pour les applications Visual Basic (ou dans d’autres langages tels que Pascal ou Fortran) pour appeler des fonctions dans une DLL C/C++, les fonctions doivent être exportées à l’aide de la Convention d’appel appropriée sans aucune décoration de nom effectuée par le compilateur

**`__stdcall`** crée la Convention d’appel appropriée pour la fonction (la fonction appelée nettoie la pile et les paramètres sont passés de droite à gauche), mais décore le nom de la fonction différemment. Ainsi, lorsque **`__declspec(dllexport)`** est utilisé sur une fonction exportée dans une dll, le nom décoré est exporté.

La **`__stdcall`** décoration de nom préfixe le nom du symbole avec un trait de soulignement ( **\_** ) et ajoute le symbole avec un caractère arobase ( **\@** ) suivi du nombre d’octets dans la liste d’arguments (espace de pile requis). En conséquence, la fonction est déclarée comme suit :

```C
int __stdcall func (int a, double b)
```

est décoré comme `_func@12` dans la sortie.

La Convention d’appel C ( **`__cdecl`** ) décore le nom en `_func` .

Pour récupérer le nom décoré, utilisez [/Map](reference/map-generate-mapfile.md). L’utilisation de **`__declspec(dllexport)`** effectue les opérations suivantes :

- Si la fonction est exportée avec la Convention d’appel C ( **`__cdecl`** ), elle supprime le trait de soulignement de début ( **\_** ) lorsque le nom est exporté.

- Si la fonction en cours d’exportation n’utilise pas la Convention d’appel C (par exemple, **`__stdcall`** ), elle exporte le nom décoré.

Étant donné qu’il n’existe aucun moyen de remplacer l’emplacement où le nettoyage de la pile se produit, vous devez utiliser **`__stdcall`** . Pour dédécorerr des noms avec **`__stdcall`** , vous devez les spécifier à l’aide d’alias dans la section EXports du fichier. def. Cette procédure est illustrée ci-dessous pour la déclaration de fonction suivante :

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

Dans le. Fichier DEF :

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

Pour que les dll soient appelées par des programmes écrits en Visual Basic, la technique d’alias présentée dans cette rubrique est nécessaire dans le fichier. def. Si l’alias est effectué dans le programme Visual Basic, l’utilisation d’alias dans le fichier. def n’est pas nécessaire. Vous pouvez le faire dans le programme Visual Basic en ajoutant une clause alias à l’instruction [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) .

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Exportation à partir d'une DLL](exporting-from-a-dll.md)

- [Exportation à partir d’une DLL à l’aide de. Fichiers DEF](exporting-from-a-dll-using-def-files.md)

- [Exportation à partir d’une DLL à l’aide de __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportation de fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Noms décorés](reference/decorated-names.md)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
