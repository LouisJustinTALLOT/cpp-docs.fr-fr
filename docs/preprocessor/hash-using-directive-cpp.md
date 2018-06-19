---
title: '#using, Directive (C + c++ / CLR) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
dev_langs:
- C++
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 053c425a6bb8dcab0dc5cb94db1537f0fff3d9f8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840734"
---
# <a name="using-directive-cclr"></a>#using, Directive (C + c++ / CLR)
Importe des métadonnées dans un programme compilé avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#using file [as_friend]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `file`  
 MSIL .dll, .exe, .netmodule ou .obj. Par exemple :  
  
 `#using <MyComponent.dll>`  
  
 as_friend  
 Spécifie que tous les types dans `file` sont accessibles.  Pour plus d’informations, consultez [assemblys Friend (C++)](../dotnet/friend-assemblies-cpp.md).  
  
## <a name="remarks"></a>Notes  
 `file` peut être un fichier MSIL (Microsoft Intermediate Language) que vous importez pour ses données et constructions managées. Si un fichier .dll contient un manifeste d’assembly, puis toutes les DLL référencé dans le manifeste sont importés et répertorie l’assembly que vous générez *fichier* dans les métadonnées comme une référence d’assembly.  
  
 Si `file` ne contient pas d’assembly (si `file` est un module) et si vous n’avez pas l’intention d’utiliser les informations de type à partir du module de l’application (assembly) actuelle, vous avez la possibilité d’indiquer simplement que le module fait partie de l’assembly ; utilisez [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Les types du module sont ensuite accessibles à toute application qui a référencé l'assembly.  
  
 Une alternative à utiliser `#using` est la [/FU](../build/reference/fu-name-forced-hash-using-file.md) option du compilateur.  
  
 les assemblys .exe passés à `#using` doit être compilée à l’aide d’un des compilateurs .NET de Visual Studio (Visual Basic ou Visual c#, par exemple).  Une tentative d’importation de métadonnées à partir d’un assembly .exe compilé avec **/CLR** entraîne une exception de chargement du fichier.  
  
> [!NOTE]
>  Un composant référencé avec `#using` peut être exécuté avec une version différente du fichier importé au moment de la compilation, ce qui provoque des résultats inattendus d'une application cliente.  
  
 Pour que le compilateur de reconnaître un type dans un assembly (pas un module), il doit être forcé à résoudre le type, vous pouvez faire, par exemple, en définissant une instance du type. Autres façons de résoudre les noms de types dans un assembly pour le compilateur, par exemple, si vous héritez d’un type dans un assembly, le nom du type sera deviennent connu du compilateur.  
  
 Lors de l’importation de métadonnées générées à partir de code source utilisé [__declspec (thread)](../cpp/thread.md), la sémantique de thread n’est pas conservée dans les métadonnées. Par exemple, une variable déclarée avec **__declspec (thread)**, compilée dans un programme qui est générée pour le common language runtime du .NET Framework, puis importé `#using`, n’aura plus **__declspec () thread)** une sémantique de la variable.  
  
 Tous les types importés (managés et natifs) dans un fichier référencé par `#using` sont disponibles, mais le compilateur traite les types natifs comme des déclarations, et non comme des définitions.  
  
 mscorlib.dll est automatiquement référencé lors de la compilation avec **/CLR**.  
  
 La variable d'environnement LIBPATH spécifie les répertoires qui font l'objet d'une recherche lorsque le compilateur tente de résoudre les noms de fichier passés à `#using`.  
  
 Le compilateur recherche des références dans le chemin d'accès suivant :  
  
-   Chemin d'accès spécifié dans l'instruction `#using`.  
  
-   Le répertoire actif.  
  
-   Répertoire système du .NET Framework.  
  
-   Répertoires ajoutés avec la [/AI](../build/reference/ai-specify-metadata-directories.md) option du compilateur.  
  
-   Répertoires sur la variable d'environnement LIBPATH.  
  
## <a name="example"></a>Exemple  
 Si vous générez un assembly (C) et référencez un assembly (B) qui lui-même référence un autre assembly (A), vous ne devrez pas référencer explicitement l'assembly A sauf si vous utilisez explicitement un des types de A dans C.  
  
```  
// using_assembly_A.cpp  
// compile with: /clr /LD  
public ref class A {};  
```  
  
## <a name="example"></a>Exemple  
  
```  
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
  
```  
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