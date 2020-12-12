---
description: En savoir plus sur les éléments suivants:/MANIFESTDEPENDENCY (spécifier les dépendances de manifeste)
title: /MANIFESTDEPENDENCY (Spécifier les dépendances de manifeste)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
ms.openlocfilehash: 129dc84818b0bda9b2106c0d07dca5b605dc6f96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199165"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Spécifier les dépendances de manifeste)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>Notes

/MANIFESTDEPENDENCY vous permet de spécifier des attributs qui seront placés dans la \<dependency> section du fichier manifeste.

Pour plus d’informations sur la création d’un fichier manifeste [, consultez/MANIFEST (créer un manifeste d’assembly côte à côte)](manifest-create-side-by-side-assembly-manifest.md) .

Pour plus d’informations sur la \<dependency> section du fichier manifeste, consultez [fichiers de configuration](/windows/win32/SbsCs/publisher-configuration-files)de l’éditeur.

Les informations/MANIFESTDEPENDENCY peuvent être passées à l’éditeur de liens de l’une des deux manières suivantes :

- Directement sur la ligne de commande (ou dans un fichier réponse) avec/MANIFESTDEPENDENCY.

- Via le pragma [Comment](../../preprocessor/comment-c-cpp.md) .

L’exemple suivant montre un commentaire/MANIFESTDEPENDENCY passé par le biais du pragma.

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

ce qui entraîne l’entrée suivante dans le fichier manifeste :

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

Les mêmes commentaires/MANIFESTDEPENDENCY peuvent être passés au niveau de la ligne de commande comme suit :

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

L’éditeur de liens collecte les commentaires/MANIFESTDEPENDENCY, élimine les entrées en double, puis ajoute la chaîne XML obtenue au fichier manifeste.  Si l’éditeur de liens détecte des entrées en conflit, le fichier manifeste est endommagé et l’application ne parvient pas à démarrer (une entrée peut être ajoutée au journal des événements, indiquant la source de l’échec).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés  >    >  **fichier manifeste** de l’éditeur de liens propriétés de configuration.

1. Modifiez la propriété **dépendances de manifeste supplémentaires** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
