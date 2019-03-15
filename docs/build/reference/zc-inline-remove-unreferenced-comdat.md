---
title: /Zc:inline (supprimer des éléments COMDAT non référencés)
ms.date: 03/01/2018
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
ms.openlocfilehash: 06bdb3300aae88c6c4c8f7e66af658f47548ac5a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820518"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (supprimer des éléments COMDAT non référencés)

Supprime les données ou fonctions non référencées qui sont des COMDAT ou qui possèdent uniquement une liaison interne. Lorsque **/Zc : inline** est spécifié, le compilateur exige que les unités de traduction qui utilisent des données inline ou des fonctions inline incluent également les définitions pour les données ou les fonctions.

## <a name="syntax"></a>Syntaxe

> **/Zc:inline**[**-**]

## <a name="remarks"></a>Notes

Lorsque **/Zc : inline** est spécifié, le compilateur n’émet pas d’informations de symboles pour les fonctions COMDAT non référencées ou des données, ou pour les fonctions ou des données qui possèdent uniquement une liaison interne. Cette optimisation simplifie une partie du travail effectué par l’éditeur de liens dans les versions release ou quand l’option de l’éditeur de liens [/OPT : REF](opt-optimizations.md) est spécifié. Quand le compilateur effectue cette optimisation, il peut réduire considérablement la taille du fichier .obj et accélérer le fonctionnement de l'éditeur de liens. Cette option du compilateur n’est pas activée quand les optimisations sont désactivées ([/Od](od-disable-debug.md)) ou lorsque [/GL (Whole Program Optimization)](gl-whole-program-optimization.md) est spécifié.

Par défaut, cette option est désactivée (**/Zc:inline-**). Le [/ permissive-](permissive-standards-conformance.md) option n’active pas **/Zc : inline**.

Si **/Zc : inline** est spécifié, le compilateur applique le C ++ 11 fait que toutes les fonctions déclarées `inline` doit avoir une définition disponible dans la même unité de traduction si elles sont utilisées. Lorsque l’option n’est pas spécifiée, le compilateur Microsoft permet au code non conforme qui appelle des fonctions déclarées `inline` même si aucune définition n’est visible. Pour plus d'informations, voir la norme C++11, section 3.2 et section 7.1.2. Cette option du compilateur a été introduite pour la première fois dans Visual Studio 2013 Update 2.

Pour utiliser le **/Zc : inline** option, la mise à jour d’un code non conforme.

Cet exemple montre comment l’utilisation non conforme d’une déclaration de fonction inline sans définition compile et lie lorsque la valeur par défaut **/Zc:inline-** option est utilisée :

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

void main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

Lorsque **/Zc : inline** est activé, le même code génère un [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) erreur, car le compilateur n’émet pas d’un corps de code non inline pour `Example::inline_call` dans example.obj. Par conséquent, l'appel non inline dans `main` référence un symbole externe non défini.

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

void main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **langage** page de propriétés.

1. Modifier le **supprimer les données et code non référencé** propriété, puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)<br/>
