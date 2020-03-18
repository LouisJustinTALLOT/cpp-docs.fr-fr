---
title: /GR (Activer les informations de type au moment de l'exécution)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: ee1398b2f9ee78c62fb84aa591e77708cd0d9d83
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439585"
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Activer les informations de type au moment de l'exécution)

Ajoute du code pour vérifier les types d’objets au moment de l’exécution.

## <a name="syntax"></a>Syntaxe

```
/GR[-]
```

## <a name="remarks"></a>Notes

Lorsque **/GR** est activé, le compilateur définit la macro de préprocesseur `_CPPRTTI`. Par défaut, **/GR** est activé. **/GR-** désactive les informations de type au moment de l’exécution.

Utilisez **/GR** si le compilateur ne peut pas résoudre de manière statique un type d’objet dans votre code. Vous avez généralement besoin de l’option **/GR** lorsque votre code utilise [dynamic_cast opérateur](../../cpp/dynamic-cast-operator.md) ou [typeid](../../cpp/typeid-operator.md). Toutefois, **/GR** augmente la taille des sections. rdata de votre image. Si votre code n’utilise pas **dynamic_cast** ou **typeid**, **/GR-** peut produire une image plus petite.

Pour plus d’informations sur la vérification des types au moment de l’exécution, consultez [informations de type au moment](../../cpp/run-time-type-information.md) de l’exécution dans la référence du  *C++ langage*.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **langue** .

1. Modifiez la propriété **activer les informations de type au moment de l’exécution** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
