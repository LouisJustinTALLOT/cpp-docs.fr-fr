---
title: /Zc:inline (supprimer des éléments COMDAT non référencés)
ms.date: 09/05/2019
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
ms.openlocfilehash: 42791b2e337fb9a9724a165145e757152b8d679d
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518242"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (supprimer des éléments COMDAT non référencés)

Supprime les données non référencées ou les fonctions qui sont des COMDAT, ou qui ont uniquement une liaison interne. Sous **/Zc : Inline**, le compilateur spécifie que les unités de traduction avec des données ou des fonctions inline doivent également inclure leurs définitions.

## <a name="syntax"></a>Syntaxe

> **/Zc:inline**[ **-** ]

## <a name="remarks"></a>Notes

Quand **/Zc : Inline** est spécifié, le compilateur n’émet pas d’informations de symbole pour les fonctions ou les données COMDAT non référencées. Ou, pour les données ou les fonctions qui ont uniquement une liaison interne. Cette optimisation simplifie une partie du travail de l’éditeur de liens dans les versions release, ou lorsque vous spécifiez l’option de l’éditeur de liens [/OPT : Ref](opt-optimizations.md) . Cette optimisation du compilateur peut réduire considérablement la taille du fichier. objet améliorer les vitesses de l’éditeur de liens. L’option de compilateur n’est pas activée lorsque vous désactivez les optimisations ([/OD](od-disable-debug.md)). Ou, lorsque vous spécifiez [/GL (optimisation de l’ensemble du programme)](gl-whole-program-optimization.md).

Par défaut, cette option est désactivée ( **/Zc : Inline-** ) dans les générations à partir de la ligne de commande. L’option [/permissive-](permissive-standards-conformance.md) n’active pas **/Zc : Inline**. Dans les projets MSBuild, l’option est définie par **les propriétés de configuration** > **langage** **C/C++**  >  > supprimer le code et la propriété de données non **référencés** , qui est défini sur **Oui** par défaut.

Si **/Zc : Inline** est spécifié, le compilateur applique la condition c++ 11 stipulant que toutes les fonctions déclarées `inline` doivent avoir une définition disponible dans la même unité de traduction si elles sont utilisées. Lorsque l’option n’est pas spécifiée, le compilateur Microsoft autorise le code non conforme qui appelle les fonctions déclarées `inline` même si aucune définition n’est visible. Pour plus d'informations, voir la norme C++11, section 3.2 et section 7.1.2. Cette option du compilateur a été introduite pour la première fois dans Visual Studio 2013 Update 2.

Pour utiliser l’option **/Zc : Inline** , mettez à jour le code non conforme.

Cet exemple montre comment l’utilisation non conforme d’une déclaration de fonction inline sans définition est toujours compilée et établit un lien lorsque la valeur par défaut de l’option **/Zc : Inline-** est utilisée :

```cpp
// example.h
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#pragma once

class Example {
public:
   inline void inline_call(); // declared but not defined inline
   void normal_call();
   Example() {};
};
```

```cpp
// example.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include <stdio.h>
#include "example.h"

void Example::inline_call() {
   printf("inline_call was called.\n");
}

void Example::normal_call() {
   printf("normal_call was called.\n");
   inline_call(); // with /Zc:inline-, inline_call forced into .obj file
}
```

```cpp
// zcinline.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include "example.h"

int main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

Quand **/Zc : Inline** est activé, le même code provoque une erreur [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) , car le compilateur n’émet pas de corps de code non inclus pour `Example::inline_call` dans example. obj. Cela amène l’appel non inline dans `main` à faire référence à un symbole externe non défini.

Pour résoudre cette erreur, vous pouvez supprimer le mot clé `inline` de la déclaration de `Example::inline_call`, placer la définition de `Example::inline_call` dans le fichier d'en-tête ou placer l'implémentation de `Example` dans main.cpp. Dans l'exemple suivant, la définition est placée dans le fichier d'en-tête, où elle est visible pour tout appelant qui inclut l'en-tête.

```cpp
// example2.h
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#pragma once
#include <stdio.h>

class Example2 {
public:
   inline void inline_call() {
      printf("inline_call was called.\n");
   }
   void normal_call();
   Example2() {};
};
```

```cpp
// example2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

void Example2::normal_call() {
   printf("normal_call was called.\n");
   inline_call();
}
```

```cpp
// zcinline2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

int main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez les **Propriétés de configuration** > page de propriétés **langue** **CC++ /**  > .

1. Modifiez la propriété **supprimer le code et les données non référencés** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)<br/>
