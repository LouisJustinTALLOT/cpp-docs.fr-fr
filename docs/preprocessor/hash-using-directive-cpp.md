---
description: 'En savoir plus sur : directive #using (C++/CLI)'
title: '#using, directive (C++/CLI)'
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
ms.openlocfilehash: 5903e3b5af4cd6ee40e0b087d52d1bd0115b1c6f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167524"
---
# <a name="using-directive-ccli"></a>#using, directive (C++/CLI)

Importe des métadonnées dans un programme compilé avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="syntax"></a>Syntaxe

> **`#using`***fichier* [ **`as_friend`** ]

### <a name="parameters"></a>Paramètres

*txt*\
Fichier Microsoft Intermediate Language (MSIL) *`.dll`* , *`.exe`* , *`.netmodule`* ou *`.obj`* . Par exemple :

`#using <MyComponent.dll>`

**`as_friend`**\
Spécifie que tous les types dans le *fichier* sont accessibles. Pour plus d’informations, consultez [assemblys friend (C++)](../dotnet/friend-assemblies-cpp.md).

## <a name="remarks"></a>Notes

le *fichier* peut être un fichier MSIL (Microsoft Intermediate Language) que vous importez pour ses données managées et les constructions managées. Si une DLL contient un manifeste d’assembly, toutes les dll référencées dans le manifeste sont importées. L’assembly que vous générez répertorie les *fichiers* dans les métadonnées en tant que référence d’assembly.

Par exemple, le *fichier* ne contient pas d’assembly (le *fichier* est un module) et vous n’avez pas l’intention d’utiliser les informations de type du module dans l’application (Assembly) actuelle. Vous pouvez indiquer que le module fait partie de l’assembly à l’aide de [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Les types du module sont ensuite accessibles à toute application qui a référencé l'assembly.

Une alternative à utiliser **`#using`** est l’option de compilateur [/Fu](../build/reference/fu-name-forced-hash-using-file.md) .

les assemblys. exe passés à **`#using`** doivent être compilés à l’aide de l’un des compilateurs Visual Studio .net (Visual Basic ou Visual C#, par exemple).  Toute tentative d’importation de métadonnées à partir d’un assembly. exe compilé avec **`/clr`** entraîne une exception de chargement de fichier.

> [!NOTE]
> Un composant référencé avec **`#using`** peut être exécuté avec une version différente du fichier importé au moment de la compilation, ce qui entraîne une application cliente qui donne des résultats inattendus.

Pour que le compilateur reconnaisse un type dans un assembly (et non un module), il doit être forcé de résoudre le type. Vous pouvez le forcer, par exemple, en définissant une instance du type. Il existe d’autres façons de résoudre les noms de types dans un assembly pour le compilateur. Par exemple, si vous héritez d’un type dans un assembly, le nom de type devient connu du compilateur.

Lors de l’importation de métadonnées générées à partir du code source utilisé [`__declspec(thread)`](../cpp/thread.md) , la sémantique des threads n’est pas conservée dans les métadonnées. Par exemple, une variable déclarée avec **`__declspec(thread)`** , compilée dans un programme généré pour la .NET Framework Common Language Runtime, puis importée via **`#using`** , n’aura pas **`__declspec(thread)`** de sémantique sur la variable.

Tous les types importés (managés et natifs) dans un fichier référencé par **`#using`** sont disponibles, mais le compilateur traite les types natifs comme des déclarations, et non des définitions.

mscorlib.dll est automatiquement référencé lors de la compilation avec **`/clr`** .

La variable d’environnement LIBPATH spécifie les répertoires à rechercher lorsque le compilateur résout les noms de fichiers passés à **`#using`** .

Le compilateur recherche des références le long du chemin suivant :

- Chemin d’accès spécifié dans l' **`#using`** instruction.

- Le répertoire actif.

- Répertoire système du .NET Framework.

- Répertoires ajoutés avec l' [`/AI`](../build/reference/ai-specify-metadata-directories.md) option du compilateur.

- Répertoires sur la variable d'environnement LIBPATH.

## <a name="examples"></a>Exemples

Vous pouvez générer un assembly qui fait référence à un deuxième assembly qui lui-même fait référence à un troisième assembly. Vous devez uniquement référencer explicitement le troisième assembly du premier assembly si vous utilisez explicitement l’un de ses types.

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

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

Dans l’exemple suivant, le compilateur ne signale pas une erreur de référencement des *using_assembly_A.dll*, car le programme n’utilise pas les types définis dans *using_assembly_A. cpp*.

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
