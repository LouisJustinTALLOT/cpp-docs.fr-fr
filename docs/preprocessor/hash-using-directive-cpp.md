---
title: '#directive using (C++/CLI)'
ms.date: 08/29/2019
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
ms.openlocfilehash: 5dae5c277055157aef5451c19ee020fbbd2aaccb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220199"
---
# <a name="using-directive-ccli"></a>#using directive (C++/CLI)

Importe des métadonnées dans un programme compilé avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="syntax"></a>Syntaxe

> **#using** *fichier* [**as_friend**]

### <a name="parameters"></a>Paramètres

*txt*\
MSIL .dll, .exe, .netmodule ou .obj. Par exemple,

`#using <MyComponent.dll>`

**as_friend**\
Spécifie que tous les types dans le *fichier* sont accessibles. Pour plus d’informations, consultez [assemblys friendC++()](../dotnet/friend-assemblies-cpp.md).

## <a name="remarks"></a>Notes

le *fichier* peut être un fichier MSIL (Microsoft Intermediate Language) que vous importez pour ses données managées et les constructions managées. Si un fichier. dll contient un manifeste d’assembly, toutes les fichiers. dll référencés dans le manifeste sont importés et l’assembly que vous générez répertorie les *fichiers* dans les métadonnées sous la forme d’une référence d’assembly.

Si le *fichier* ne contient pas d’assembly (si le *fichier* est un module) et si vous n’envisagez pas d’utiliser les informations de type du module dans l’application (Assembly) actuelle, vous avez la possibilité de simplement indiquer que le module fait partie de l’assembly. Utilisez [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Les types du module sont ensuite accessibles à toute application qui a référencé l'assembly.

Une alternative à l’utilisation de **#using** est l’option de compilateur [/Fu](../build/reference/fu-name-forced-hash-using-file.md) .

les assemblys. exe passés à **#using** doivent être compilés à l’aide de l’un des compilateurs Visual Studio .net ( C#Visual Basic ou visuel, par exemple).  Toute tentative d'importation des métadonnées à partir d'un assembly .exe compilé avec `/clr` provoque une exception de chargement du fichier.

> [!NOTE]
> Un composant référencé avec **#using** peut être exécuté avec une version différente du fichier importé au moment de la compilation, ce qui entraîne une application cliente qui donne des résultats inattendus.

Pour que le compilateur reconnaisse un type dans un assembly (et non un module), il doit être forcé de résoudre le type. Vous pouvez le forcer, par exemple, en définissant une instance du type. Il existe d’autres façons de résoudre les noms de types dans un assembly pour le compilateur. Par exemple, si vous héritez d’un type dans un assembly, le nom de type devient connu du compilateur.

Lors de l’importation de métadonnées générées à partir du code source qui utilisait [_ _ declspec (thread)](../cpp/thread.md), la sémantique des threads n’est pas conservée dans les métadonnées. Par exemple, une variable déclarée avec **_ _ declspec (thread)** , compilée dans un programme généré pour la .NET Framework Common Language Runtime, puis importée via **#using**, n’aura pas de sémantique **_ _ declspec (thread)** sur la variable.

Tous les types importés (managés et natifs) dans un fichier référencé par **#using** sont disponibles, mais le compilateur traite les types natifs comme des déclarations, et non des définitions.

mscorlib.dll est automatiquement référencé lors de la compilation avec `/clr`.

La variable d’environnement LIBPATH spécifie les répertoires à rechercher lorsque le compilateur résout les noms de fichiers passés à **#using**.

Le compilateur recherche des références le long du chemin suivant:

- Chemin d’accès spécifié dans l’instruction **#using** .

- Répertoire actif.

- Répertoire système du .NET Framework.

- Répertoires ajoutés avec l’option du compilateur [/ai](../build/reference/ai-specify-metadata-directories.md) .

- Répertoires sur la variable d'environnement LIBPATH.

## <a name="example"></a>Exemples

Si vous générez un assembly (C) et que vous référencez un assembly (B) qui lui-même fait référence à un autre assembly (A), vous n’aurez pas à référencer explicitement un assembly A, sauf si vous utilisez explicitement l’un des types de A dans C.

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

Dans l’exemple suivant, il n’y a pas d’erreur de compilateur pour ne pas référencer *using_assembly_A. dll*, car le programme n’utilise pas les types définis dans *using_assembly_A. cpp*.

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
