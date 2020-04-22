---
title: /Gh (Activer la fonction de raccordement _penter)
ms.date: 11/04/2016
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: 87815b5f0e0450b84acbe3c35b7ef4f31216ec72
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749295"
---
# <a name="gh-enable-_penter-hook-function"></a>/Gh (Activer la fonction de raccordement _penter)

Provoque un appel `_penter` à la fonction au début de chaque méthode ou fonction.

## <a name="syntax"></a>Syntaxe

```
/Gh
```

## <a name="remarks"></a>Notes

La `_penter` fonction ne fait partie d’aucune bibliothèque et c’est à vous de fournir une définition pour `_penter`.

Sauf si vous `_penter`avez l’intention d’appeler explicitement , vous n’avez pas besoin de fournir un prototype. La fonction doit apparaître comme si elle avait le prototype suivant, et il doit pousser le contenu de tous les registres à l’entrée et pop le contenu inchangé à la sortie:

```cpp
void __declspec(naked) __cdecl _penter( void );
```

Cette déclaration n’est pas disponible pour les projets 64 bits.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Exemple

Le code suivant, lorsqu’il est `_penter` compilé avec **/Gh**, montre comment est appelé deux fois; une fois `main` lors de l’entrée de la fonction et une fois lors de l’entrée de la fonction `x`.

```cpp
// Gh_compiler_option.cpp
// compile with: /Gh
// processor: x86
#include <stdio.h>
void x() {}

int main() {
   x();
}

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

```Output
In a function!
In a function!
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
