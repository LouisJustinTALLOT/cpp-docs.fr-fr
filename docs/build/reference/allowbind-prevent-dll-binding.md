---
title: /ALLOWBIND (Éviter la liaison DLL)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
ms.openlocfilehash: bd9976e434441d2480386ee6fa3d0315fd8d2ef5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295147"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Éviter la liaison DLL)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Notes

/ALLOWBIND:NO définit un bit dans l'en-tête d'une DLL, qui indique à Bind.exe que l'image n'est pas autorisée à être liée. Vous ne voulez peut-être pas qu’une DLL soit liée si elle a été signée numériquement (la liaison invalide la signature).

Vous pouvez modifier une DLL existante pour la fonctionnalité /ALLOWBIND à le [/ALLOWBIND](allowbind.md) option de l’utilitaire EDITBIN.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Développez **propriétés de Configuration**, **l’éditeur de liens**, puis sélectionnez **ligne de commande**.

1. Entrez `/ALLOWBIND:NO` dans **des Options supplémentaires**.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[BindImage (fonction)](/windows/desktop/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx (fonction)](/windows/desktop/api/imagehlp/nf-imagehlp-bindimageex)
