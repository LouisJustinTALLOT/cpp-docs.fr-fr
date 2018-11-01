---
title: /ASSEMBLYDEBUG (Ajouter DebuggableAttribute)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AssemblyDebug
- /ASSEMBLYDEBUG
helpviewer_keywords:
- /ASSEMBLYDEBUG linker option
- -ASSEMBLYDEBUG linker option
- ASSEMBLYDEBUG linker option
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
ms.openlocfilehash: e9b39791e6537976be37b942292e1b1d42d5f700
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478648"
---
# <a name="assemblydebug-add-debuggableattribute"></a>/ASSEMBLYDEBUG (Ajouter DebuggableAttribute)

```
/ASSEMBLYDEBUG[:DISABLE]
```

/ASSEMBLYDEBUG émet le **DebuggableAttribute** attribut avec débogage informations suivi et désactive les optimisations JIT. Cela équivaut à spécifier l’attribut suivant dans la source :

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

: Disable émet le **DebuggableAttribute** attribut mais désactive le suivi des informations de débogage et Active les optimisations JIT. Cela équivaut à spécifier l’attribut suivant dans la source :

```
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE
```

La valeur par défaut est de ne pas émettre le **DebuggableAttribute** attribut.

DebuggableAttribute peut également être ajouté à un assembly directement dans le code source. Par exemple :

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

## <a name="remarks"></a>Notes

Il est nécessaire de spécifier explicitement qu’une image managée est débogable. À l’aide de [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) seul ne suffit pas.

Autres options de l’éditeur de liens qui affectent la génération de l’assembly sont :

- [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **déboguer** page de propriétés.

1. Modifier le **Assembly pouvant être débogué** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)