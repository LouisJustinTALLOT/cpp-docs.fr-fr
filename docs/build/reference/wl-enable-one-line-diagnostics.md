---
title: /WL (Activer un diagnostic de ligne)
ms.date: 11/04/2016
f1_keywords:
- /wl
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
ms.openlocfilehash: c0d5110615f66dcf4f7dc170d89ee58c2e8fa5cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316533"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Activer un diagnostic de ligne)

Ajoute des informations supplémentaires à un message d’erreur ou avertissement.

## <a name="syntax"></a>Syntaxe

```
/WL
```

## <a name="remarks"></a>Notes

Messages d’erreur et Avertissement du compilateur C++ peuvent être suivies d’autres informations qui s’affiche, par défaut, sur une nouvelle ligne. Lorsque vous compilez à partir de la ligne de commande, la ligne d’informations supplémentaire peut être ajoutée pour le message d’erreur ou avertissement. Cela peut être souhaitable si vous capturez votre sortie de génération dans un fichier journal et ensuite traitez ce journal pour rechercher toutes les erreurs et avertissements. Un point-virgule pour séparer le message d’erreur ou avertissement de la ligne supplémentaire.

Pas tous les messages d’erreur et avertissement ont une ligne supplémentaire d’informations. Le code suivant génère une erreur qui a une ligne supplémentaire d’informations ; Il vous permet de tester l’effet lorsque vous utilisez **/WL**.

```
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
