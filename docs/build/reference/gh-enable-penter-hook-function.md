---
title: /Gh (Activer la fonction de raccordement _penter)
description: Décrit l’option du compilateur/GH pour appeler la fonction _penter fournie.
ms.date: 07/06/2020
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: 96597d964e6a341aa25f4d52d34974949eb7b096
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058579"
---
# <a name="gh-enable-_penter-hook-function"></a>/Gh (Activer la fonction de raccordement _penter)

Provoque un appel à la `_penter` fonction au début de chaque méthode ou fonction.

## <a name="syntax"></a>Syntaxe

> **`/Gh`**

## <a name="remarks"></a>Notes

La `_penter` fonction ne fait partie d’aucune bibliothèque. C’est à vous de fournir une définition pour `_penter` .

À moins que vous n’envisagez d’appeler explicitement `_penter` , vous n’avez pas besoin de fournir un prototype. La fonction doit transmettre le contenu de tous les registres sur l’entrée et dépiler le contenu non modifié à la sortie. Il doit apparaître comme s’il avait le prototype suivant :

```cpp
void __declspec(naked) __cdecl _penter( void );
```

Cette déclaration n’est pas disponible pour les projets 64 bits.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Entrez l’option de compilateur dans la zone **options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Exemple

Le code suivant, lorsqu’il est compilé avec **/GH**, montre comment `_penter` est appelé deux fois ; une fois lors de l’entrée de la fonction `main` et une fois lors de l’entrée de la fonction `x` . L’exemple se compose de deux fichiers sources, que vous compilez séparément.

```cpp
// local_penter.cpp
// compile with: cl /EHsc /c local_penter.cpp
// processor: x86
#include <stdio.h>

extern "C" void __declspec(naked) __cdecl _penter( void ) {
   _asm {
      push eax
      push ebx
      push ecx
      push edx
      push ebp
      push edi
      push esi
    }

   printf_s("\nIn a function!");

   _asm {
      pop esi
      pop edi
      pop ebp
      pop edx
      pop ecx
      pop ebx
      pop eax
      ret
    }
}
```

```cpp
// Gh_compiler_option.cpp
// compile with: cl /EHsc /Gh Gh_compiler_option.cpp local_penter.obj
// processor: x86
#include <stdio.h>

void x() {}

int main() {
   x();
}
```

Quand elle est exécutée, la `_penter` fonction locale est appelée à l’entrée `main` et `x` :

```Output

In a function!
In a function!
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[`/GH`(Activer la fonction de raccordement _pexit)](gh-enable-pexit-hook-function.md)
