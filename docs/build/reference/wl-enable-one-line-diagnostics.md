---
description: En savoir plus sur:/WL (activer les diagnostics One-Line)
title: /WL (Activer un diagnostic de ligne)
ms.date: 11/04/2016
f1_keywords:
- /wl
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
ms.openlocfilehash: 032f2c41558c1475be5673d4a69de9ff9b09f323
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258861"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Activer un diagnostic de ligne)

Ajoute des informations supplémentaires à un message d’erreur ou d’avertissement.

## <a name="syntax"></a>Syntaxe

```
/WL
```

## <a name="remarks"></a>Notes

Les messages d’erreur et d’avertissement du compilateur C++ peuvent être suivis par des informations supplémentaires qui apparaissent, par défaut, sur une nouvelle ligne. Quand vous compilez à partir de la ligne de commande, la ligne d’informations supplémentaire peut être ajoutée au message d’erreur ou d’avertissement. Cela peut être souhaitable si vous capturez votre sortie de génération dans un fichier journal, puis traitez ce journal pour rechercher toutes les erreurs et tous les avertissements. Un point-virgule sépare le message d’erreur ou d’avertissement de la ligne supplémentaire.

Tous les messages d’erreur et d’avertissement n’ont pas de ligne d’informations supplémentaire. Le code suivant génère une erreur qui contient une ligne d’informations supplémentaire ; elle vous permet de tester l’effet lorsque vous utilisez **/WL**.

```cpp
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
