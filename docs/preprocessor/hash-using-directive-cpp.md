---
title: '#using, Directive (C + c++ / CLI)'
ms.date: 10/18/2018
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
ms.openlocfilehash: ddae6137e94e10f5701e1e7d0f8f7a7514b18662
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034259"
---
# <a name="using-directive-ccli"></a>#using, Directive (C + c++ / CLI)

Importe des métadonnées dans un programme compilé avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="syntax"></a>Syntaxe

```
#using file [as_friend]
```

### <a name="parameters"></a>Paramètres

*fichier*<br/>
MSIL .dll, .exe, .netmodule ou .obj. Par exemple :

`#using <MyComponent.dll>`

*as_friend*<br/>
Spécifie que tous les types de *fichier* sont accessibles. Pour plus d’informations, consultez [assemblys Friend (C++)](../dotnet/friend-assemblies-cpp.md).

## <a name="remarks"></a>Notes

*fichier* peut être un fichier de langage intermédiaire (MSIL) de Microsoft que vous importez pour ses données et les constructions managées. Si un fichier .dll contient un manifeste d’assembly, puis tous les fichiers .dll référencés dans le manifeste sont importées et que l’assembly que vous générez répertorie *fichier* dans les métadonnées comme une référence d’assembly.

Si *fichier* ne contient pas d’assembly (si *fichier* est un module) et si vous ne souhaitez pas utiliser les informations de type à partir du module dans l’application (assembly) actuelle, vous avez la possibilité d’indiquer simplement que le module fait partie de l’assembly ; Utilisez [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Les types du module sont ensuite accessibles à toute application qui a référencé l'assembly.

Une alternative à utiliser **#using** est la [/FU](../build/reference/fu-name-forced-hash-using-file.md) option du compilateur.

assemblys .exe passés à **#using** doit être compilée à l’aide d’un des compilateurs .NET Visual Studio (Visual Basic ou Visual c#, par exemple).  Toute tentative d'importation des métadonnées à partir d'un assembly .exe compilé avec `/clr` provoque une exception de chargement du fichier.

> [!NOTE]
> Un composant qui est référencé avec **#using** peut être exécuté avec une version différente du fichier importé au moment de la compilation, à l’origine d’une application cliente à donner des résultats inattendus.

Pour que le compilateur reconnaisse un type dans un assembly (pas un module), il doit être forcé à résoudre le type, vous pouvez faire, par exemple, en définissant une instance du type. Autres façons de résoudre les noms de type dans un assembly pour le compilateur, par exemple, si vous héritez d’un type dans un assembly, le nom de type sera deviennent connu du compilateur.

Lors de l’importation de métadonnées générées à partir de code source utilisé [__declspec (thread)](../cpp/thread.md), la sémantique de thread n’est pas conservée dans les métadonnées. Par exemple, une variable déclarée avec **__declspec (thread)**, compilée dans un programme qui est la build pour le common language runtime du .NET Framework et puis importée via **#using**, n’aura plus **__declspec (thread)** sémantique sur la variable.

Tous les types (natifs et managés) dans un fichier référencé par importés **#using** sont disponibles, mais le compilateur traite les types natifs en tant que déclarations et non les définitions.

mscorlib.dll est automatiquement référencé lors de la compilation avec `/clr`.

La variable d’environnement LIBPATH spécifie les répertoires qui seront recherchés lors le compilateur tente de résoudre les noms de fichiers passées à **#using**.

Le compilateur recherche des références dans le chemin d’accès suivant :

- Un chemin d’accès spécifié dans le **#using** instruction.

- Le répertoire actif.

- Répertoire système du .NET Framework.

- Répertoires ajoutés avec la [/AI](../build/reference/ai-specify-metadata-directories.md) option du compilateur.

- Répertoires sur la variable d'environnement LIBPATH.

## <a name="example"></a>Exemple

Si vous générez un assembly (C) et référencez un assembly (B) qui lui-même référence un autre assembly (A), vous ne devrez pas référencer explicitement l'assembly A sauf si vous utilisez explicitement un des types de A dans C.

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

## <a name="example"></a>Exemple

```cpp
// using_assembly_B.cpp
// compile with: /clr /LD
#using "using_assembly_A.dll"
public ref class B {
public:
   void Test(A a) {}
   void Test() {}
};
```

## <a name="example"></a>Exemple

Dans l'exemple suivant, aucune erreur du compilateur ne se produit pour absence de référencement d'using_assembly_A.dll, car le programme n'utilise aucun des types définis dans using_assembly_A.cpp.

```cpp
// using_assembly_C.cpp
// compile with: /clr
#using "using_assembly_B.dll"
int main() {
   B b;
   b.Test();
}
```

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)